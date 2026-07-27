## Project:

Multi-CPU usage in wireshark

### Brief explanation:

The wireshark network protocol analyser [1] allows programmers to use Lua to write dissectors, post-dissectors and taps. Dissectors are protocol analysers, while post-dissectors are executed after all others dissectors, and taps are used to collect information after packet dissection. Protocol dissection can involve time constraints, and it would be nice to benefit from multi-CPU processing power in dissector script. The purpose of this project is to include support for multi-CPU usage in wireshark, using luaproc, a library that allows programmers to create multiple independent execution flows of Lua code that can run inparallel, communicating only via message-passing.

### Expected results:

We expect the support for Multi-CPU usage in wireshark.

### Knowledge prerequisite:

C, Lua

### Skill level:

Medium

### Mentor:

Noemi Rodriguez

[1] http://www.wireshark.org/
