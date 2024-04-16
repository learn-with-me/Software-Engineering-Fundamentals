# Async Operation

Fact: true asynchrony must be provided at the OS (Operating System) level.

- CPU bound operations are inhenrently synchronous, hence they generally use [Threading](https://learn.microsoft.com/en-us/windows/win32/procthread/processes-and-threads) to support parallel operations. A thread can also _pretend_ to be async by offloading it's taks to another thread.
- I/O bound operations generally use [Asynchronous I/O](https://learn.microsoft.com/en-us/windows/win32/fileio/synchronous-and-asynchronous-i-o)


## State Machine

Refer [State Machine Design in C++](https://www.drdobbs.com/cpp/state-machine-design-in-c/184401236)

## OS level Asynchrony

TBD

## Application level Aysnchrony

Let's take an example of JavaScript's `async/await`, which is a compiler-generated `state machine`, that runs async functions, but relies on OS primitives (`interrupts`, `threads`) to acutally perform a task in async manner.

Often there won't be a new thread created to handle async operations. On Windows, the primary mechanism for performing async work is [I/O Completion Ports](https://learn.microsoft.com/en-us/windows/win32/fileio/i-o-completion-ports) - a Windows API, used under the hood even by the `HttpClient`.

For non-I/O operations, we can always use [Thread](https://learn.microsoft.com/en-us/windows/win32/procthread/creating-threads) and [ThreadPool API](https://learn.microsoft.com/en-us/windows/win32/procthread/thread-pool-api), to perform background work that will complete asynchronously.

## How Async works?

TBD

```
Making a method `async` doesn't meant it will spawn a thread. I/O will not use a thread, unless intentionally created. This is managed at OS level.
General use of async is to help with I/O bound processes, not CPU bound. I/O has callback operated interfaces at the lowest level.

Internally the compiler makes a state machine, which it uses to pause/await/resume executing code.
The method basically turns into a state engine relinquishing control to the task scheduler waiting for a completed task being signalled.
```

> There are no free lunches. To save on waiting on this network round-trip, the producer application has a `operation-stack or something` waiting to listen on the response, whenever it comes back. This means that part resources on the consumers will be occupied till that stack clears up, or for always serving some.

## References

- [There is no thread](https://blog.stephencleary.com/2013/11/there-is-no-thread.html) blog by [Stephen Cleary](https://stephencleary.com/)
  - [Task.Run Etiquette and Proper Usage](https://blog.stephencleary.com/2013/10/taskrun-etiquette-and-proper-usage.html)
  - [Task.Run Etiquette Examples](https://blog.stephencleary.com/2013/11/taskrun-etiquette-examples-even-in.html)
- Regarding `deadlocks` blog by [Stephen Cleary](https://stephencleary.com/)
  - [Parallel Computing - SynchronizationContext](https://learn.microsoft.com/en-us/archive/msdn-magazine/2011/february/msdn-magazine-parallel-computing-it-s-all-about-the-synchronizationcontext)
  - [Async and Await](https://blog.stephencleary.com/2012/02/async-and-await.html)
  - [Don't Block on Async Code](https://blog.stephencleary.com/2012/07/dont-block-on-async-code.html)
  - [Don't Block in Asynchronous Code](https://blog.stephencleary.com/2012/12/dont-block-in-asynchronous-code.html)
- Regarding `Task` blogs by [Stephen Cleary](https://stephencleary.com/)
  - [A Tour of Task, Part 0: Overview](https://blog.stephencleary.com/2014/04/a-tour-of-task-part-0-overview.html) series
  - [Task.Run vs BackgroundWorker: Intro](https://blog.stephencleary.com/2013/05/taskrun-vs-backgroundworker-intro.html) series
  - [Cancellation, Part 1: Overview](https://blog.stephencleary.com/2022/02/cancellation-1-overview.html) series
  - [Asynchronous Messaging, Part 1: Basic Distributed Architecture](https://blog.stephencleary.com/2021/01/asynchronous-messaging-1-basic-distributed-architecture.html) series
  - [BackgroundService Gotcha: Startup](https://blog.stephencleary.com/2020/05/backgroundservice-gotcha-startup.html) series
- Talks by Stephen Cleary [Search](https://learn.microsoft.com/en-us/search/?terms=Stephen_Cleary)
  - [asyncfx](https://learn.microsoft.com/en-us/shows/on-net/stephen-cleary-asyncfx)
  - [Introduction to Async Streams](https://learn.microsoft.com/en-us/events/dotnetconf-net-conf-2019/b325)
  - [Testing async code](https://learn.microsoft.com/en-us/events/seth-on-the-road-that-conference-2015/t012)
- Stephen Toub
  - [An Introduction to System.Threading.Channels](https://devblogs.microsoft.com/dotnet/an-introduction-to-system-threading-channels/)
- [Asynchronous programming with async and await](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/async/)
- [Multithreaded Asynchronous I/O & I/O Completion Ports](https://www.drdobbs.com/cpp/multithreaded-asynchronous-io-io-comple/201202921) blog by [Dr Dobbs](https://www.drdobbs.com/)
- [https://stackoverflow.com/questions/40916697/must-async-methods-be-supported-by-os-or-is-async-program-level-feature](https://stackoverflow.com/questions/40916697/must-async-methods-be-supported-by-os-or-is-async-program-level-feature)
- [.NET Parallel Programming](https://devblogs.microsoft.com/pfxteam/) blogs
- [Stephen Toub](https://devblogs.microsoft.com/dotnet/author/toub/) blogs
