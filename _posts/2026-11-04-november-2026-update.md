---
title: "My Tech Journal - November 2026"
date: 2026-11-04
tags: [journal, monthly-update, Rust]
description: "Monthly collection of interesting tech talks, articles, and software from November 2026."
---

## My Tech Journal - November 2026 Edition
---

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
  
