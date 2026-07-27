<!-- Archived from http://www.lua.inf.puc-rio.br/gsoc/ideas2021.html; this is the ideas list as published for GSoC 2021. -->

## Ideas List - Google Summer of Code 2021

We are proud to announce that this year we will again be participating in [Google Summer of Code](https://summerofcode.withgoogle.com/). In this page we introduce some of the projects that are are working with us this year under the LabLua umbrella and list some potential ideas for GSOC 2021 projects.

If you are a student, feel free to get in touch with us via our [mailing list](mailto:labluagsoc@googlegroups.com) or by sending an email to one of our mentors. You can apply using one of the ideas in the list or you can bring your own idea. Either way, don't leave it to the last minute :)

Please use our [application template](http://www.lua.inf.puc-rio.br/gsoc/apply2021.html) to prepare your proposal.

-----

  - [Lua scripted watchpoints in LLDB](#lldb)
  - [Closures for Pallene](#pallene-closures)
  - [Typed API for LuaRocks](#typed-api-for-luarocks)
  - [A Lua library for Freechains-P2P](#freechains)

<a id="lldb"></a>

### Lua scripted watchpoints in LLDB

[LLDB](https://lldb.llvm.org/) is a modern debugger developed by the LLVM project. LLDB can be scripted with Python and more recently [with Lua](https://www.youtube.com/watch?v=UgfzdAr9AFg&list=PL_R5A0lGi1ABzH_FIZSx0sHQkOqI7p4Cg&index=58).

Scripted watchpoints allow users to attach a script or Lua function to a watchpoint and execute it when the program flow hits it. In this project, you will add support for Lua in scripted watchpoints. You will also improve the general Lua scripting documentation.

#### Expected results

  - Lua scripted watchpoints
  - Documentation for Lua scripting in LLDB
  - Unit tests

#### Tools

  - LLDB
  - Lua-C API
  - LLVM API

#### Prerequisites

  - Intermediate C++
  - Lua-C API

#### Skill level

Intermediate

#### Mentors

[Jonas Devlieghere](mailto:jonas@devlieghere.com) and [Pedro Tammela](mailto:pctammela@gmail.com)

-----

<a id="pallene-closures"></a>

### Closures for Pallene

[Pallene](https://github.com/pallene-lang/pallene) is a statically-typed companion language for Lua. It's main goal is improving Lua's performance by allowing programmers to use type annotations to write performant extension modules.

The Pallene language implements a subset of Lua's features. One feature that is currently missing are nested functions and closures. Implementing them would empower programmers to use a more functional programming style and would make it easier to use Lua APIs that expect to receive a Pallene function as a callback.

#### Expected results

  - Implement the required changes to the type checker and compiler
  - Document how nested functions work in Pallene
  - Unit tests for the new feature

#### Prerequisites

  - Lua and C programming languages
  - Some experience with compilers
  - Lua-C API

#### Skill level

Challenging

#### Mentor

[Hugo Gualandi](mailto:hgualandi@inf.puc-rio.br)  

-----

<a id="typed-api-for-luarocks"></a>

### Typed API for LuaRocks

[LuaRocks](https://luarocks.org) is the package manager for Lua. It is written as a Lua application, composed of several modules required by the main "luarocks" CLI program.

These modules were not originally designed for reuse outside of LuaRocks, but some provide useful generic functionality, such as filesystem and platform abstractions. Further, they do not provide a programmatic interface for other applications which wish to drive LuaRocks using Lua scripting.

The goal of this project is to provide typed API for LuaRocks modules, specified using [Teal](https://github.com/teal-language), a typed dialect of Lua, which allows for typed definition files to be written for untyped Lua modules. Our goal here is not to port all of LuaRocks to Teal, but to provide typed interfaces for Teal or Lua applications, so that users of these interfaces can have a stable contract of the API's inputs and outputs.

We will exercise this new API via a proof-of-concept implementation integrating LuaRocks to some other Lua application via the API, yet to be chosen by the student and mentor. This will allow opportunity for interacting with other open source projects as well.

#### Expected results

  - Refactoring of reusable LuaRocks components
  - Design of a public LuaRocks API
  - Teal declaration files presenting this API
  - A proof-of-concept implementation using this API to drive LuaRocks

#### Tools

  - Lua
  - [Teal](https://github.com/teal-language)

#### Prerequisites

  - Lua

#### Skill level

Intermediate

#### Mentor

[Hisham Muhammad](mailto:hisham@luarocks.org)

-----

<a id="freechains"></a>

### A Lua library for Freechains-P2P

[Freechains](https://github.com/Freechains/README) is an unstructured peer-to-peer topic-based publish-subscribe system. Each topic, or chain, is disseminated peer by peer in the network with gossiping. This way, as an author posts to a chain, other users subscribed to the same chain eventually receive the message. Freechains supports multiple types of chains for public and private communication.

The goal of this project is to create a Lua library to interface with Freechains. The Lua interface should mimic the standard [command-line interface of Freechains](https://github.com/Freechains/README/blob/master/docs/cmds.md).

#### Tools

  - Freechains
  - Lua
  - Luasocket

#### Prerequisites

The student should be familiar with Lua and LuaSockets. We ask applicants to complete the following activities before the application period:

  - Install Lua, LuaSockets, and Freechains.
  - Watch the videos about Freechains in the first link above.
  - Create a simple example with Freechains and LuaSockets:
    1.  Start a Freechains daemon with the command `freechains-host`.
    2.  Join a sample chain with the command `freechains chains join`.
    3.  Write a LuaSockets script that connects with the daemon and writes `FC v0.7.10 chains list` to it.
    4.  Confirm if the result matches the joined chain.

#### Skill level

Easy

#### Mentor

[Francisco Sant'Anna](mailto:francisco.santanna@gmail.com)  

-----
