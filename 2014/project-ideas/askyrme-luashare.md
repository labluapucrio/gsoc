## Project

luashare - data sharing among parallel execution flows of Lua code

### Brief explanation

luaproc is a concurrent programming library for the Lua
programming language. It allows programmers to create multiple independent
execution flows of Lua code, called Lua processes, that can run in
parallel with underlying multithreading support. Lua processes can only
communicate through message passing. However, messages cannot hold tables,
only basic data types like numbers, strings and booleans. To send tables,
programmers must serialize data on the sender and de-serialize it on the
receiver. Apart from the implementation overhead, there can also be a
performance cost to serialize and de-serialize data. Therefore, it would
be useful to allow table references to be sent in messages, so instead of
copying data, memory would be shared. Assuming the Lua interpreter is
thread-safe, the purpose of this project is to implement a variation of
the luaproc library where instead of having completely independent Lua
processes, data could be shared, in a controlled way, among Lua processes.

### Expected results

new concurrent programming library for the Lua programming language,
based on the principles of the luaproc programming library, that would
allow for controlled data sharing among parallel execution flows of Lua code.

### Knowledge prerequisites

C, Lua, pthreads

### Skill level

Medium

### Mentor

Noemi Rodriguez

