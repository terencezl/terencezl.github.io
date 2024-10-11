---
layout: post
title: Comparing Value and Reference Semantics across Languages
---

Started learning [Mojo](https://docs.modular.com/mojo/manual/), and watched this [deep dive on ownership](https://www.youtube.com/watch?v=9ag0fPMmYPQ) when it came out:

<div style="max-width: 95%; width: 560px; height: 315px; margin: 0 auto;">
<iframe width="100%" height="100%" src="https://www.youtube.com/embed/9ag0fPMmYPQ?si=q1rL7p2p5e7t2Mkd" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

Just summarizing the value and reference semantics across three langauges: C++, Rust, and Mojo:

C++:

```
copy: `func(string s)`, caller `func(s)`
move: `func(string&& s)`, caller `func(std::move(s))`
immutable reference: `func(const string& s)`, caller `func(s)`
mutable reference: `func(string& s)`, caller `func(s)`
```

Rust:
```
copy: `func(s: String)`, caller `func(s.clone())`
move: `func(s: String)`, caller `func(s)`
immutable reference: `func(s: &String)`, caller `func(&s)`
mutable reference: `func(s: &mut String)`, caller `func(&mut s)`
```

Mojo:
```
copy: `func(owned s: String)`, caller `func(s)`
move: `func(owned s: String)`, caller `func(s^)`
immutable reference: `func(borrowed s: String)`, caller `func(s)`
mutable reference: `func(inout s: String)`, caller `func(s)`
```
