<!-- Archived from http://www.lua.inf.puc-rio.br/gsoc/ideas2024.html; this is the ideas list as published for GSoC 2024. -->

## Ideas List - Google Summer of Code 2024

We are proud to announce that this year we will again be participating in [Google Summer of Code](https://summerofcode.withgoogle.com/). In this page we introduce some of the projects that are are working with us this year under the LabLua umbrella and list some potential ideas for GSOC 2024 projects.

If you are a contributor candidate, feel free to get in touch with us via our [mailing list](mailto:labluagsoc@googlegroups.com) or by sending an email to one of our mentors. You can apply using one of the ideas in the list or you can bring your own idea. Either way, don't leave it to the last minute :)

Please use our [application template](http://www.lua.inf.puc-rio.br/gsoc/apply2024.html) to prepare your proposal.

-----

  - [Improved debugging support for Pallene](#pallene-debugging)
  - [Documentation generator tool for the Teal language](#teal-doc)
  - [Port LuaRocks to Teal](#luarocks-teal)
  - [A Windows installer for LuaRocks](#luarocks-windows)
  - [Adapt LuaSQL drivers to Lua 5.4](#luasql-drivers)
  - [Port Lua Test Suite to Lunatik](#lunatik-test)
  - [Lunatik binding for Netfilter](#lunatik-nefilter)
  - [Lunatik binding for Human Interface Devices (HID) drivers](#lunatik-hid)
  - [Lunatik package for Linux distros](#lunatik-distro)

-----

<a id="pallene-debugging"></a>

### Improved debugging support for Pallene

[Pallene](https://github.com/pallene-lang/pallene) is a statically-typed programming language, intended to serve as a more performant companion to Lua. It is designed to to seamlessly interoperate with Lua, with first-class support for Lua data types.

Pallene is able to be faster than Lua (sometimes as fast as LuaJIT) by taking advantage of the type annotations in Pallene in order to guide the compiler into outputting efficient executable code. The catch, is that Pallene can receive dynamically-typed data from Lua and it must check if this data matches the expected types, before it can send it into the faster code paths. If Pallene receives a value of an unexpected type, it will immediately raise an exception and emit a stack trace. The objective of this project is to improve the debuggability of these stack traces.

The biggest problem is that currently the error message only shows the line number of the error. The stack trace does not show the Pallene stack frames, only any Lua stack frames that might be present. This is because, from Lua's point of view, Pallene stack calls are implemented as C function calls and the default Lua stack traceback does not show C stack frames. The main objective of this project would be to implement a way to include Pallene stack frames in the stack trace.

One risk of the project is that the code needed to support stack traces might potentially result in slower performance even when the code never encounters an error. Therefore, an additional requirement is that we measure the performance of the new implementation. If it is worse than before, it might be necessary to turn the improved stack traces into an optional feature instead of the default.

#### Expected results

  - A way to produce stack traces including all Pallene function calls
  - Benchmarks to measure the run-time overhead of supporting stack trace.
  - Document how the stack traces are implemented
  - Unit tests for the new feature

#### Prerequisites

  - Lua and C programming languages
  - Experience with the Lua-C API (highly desirable)
  - Experience with Lua debuggers (nice to have)

#### Skill level

Challenging

#### Project size

Large (350 hours)

#### Mentor

[Hugo Musso Gualandi](mailto:hugo.gualandi@gmail.com)  

-----

<a id="teal-doc"></a>

### Documentation generator tool for the Teal language

The goal of this project is to create a "tealdoc" tool that generates documentation from comments embedded in [Teal](https://teal-language.org) source code. Teal is a statically typed language that compiles to Lua (Teal is to Lua somewhat like TypeScript is to JavaScript). Since Teal is essentially a superset of Lua, this tool should be useful for Lua as well. There is prior art for Lua (LuaDoc, LDoc), but the community would benefit from a Teal-specific tool that is able to make use of its type annotations as possibly integrate better with language servers in modern editors.

#### Expected results

  - a CLI tool that generates Markdown from Teal or Lua comments and Teal type annotations
  - support for generating HTML, possibly using templating systems (possibly reusing LDoc code)
  - stretch goal: integration with other existing tooling such as the vscode-teal plugin and LuaRocks
  - stretch goal: extensibility for supporting more languages in the Lua ecosystem

#### Tools

  - [Teal](https://teal-language.org)
  - any Lua libraries needed
  - [LuaRocks](https://luarocks.org)

#### Skill level

Intermediate

#### Project size

Large (350 hours)

#### Mentor

[Hisham Muhammad](mailto:h@hisham.hm)  

-----

<a id="luarocks-teal"></a>

### Port LuaRocks to Teal

[LuaRocks](https://luarocks.org) is the package manager for the Lua language. It is written in pure Lua, making use of several optional libraries. The goal of this project is to port the LuaRocks source code to [Teal](https://teal-language.org), a statically typed language that compiles to Lua (Teal is to Lua somewhat like TypeScript is to JavaScript).

Porting LuaRocks to Teal comprises essentially of writing type annotations to its source code, but will also allow for many opportunities for refactoring and improving its codebase, understanding and reporting on limitations of the Teal language and possibly inform or contribute to its development.

#### Expected results

  - a version of LuaRocks written in Teal

#### Tools

  - [Teal](https://teal-language.org)
  - [LuaRocks](https://luarocks.org)

#### Skill level

Challenging

#### Project size

Large (350 hours)

#### Mentor

[Hisham Muhammad](mailto:h@hisham.hm)  

-----

<a id="luarocks-windows"></a>

### A Windows installer for LuaRocks

[LuaRocks](https://luarocks.org) is the package manager for the Lua language. While the tool itself does have full Windows support, the installation process leaves much to be desired, due to the lack of standard package management systems on Windows. The goal of this project is to produce a native installer for LuaRocks on Windows using some FOSS GUI installer tool of your choice, that allows installing LuaRocks, Lua and configuring it with the user's compiler toolchain.

#### Expected results

  - a GUI installer for LuaRocks
  - integration of the building of the GUI installer to the LuaRocks release scripts (ideally it should be possible to cross-compile the installer generation on Linux, and/or run it from a CI system)
  - stretch goal: bundling the Mingw C compiler toolchain as an optional component of the installer

#### Tools

  - [LuaRocks](https://luarocks.org)
  - a FOSS GUI installer toolkit, such as [WIX](https://wixtoolset.org) or [NSIS](https://nsis.sf.net)
  - Microsoft Windows

#### Skill level

Easy/Intermediate

#### Project size

Large (350 hours)

#### Mentor

[Hisham Muhammad](mailto:h@hisham.hm)  

-----

<a id="luasql-drivers"></a>

### Adapt LuaSQL drivers to Lua 5.4

[LuaSQL](https://lunarmodules.github.io/luasql/) is a simple -- and unique -- interface from Lua to a DBMS: ODBC, ADO, Oracle, MySQL, SQLite, Firebird and PostgreSQL. Its main goal is a common API. The last version was tested against Lua 5.3. Although it should work with Lua 5.4, it was not tested. Also the code may benefit from new features from version 5.4.

Since the goal is to update the "Lua C API part" of the code, there is little knowledge of the DBMS' involved in the project. Also, since the code is very similar between the drivers, it should be easy to extend the effort to all drivers.

#### Expected results

  - revision of the actual code of the chosen drivers and possibly some improvement
  - update docs
  - overall tests and distribution of a new version

#### Tools

  - Lua
  - DBMS C libraries (of the chosen drivers)

#### Prerequisites

  - Lua and C programming languages
  - Experience with the Lua-C API (highly desirable)

#### Skill level

Intermediate

#### Project size

Small (90 hours), Medium (175 hours) or (Large (350 hours) depending on the chosen drivers

#### Mentor

[Tomás Guisasola](mailto:tomasguisasola@gmail.com)  

-----

<a id="lunatik-hid"></a>

### Lunatik binding for Human Interface Devices (HID) drivers

[Lunatik](https://github.com/luainkernel/lunatik/) is a framework for scripting the Linux kernel with Lua. For example, Lunatik can be used for scripting the Linux networking subsystem (as presented at Netdev [0x14](https://netdevconf.info/0x14/session.html?talk-linux-network-scripting-with-lua) and [0x17](https://netdevconf.info/0x17/sessions/talk/scripting-the-linux-routing-table-with-lua.html)) among other [examples](https://github.com/luainkernel/lunatik#examples).

The purpose of this project is to create a Lunatik library for binding the [Linux HID APIs](https://docs.kernel.org/hid/index.html) to allow developers to write new HID drivers using Lua. This project might leverage the [Lunatik device library](https://github.com/luainkernel/lunatik#device), which allows the creation of character device drivers using Lua. Moreover, this project should also port the [Nvidia Shield HID driver](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/drivers/hid/hid-nvidia-shield.c) to Lua.

#### Expected results

  - Lunatik HID library
  - Nvidia Shield HID driver in Lua
  - Benchmark comparison between Nvidia Shield HID driver and its Lua implementation

#### Prerequisites

  - Lua and C programming languages
  - Experience with the Lua-C API (highly desirable)
  - Experience with Linux kernel (highly desirable)

#### Skill level

Challenging

#### Project size

Large (350 hours)

#### Mentors

[Lourival Vieira Neto](mailto:lourival.neto@gmail.com)  

-----

<a id="lunatik-test"></a>

### Port Lua Test Suite to Lunatik

[Lunatik](https://github.com/luainkernel/lunatik/) is a framework for scripting the Linux kernel with Lua. For example, Lunatik can be used for scripting the Linux networking subsystem (as presented at Netdev [0x14](https://netdevconf.info/0x14/session.html?talk-linux-network-scripting-with-lua) and [0x17](https://netdevconf.info/0x17/sessions/talk/scripting-the-linux-routing-table-with-lua.html)) among other [examples](https://github.com/luainkernel/lunatik#examples).

The purpose of this project is to port the [Lua Test Suite](https://www.lua.org/tests/) to Lunatik. That is, to adapt scripts from the Lua Test Suite and develop a Linux loadable kernel module containing its C portion. This project might leverage the [GSoC 2015 project](http://www.lua.inf.puc-rio.br/gsoc/blog2015.html#kerneltest) developed by [Guilherme Salazar](mailto:gsz@acm.org), which ported the Lua Test Suite to the [NetBSD kernel](https://man.netbsd.org/lua.4).

The main difference between the kernel Lua and regular user-level Lua is that kernel Lua doesn't have support for standard libraries that depend on operating system (e.g., io and os) and for floating-point numbers.

#### Expected results

  - Adapted test scripts for Lunatik
  - Lunatik library for testing the Lua C API
  - Test Report at least for x86\_64 and ARM64

#### Prerequisites

  - Lua and C programming languages
  - Experience with the Lua-C API (nice to have)
  - Experience with Linux kernel (nice to have)

#### Skill level

Intermediate

#### Project size

Medium (175 hours)

#### Mentors

[Guilherme Salazar](mailto:gsz@acm.org) and [Lourival Vieira Neto](mailto:lourival.neto@gmail.com)  

-----

<a id="lunatik-nefilter"></a>

### Lunatik binding for Netfilter

[Lunatik](https://github.com/luainkernel/lunatik/) is a framework for scripting the Linux kernel with Lua. For example, Lunatik can be used for scripting the Linux networking subsystem (as presented at Netdev [0x14](https://netdevconf.info/0x14/session.html?talk-linux-network-scripting-with-lua) and [0x17](https://netdevconf.info/0x17/sessions/talk/scripting-the-linux-routing-table-with-lua.html)) among other [examples](https://github.com/luainkernel/lunatik#examples).

Netfilter is a packet filtering framework provided by the Linux kernel. It implements a set of hooks at well-defined points in the packet traversal of the network stack, allowing registered callback functions to receive and act upon every packet that reaches their associated hooks. The callback functions are defined by loadable kernel modules that dynamically extend Netfilter in order to set up custom filtering strategies.

[NFLua](https://github.com/luainkernel/nflua) is an extension module to Netfilter which provides a kernel-scripting framework for packet filtering using an older version of the Lunatik's Lua interpreter. The purpose of this project is to create a new Lunatik library for binding Netfilter to allow the creation of Netfilter extension modules in Lua (instead of using Lua for scripting a single Netfilter module like NFLua). This project should provide Lua APIs for hooking Netfilter (similarly to [Lunatik device library](https://github.com/luainkernel/lunatik#device), which allows the creation of character device drivers using Lua).

#### Expected results

  - Lunatik Netfilter library
  - Iptables Lua library
  - Benchmark comparison between NFLua and the Lunatik Netfilter library

#### Prerequisites

  - Lua and C programming languages
  - Linux Networking
  - Experience with the Lua-C API (highly desirable)
  - Experience with Linux kernel (highly desirable)

#### Skill level

Challenging

#### Project size

Large (350 hours)

#### Mentors

[Marcel Moura](mailto:marcel.stanley@gmail.com) and [Lourival Vieira Neto](mailto:lourival.neto@gmail.com)  

-----

<a id="lunatik-distro"></a>

### Lunatik package for Linux distros

[Lunatik](https://github.com/luainkernel/lunatik/) is a framework for scripting the Linux kernel with Lua. For example, Lunatik can be used for scripting the Linux networking subsystem (as presented at Netdev [0x14](https://netdevconf.info/0x14/session.html?talk-linux-network-scripting-with-lua) and [0x17](https://netdevconf.info/0x17/sessions/talk/scripting-the-linux-routing-table-with-lua.html)) among other [examples](https://github.com/luainkernel/lunatik#examples).

The purpose of this project is to create Lunatik packages for some Linux distributions including, at least, Ubuntu, OpenWRT and VyOS. This project should also provide the documentation and templates for creating packages for new Lunatik libraries.

#### Expected results

  - Lunatik packages for Linux distros (at least, Ubuntu, OpenWRT, VyOS)
  - Submit packages to upstream repositories
  - Documentation and templates

#### Prerequisites

  - Lua and C programming languages
  - Experience with build tools and package managers (highly desirable)
  - Experience with the Lua-C API (nice to have)
  - Experience with Linux kernel (nice to have)

#### Skill level

Intermediate

#### Project size

Small (90 hours)

#### Mentors

[Marcel Moura](mailto:marcel.stanley@gmail.com) and [Lourival Vieira Neto](mailto:lourival.neto@gmail.com)  

-----
