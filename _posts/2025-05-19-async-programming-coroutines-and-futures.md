
## Understanding the relationship between Coroutines and Futures in C++

A Coroutine
- is a special kind of function that can suspend its execution and resume later
- maintains its state across suspensions

A Future
- is an object representing a value _that may become available at some point_, typically as the result of an asynchronous computation

</br>

| **Feature** | **Coroutine** | **Future** |
|:------------|:---------------------------------|:---------------------------------|
| Purpose     | Suspend / resume computation     | Represents eventual result of the computation |
| Control Flow | Explicit suspension / resumption | Waits for result (blocking or polling) |
| Relationship | Can produce or consume futures | Can be produced by coroutines |
| Keywords / Entities | - co_await: suspends the coroutine and returns control to the caller</br> - co_yield: returns a value to the caller and suspends the current coroutine</br> - co_return: terminates the current function and may return the specified value to the caller. | std library header: <code>&lt;future&gt;</code> <br> - std::future<br> - std::promise  |



#### References
- [Perplexity](https://www.perplexity.ai)
- [cppreference.com](https://en.cppreference.com/w/cpp/20)
