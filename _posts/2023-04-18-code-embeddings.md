---
layout: post
title: Code Embeddings
---

In this post, I would like to explore the idea of using embedding vectors to represent code snippets, and compute the cosine similarity scores between a few examples. I will compare OpenAI's [text-embedding-ada-002](https://platform.openai.com/docs/guides/embeddings) with two open-source models, [SantaCoder](https://huggingface.co/bigcode/santacoder) and Salesforce [CodeGen](https://github.com/salesforce/CodeGen). The OpenAI model was trained on general text data, but it's the only embedding model the company currently offers. The other two models were trained on code to generate code, so we would need to do some hacking to get the embedding vectors.

## Setup

```python
from itertools import combinations
import torch
from transformers import AutoTokenizer, AutoModelForCausalLM
```

How do we get the embedding vectors from a model? We can use the `transformer` part of the model to get the hidden states - layer-by-layer outputs of the transformer blocks. Thanks to a conversation with [Vlad](https://vladlialin.com/), I decided to use the last hidden state. The shape of this output is `(batch_size, seq_len, hidden_size)`, so we would need to aggregate over the `seq_len` dimension to get the "summary". We could take the mean, or max, or some other way. I tried the max, but the similarity scores looked all close to 1. So here let's stick with the mean.

It is noteworthy to spell out the variety of choices here. Echoing my previous [post](https://terencezl.github.io/blog/2023/04/17/the-world-of-embedding-vectors/), the embeddings from a generative model were not trained to definitively tell things apart.

<!--more-->

```python
class EmbeddingModel:
    """
    Wrapper class to get the embedding vector from a model.
    """
    def __init__(self, tokenizer, model):
        self.tokenizer = tokenizer
        self.model = model

    def get_embedding(self, code):
        with torch.no_grad():
            inputs = self.tokenizer(code, return_tensors="pt").to(self.model.device)
            # here we use the transformer part (not the lm head, which is used for generation).
            outputs = self.model.transformer(**inputs)
            # we could use the last_hidden_state, or second last...
            # the shape is (batch_size, seq_len, hidden_size), so we would need to aggregate over the seq_len dimension.
            # we choose to take the mean here.
            return outputs.last_hidden_state.mean(axis=1)[0]


def cosine_similarity(embedding1, embedding2):
    """
    Compute the cosine similarity between two embedding vectors.
    """
    return embedding1.dot(embedding2) / embedding1.norm() / embedding2.norm()
```

Get some snippets of code to compare.

```python
code_snippets = []

code_snippets.append("""def print_hello_world():
    print("hello world")
""")

code_snippets.append("""def do_something():
    a = 1
    b = a + 1
    return b
""")

code_snippets.append("""def hello_world():
    return "hello world"
""")
```

## OpenAI `text-embedding-ada-002`

Here we just initialize and define one function for later use.

```python
# openai

import openai
openai.api_key = "YOUR_API_KEY"

def get_openai_embedding(text, model="text-embedding-ada-002"):
   text = text.replace("\n", " ")
   return torch.tensor(openai.Embedding.create(input = [text], model=model)['data'][0]['embedding'])

```

## SantaCoder

```python
# bigcode/santacoder

device = "cpu"
tokenizer = AutoTokenizer.from_pretrained("bigcode/santacoder")
model = AutoModelForCausalLM.from_pretrained("bigcode/santacoder", trust_remote_code=True).to(device)
santacoder = EmbeddingModel(tokenizer, model)
```

Let's see how the model generates code from a prompt.

```python
code = """def binary_search():
"""
inputs = santacoder.tokenizer(code, return_tensors="pt").to(device)
outputs = santacoder.model.generate(**inputs, max_length=512)
print(santacoder.tokenizer.decode(outputs[0], truncate_before_pattern=[r"\n\n^#", "^'''", "\n\n\n"]))
# don't think `truncate_before_pattern` had any effect here
```

**Output:**

    Setting `pad_token_id` to `eos_token_id`:50256 for open-end generation.


    def binary_search():
        # 1. Get the input
        n = int(input())
        # 2. Initialize the list
        arr = [0] * n
        # 3. Get the elements
        for i in range(n):
            arr[i] = int(input())
        # 4. Find the index
        index = binary_search_recursive(arr, 0, n - 1)
        # 5. Print the result
        print(index)

    def binary_search_recursive(arr, left, right):
        # 1. Base case
        if left > right:
            return -1
        # 2. Get the middle index
        mid = (left + right) // 2
        # 3. Check if the element is present at the middle index
        if arr[mid] == mid:
            return mid
        # 4. Check if the element is smaller than the middle index
        elif arr[mid] < mid:
            return binary_search_recursive(arr, left, mid - 1)
        # 5. Check if the element is greater than the middle index
        else:
            return binary_search_recursive(arr, mid + 1, right)

    if __name__ == '__main__':
        binary_search()<|endoftext|>...

The `truncate_before_pattern` argument didn't seem to take effect here and I saw a lot more code after `<|endoftext|>`. Doesn't affect this experiment, so I'll leave it as is.

What does a SantaCoder embedding vector look like?

```python
embedding = santacoder.get_embedding("def hello_world(): return 'hello world'")
print(embedding.shape)
print(embedding)
```

**Output:**

    torch.Size([2048])
    tensor([-0.2162,  0.7902, -1.0303,  ...,  1.9904, -1.1341, -2.7802],
           device='cpu')

Time to compute the cosine similarity scores using the embedding vectors. We denote `SIM local` as the results from the open-source model, and `SIM openai` as the results from the OpenAI model.

```python
for code1, code2 in combinations(code_snippets, 2):
    sim_local = cosine_similarity(santacoder.get_embedding(code1), santacoder.get_embedding(code2)).item()
    sim_openai = cosine_similarity(get_openai_embedding(code1), get_openai_embedding(code2)).item()
    print(code1)
    print("----------")
    print(code2)
    print(f"SIM local: {sim_local:.2f} SIM openai: {sim_openai:.2f}")
    print("=================================")
```

**Output:**

    def print_hello_world():
        print("hello world")

    ----------
    def do_something():
        a = 1
        b = a + 1
        return b

    SIM local: 0.79 SIM openai: 0.81
    =================================
    def print_hello_world():
        print("hello world")

    ----------
    def hello_world():
        return "hello world"

    SIM local: 0.90 SIM openai: 0.93
    =================================
    def do_something():
        a = 1
        b = a + 1
        return b

    ----------
    def hello_world():
        return "hello world"

    SIM local: 0.84 SIM openai: 0.82
    =================================

You know... They agree quite well. If I don't want to use the OpenAI model, I can just use SantaCoder.

## Salesforce CodeGen

We only use the 2B parameter model for this experiment here.

```python
# salesforce codegen-2B-mono

device = "cpu"
tokenizer = AutoTokenizer.from_pretrained("Salesforce/codegen-2B-mono")
model = AutoModelForCausalLM.from_pretrained("Salesforce/codegen-2B-mono").to(device)
codegen = EmbeddingModel(tokenizer, model)
```

Same here. Let's see how the model generates code from a prompt.

```python
code = """def binary_search():
"""
inputs = codegen.tokenizer(code, return_tensors="pt").to(device)
outputs = codegen.model.generate(**inputs, max_length=512)
print(codegen.tokenizer.decode(outputs[0], truncate_before_pattern=[r"\n\n^#", "^'''", "\n\n\n"]))
```

**Output:**

    Setting `pad_token_id` to `eos_token_id`:50256 for open-end generation.


    def binary_search():
        print("Binary Search")
        arr = list(map(int, input("Enter the array: ").split()))
        key = int(input("Enter the key: "))
        low = 0
        high = len(arr) - 1
        while low <= high:
            mid = (low + high) // 2
            if arr[mid] == key:
                print("Element found at index: ", mid)
                break
            elif arr[mid] < key:
                low = mid + 1
            else:
                high = mid - 1
        else:
            print("Element not found")

Examine the CodeGen embedding vector.

```python
embedding = codegen.get_embedding("def hello_world(): return 'hello world'")
print(embedding.shape)
print(embedding)
```

**Output:**

    torch.Size([2560])
    tensor([ 1.2350,  1.5245,  1.9772,  ...,  3.1278, -2.5663, -1.3473],
           device='cpu')

Compute the cosine similarity scores. Here `SIM local` are from the Salesforce model, and `SIM openai` as the results from the OpenAI model.

```python
for code1, code2 in combinations(code_snippets, 2):
    sim_local = cosine_similarity(codegen.get_embedding(code1), codegen.get_embedding(code2)).item()
    sim_openai = cosine_similarity(get_openai_embedding(code1), get_openai_embedding(code2)).item()
    print(code1)
    print("----------")
    print(code2)
    print(f"SIM local: {sim_local:.2f} SIM openai: {sim_openai:.2f}")
    print("=================================")
```

**Output:**

    def print_hello_world():
        print("hello world")

    ----------
    def do_something():
        a = 1
        b = a + 1
        return b

    SIM local: 0.98 SIM openai: 0.81
    =================================
    def print_hello_world():
        print("hello world")

    ----------
    def hello_world():
        return "hello world"

    SIM local: 0.99 SIM openai: 0.93
    =================================
    def do_something():
        a = 1
        b = a + 1
        return b

    ----------
    def hello_world():
        return "hello world"

    SIM local: 0.98 SIM openai: 0.82
    =================================

Here CodeGen is giving scores all close to 1. It doesn't seem to differentiate between different snippets. I've tried to use the 6B model, but the results were similar. CodeGen should be a decent model for code generation, but apparently, the embedding vector obtained from its last hidden state is not suitable for code similarity.

You can read more about the topic in this [issue](https://github.com/huggingface/transformers/issues/21246) and [Q&A](https://discuss.huggingface.co/t/how-to-get-embedding-matrix-of-bert-in-hugging-face/10261).
