## C++ comparing threads and fibers

| **Aspect** | **Threads** | **Fibers** |
|:------------------|:---------------------------------|:---------------------------------|
| Multitasking | preemptive | cooperative |
| Scheduling and Context switch | managed by the OS kernel | controlled / managed by the application in the user space |
| Context switch overhead | High; can be an issue when the number of threads exceed the # of CPU cores | Very low; since it happens entirely in the user-space | 
| Parallelism | can run in parallel on multiple CPUs | Do not offer parallel execution |
| Stack management | OS | Application |
| Synchronization | Essential for ensuring the data integrity | Less of an issue; due to explicit yielding |
| Scalability | Limited by the OS and memory overhead | Highly scalable |
| Best for | CPU-bound, parallel workloads | I/O bound, highly concurrent workloads |
| Blocking operations | only blocks the current thread | blocks all fibers in the thread |
| C++ standard support | since C++11 | Not part of the official C++ standard (C++23) | 

#### Reference
- [Fiber in C++: Understanding the Basics](https://agraphicsguynotes.com/posts/fiber_in_cpp_understanding_the_basics/)
- sourced from [Perplexity](https://www.perplexity.ai)
