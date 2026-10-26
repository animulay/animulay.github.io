---
title: "My Tech Journal - October 2026"
date: 2026-10-09
tags: [journal,monthly-update,net,rust]
description: "Monthly collection of interesting tech talks, articles, and software from October 2026."
---

## My Tech Journal - October 2026 Edition
---

### Net
- [Netdev 0x13 - QUIC Tutorial](https://www.youtube.com/watch?v=CtsBawwGwns) May 20, 2019<br>
  QUIC guru [Jana Iyengar](https://github.com/janaiyengar) gave a tutorial at netdev 0x13<br>
  - QUIC is an application level transport protocol on top of UDP for improved end-to-end application performance.<br>
  - QUIC was created at Google with 2 main design goals:<br>
    1. Deployability and evolvability
    2. Low-latency secure communication establishment
  - In QUIC, once you establish connection between 2 endpoints, you can open multiple independent streams within the connection. This avoids the [head-of-line blocking](https://en.wikipedia.org/wiki/Head-of-line_blocking) problem observed with TCP.<br>
  - A QUIC stream is equivalent to a TCP connection.<br>
  - QUIC headers and payload are encrypted.<br>
  - [quicly](https://github.com/h2o/quicly) - [Fastly](https://www.fastly.com/)'s reference implementation of QUIC
  - Since QUIC packets are encrypted, we cannot use [Wireshark](https://www.wireshark.org/). But there are open source tools for QUIC tracing:<br>
    1. [quic-trace](https://github.com/google/quic-trace)
    2. [QUICvis](https://github.com/rmarx/QUICvis) - Note: This has been deprecated in favor of [qvis](https://github.com/quiclog/qvis).
  - [QUIC](https://quicwg.org/) is being standardized. Refer to: [RFC 9000](https://www.rfc-editor.org/rfc/rfc9000.html) QUIC: A UDP-Based Multiplexed and Secure Transport

### Rust
- [cuda-oxide: Rust on the GPU.](https://www.youtube.com/watch?v=3X_x0MfN90Q) What’s Behind #[kernel]?<br>
  - cuda-oxide is a custom rustc backend for compiling kernels for Nvidia GPUs in pure [Rust](https://rust-lang.org/).<br>
  - [Nihal Pasham](github.com/nihalpasham) is the creator of cuda-oxide.<br>
  - In this presentation, Nihal gives us an overview of the code repo and explains the working of #[kernel] annotation with the [vecadd](https://github.com/NVIDIA/cuda-rust/blob/main/cuda-oxide/crates/rustc-codegen-cuda/examples/vecadd/src/main.rs) example.<br>
  - To implement GPU kernel in Rust, the code that runs on the GPU (i.e. the device side of the code) is annotated with #[kernel] and the rustc codegen backend transforms that code into CUDA PTX.<br>
  - Reference: [The cuda-oxide Book](https://nvidia.github.io/cuda-rust/cuda-oxide/)


### Interesting Projects, Code Repositories
- [doxxnet](https://github.com/doxx/doxx.net) an Agentic Defined Network (ADN)
- [BeautifulRust](https://github.com/morganlinton/BeautifulRust) Agent Skills that teach coding agents to write, review, and port idiomatic Rust
