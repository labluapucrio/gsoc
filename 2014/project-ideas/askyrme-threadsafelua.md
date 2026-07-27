## Project

Thread-safe Lua

### Brief explanation

The Lua programming language includes cooperative
multithreading support through coroutines. However, this form of
multithreading is not designed to exploit parallelism. The Lua C API
allows programmers to create independent Lua states, which store
interepreter-related data, that can be used to execute code as if it was
executed from within a coroutine. This has been used by libraries, such as
luaproc and Lua Lanes, to implement concurrency models based on system
threads that can exploit parallelism. The Lua C API also allows
programmers to create new (userland) threads within the same Lua state.
These threads share data with the parent state and thus can potentially
lead to race conditions if executed in parallel. The purpose of this
project is to implement a fork of the standard Lua interpreter that is
internally thread-safe, i.e., that allows multiple (userland) threads
within the same Lua state to execute in parallel without internal
interpreter data races.

### Expected results

A fork implementation of the latest version of the
interpreter of the Lua programming language that is internally
thread-safe.

### Knowledge prerequisites

C, Lua, pthreads

### Skill level

Hard

### Mentor

Noemi Rodriguez

