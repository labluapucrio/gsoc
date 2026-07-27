## Project

Create a library to help "memory leak" detection in Lua [1].

### Brief explanation

Memory leak in garbage collected languages happens when the program allocates a
memory, then finish using it but does not free3 the memory block. In this case,
all pointers to this block and the block itself are valid, however the data
will never be accessed again by the program.

Lua is a dynamic typed language with garbage collection that as other
garbage-collected languages has many reported issues related to memory leak.
Your task would be to create a library to help memory leak detection in Lua.

### Expected results

* A library that helps memory leak detection in Lua.

There is no restriction if the library should:
* use a combination of heap-differencing and fine-grained allocation tracking
* detect when objects exceed their expected lifetimes
* detect when an object becomes stale
* track growing data structures to check whether they are leaking or not.

### Knowledge prerequisites

A memory leak detection tool will need to monitor and understand objects
behavior and maybe interact with the garbage collector.
Since Lua is implemented in ANSI C and this tool will need access to
the language internals, C is mandatory.

Understanding garbage collection techniques can be very helpful, mainly
the incremental mark-and-sweep collector technique, which Lua implements.

Programming in Lua is not mandatory, however, understanding the language
structure will be very important. For example, Lua has different types of
objects, but only one data structuring mechanism.

### Skill level

Hard

### Mentor

Roberto Ierusalimschy [2]

### Links

[1] Lua:   <http://lua.org/>

[2] Roberto: <http://www.inf.puc-rio.br/~roberto>
