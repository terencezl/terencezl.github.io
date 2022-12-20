---
layout: post
title: Training Deep Learning Models
---

I recently come across an [article](https://karpathy.github.io/2019/04/25/recipe/) by Andrej Karpathy, ex-Sr. Director of AI at Tesla. Besides being impressed by the content, it almost brought me to tears, because so much of it was what I personally experienced, learned the hard way, came to believe in, and decided to teach others. It felt vindicating to hear him say

> ...a “fast and furious” approach to training neural networks does not work and only leads to suffering... the qualities that in my experience correlate most strongly to success in deep learning are patience and attention to detail.

because I kept saying this but this point and its implications weren't going through people's minds.

Here I offer some of my own rules of training deep learing models.

1. There were typically open source code and data to begin with. Replicate their results closely, then multiple times with slightly different configs to explore the param space.
2. Perfect the training code with each iteration, making logging, charting, resuming extremely easy.
3. For lack of better tooling for tracking experiments in dynamic ways, create a worklog, form a mental map of the things done, and be sensitive to the file sizes, timestamps, git diff outputs in the commandline to enrich your own working memory. The ability to hold a lot of trial and error outcomes provide changes for breakthroughs. It's like your brain CPU's fast-access memory.
4. Bring new/more data in. Do a lot of experiments at a small scale with big param changes, from data sampling strategy, preprocessing, learning rate schedule, number of epochs to hone in to a good baseline. Figure out which params are more sensitive to specific datasets, and which are less likely to drift.
5. Scale up 10x, and change the params that are more sensitive. Observe if experimental results agree with your hypotheses. Also observe if at this scale the trends and rules observed at the smaller scale still hold. Make new hypotheses about scaling to the next level.
6. In the meantime spend days drilling into relevant parts of the deep learning framework being used. Block out time to go deep as they are the most intimate tooling, and mastering them at a deep level will pay dividends before a big endeavor goes to its finishing line.
7. Gradually scale up to the largest size of data and model architecture one has & can afford. Apply the scaling rules and all the evidence, working intuition and pick the outcome models that evaluate best on a large and representative test set.
8. If test set starts to get saturated, it’s time to take a break and create a more effective test set.
