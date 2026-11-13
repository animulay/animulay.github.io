---
title: "My Tech Journal - November 2026"
date: 2026-11-04
tags: [inference, journal, monthly-update, Rust]
description: "Monthly collection of interesting tech talks, articles, and software from November 2026."
---

## My Tech Journal - November 2026 Edition
---

### Inference
- [Stanford CS336](https://cs336.stanford.edu/) Language Modeling from Scratch | Spring 2026 | [Lecture 10: Inference](https://www.youtube.com/watch?v=EfM546A79aM), Prof. Percy Liang<br>
- Training has one-time cost, whereas inference shows up in many places - actual use, model evaluation, reinforcement learning (RL).<br>
- What does fast inference mean? (evaluation metrics)<br>
  1. Time-to-First-Token (TTFT) i.e. how long user waits before any generation happens?<br>
  2. Latency (seconds/token)    how fast tokens appear for one query (interactive)<br>
  3. Throughput (tokens/second) how fast tokens appear for many queries? (batch)<br>
- Two stages of inference:<br><br>
  | 1. Prefill | 2. Generation |
  |:----------:|:-------------:|
  | Given a prompt, encode into vectors. | Generate new response token(s). |
  | This phase is parallelisable like training. | Essentially a sequential operation. |
  | **Compute**-bound | **Memory**-bound |
  <br>
- [Arithmetic intensity analysis](https://youtu.be/EfM546A79aM?t=870)<br>
- Since inference is memory-bound, reducing the KV Cache memory usage leads to speed up.<br>
  Common techniques for improving inference performance:<br>
  1. Quantization<br>
  2. Model pruning (removing unimportant hidden layers without sacrificing the model accuracy)<br>
  3. Speculative Decoding (using a smaller model to generate tokens that are fed to the larger model for evaluation)<br>
- References:<br>
  • [How to Parallelize a Transformer for Training](https://jax-ml.github.io/scaling-book/training/)<br>
  • [All About Transformer Inference](https://jax-ml.github.io/scaling-book/inference/)<br>

### Rust
- [Completion-based IO](https://www.youtube.com/watch?v=CmLAHUuUsAQ) ([Alice Ryhl](https://ryhl.io/) at RustWeek) RustNL<br>
  In this presentation, Alice Ryhl provides an overview of the two different approaches to async IO: readiness-based and completion-based.<br>
  • For many years, the most widely used IO APIs on Linux were based on the **readiness** model. e.g. [select](https://www.man7.org/linux/man-pages/man2/select.2.html), [poll](https://man7.org/linux/man-pages/man2/poll.2.html), [epoll](https://man7.org/linux/man-pages/man7/epoll.7.html)<br>
  • In 2019, [io_uring](https://unixism.net/loti/what_is_io_uring.html) - added **completion** based APIs to Linux.<br>
  • In the readiness-based IO, the waiting happens in the application (user-space), whereas<br> in the completion-based IO, the waiting happens in the kernel-space.<br>
  • [Tokio](https://tokio.rs/) async runtime for Rust is based on the readiness model.<br>
  • [Compio](https://compio.rs/) is an async runtime for Rust built with completion-based IO.<br>
 
 - She also explains different options to implement completion-based async IO in Rust <ins>correctly</ins>.<br>
  • Option 1: Keep using old IO traits with an extra copy<br>
  • Option 2: Not all IO would be completion based; and keep compatibility at a higher layer<br>
  • Option 3: Keep using readiness-based IO for scenarios where it makes sense e.g. TCPStream<br>
  • Option 4: Use the appropriate IO model for every use-case<br>
  
