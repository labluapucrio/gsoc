## Project:

Multi-CPU usage in VLC

### Brief explanation:

VLC [1] is a free and open source cross-platform multimedia player and framework that plays most multimedia files as well as DVD, Audio CD, VCD, and various streaming protocols. Lua scripts can be added to VLC for tasks such as playlist construction and service discovery. Such tasks may involve a lot of parsing and communication and could benefit from using multiple CPUs when available. The purpose of this project is to include support for multi-CPU usage in VLC, using luaproc, a library that allows programmers to create multiple independent execution flows of Lua code that can run inparallel, communicating only via message-passing.

### Expected results:

Multi-CPU support in VLC.

### Knowledge prerequisite:

C, Lua

### Skill level:

Medium

### Mentor:

Noemi Rodriguez
