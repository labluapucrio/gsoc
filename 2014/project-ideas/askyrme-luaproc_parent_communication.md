## Project

Send/Receive support for main script in the luaproc library

### Brief explanation

luaproc is a concurrent programming library for the Lua
programming language. It allows programmers to create multiple independent
execution flows of Lua code, called Lua processes, that can run in
parallel with underlying multithreading support. Lua processes can only
communicate through message passing. However, the main Lua script from
where the library is loaded and initial Lua processes are created, cannot
send or receive messages. The purpose of this project is to implement the
required changes in luaproc to allow the main Lua script to communite with
spawned Lua processes through message passing.

### Expected results

An updated version of the luaproc library where it is
possible for the main Lua script to send messages to and to receive
messages from spawned Lua processes.

### Knowledge prerequisites

C, Lua, pthreads

### Skill level

Medium

### Mentor

Noemi Rodriguez

