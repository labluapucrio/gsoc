# LabLua - Programming Language Research

![](http://www.lua.inf.puc-rio.br/images/site_header.png)

Ideas List - Google Summer of Code 2025
---------------------------------------

In this page we introduce some of the projects that are are working with us this year under the LabLua umbrella and list some potential ideas for GSOC 2025 projects.

If you are a contributor candidate, feel free to get in touch with us via our [mailing list](mailto:labluagsoc@googlegroups.com) or by sending an email to one of our mentors. You can apply using one of the ideas in the list or you can bring your own idea. Either way, don't leave it to the last minute :)

Please use our [application template](http://www.lua.inf.puc-rio.br/gsoc/apply2024.html) to prepare your proposal.

* * *

*   [Documentation generator tool for the Teal language](#teal-doc)
*   [A Windows installer for LuaRocks](#luarocks-windows)
*   [Port Lua Test Suite to Lunatik](#lunatik-test)
*   [Lunatik binding for Human Interface Devices (HID) drivers](#lunatik-hid)
*   [Lunatik package for Linux distros](#lunatik-distro)
*   [Terminal UI library for Lua](#terminal-ui-library-for-lua)
*   [Conntrack and NAT support for Lunatik](#conntrack-and-nat-support-for-lunatik)

* * *

### Documentation generator tool for the Teal language

The goal of this project is to create a "tealdoc" tool that generates documentation from comments embedded in [Teal](https://teal-language.org) source code. Teal is a statically typed language that compiles to Lua (Teal is to Lua somewhat like TypeScript is to JavaScript). Since Teal is essentially a superset of Lua, this tool should be useful for Lua as well. There is prior art for Lua (LuaDoc, LDoc), but the community would benefit from a Teal-specific tool that is able to make use of its type annotations as possibly integrate better with language servers in modern editors.

#### Expected results

*   a CLI tool that generates Markdown from Teal or Lua comments and Teal type annotations
*   support for generating HTML, possibly using templating systems (possibly reusing LDoc code)
*   stretch goal: integration with other existing tooling such as the vscode-teal plugin and LuaRocks
*   stretch goal: extensibility for supporting more languages in the Lua ecosystem

#### Tools

*   [Teal](https://teal-language.org)
*   any Lua libraries needed
*   [LuaRocks](https://luarocks.org)

#### Skill level

*  Intermediate

#### Project size

*  Large (350 hours)

#### Mentor

*  [Hisham Muhammad](mailto:h@hisham.hm)  

* * *

### A Windows installer for LuaRocks

[LuaRocks](https://luarocks.org) is the package manager for the Lua language. While the tool itself does have full Windows support, the installation process leaves much to be desired, due to the lack of standard package management systems on Windows. The goal of this project is to produce a native installer for LuaRocks on Windows using some FOSS GUI installer tool of your choice, that allows installing LuaRocks, Lua and configuring it with the user's compiler toolchain.

#### Expected results

*   a GUI installer for LuaRocks
*   integration of the building of the GUI installer to the LuaRocks release scripts (ideally it should be possible to cross-compile the installer generation on Linux, and/or run it from a CI system)
*   stretch goal: bundling the Mingw C compiler toolchain as an optional component of the installer

#### Tools

*   [LuaRocks](https://luarocks.org)
*   a FOSS GUI installer toolkit, such as [WIX](https://wixtoolset.org) or [NSIS](https://nsis.sf.net)
*   Microsoft Windows

#### Skill level

*  Easy/Intermediate

#### Project size

*  Large (350 hours)

#### Mentor

*  [Hisham Muhammad](mailto:h@hisham.hm)  

* * *

### Lunatik binding for Human Interface Devices (HID) drivers

[Lunatik](https://github.com/luainkernel/lunatik/) is a framework for scripting the Linux kernel with Lua. For example, Lunatik can be used for scripting the Linux networking subsystem (as presented at Netdev [0x14](https://netdevconf.info/0x14/session.html?talk-linux-network-scripting-with-lua) and [0x17](https://netdevconf.info/0x17/sessions/talk/scripting-the-linux-routing-table-with-lua.html)) among other [examples](https://github.com/luainkernel/lunatik#examples).

The purpose of this project is to create a Lunatik library for binding the [Linux HID APIs](https://docs.kernel.org/hid/index.html) to allow developers to write new HID drivers using Lua. This project might leverage the [Lunatik device library](https://github.com/luainkernel/lunatik#device), which allows the creation of character device drivers using Lua. Moreover, this project should also port the [Nvidia Shield HID driver](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/drivers/hid/hid-nvidia-shield.c) to Lua.

#### Expected results

*   Lunatik HID library
*   Nvidia Shield HID driver in Lua
*   Benchmark comparison between Nvidia Shield HID driver and its Lua implementation

#### Prerequisites

*   Lua and C programming languages
*   Experience with the Lua-C API (highly desirable)
*   Experience with Linux kernel (highly desirable)

#### Skill level

*  Challenging

#### Project size

*  Large (350 hours)

#### Mentors

*  [Lourival Vieira Neto](mailto:lourival.neto@gmail.com)  

* * *

### Port Lua Test Suite to Lunatik

[Lunatik](https://github.com/luainkernel/lunatik/) is a framework for scripting the Linux kernel with Lua. For example, Lunatik can be used for scripting the Linux networking subsystem (as presented at Netdev [0x14](https://netdevconf.info/0x14/session.html?talk-linux-network-scripting-with-lua) and [0x17](https://netdevconf.info/0x17/sessions/talk/scripting-the-linux-routing-table-with-lua.html)) among other [examples](https://github.com/luainkernel/lunatik#examples).

The purpose of this project is to port the [Lua Test Suite](https://www.lua.org/tests/) to Lunatik. That is, to adapt scripts from the Lua Test Suite and develop a Linux loadable kernel module containing its C portion. This project might leverage the [GSoC 2015 project](http://www.lua.inf.puc-rio.br/gsoc/blog2015.html#kerneltest) developed by [Guilherme Salazar](/cdn-cgi/l/email-protection#2a4d59506a4b49470445584d), which ported the Lua Test Suite to the [NetBSD kernel](https://man.netbsd.org/lua.4).

The main difference between the kernel Lua and regular user-level Lua is that kernel Lua doesn't have support for standard libraries that depend on operating system (e.g., io and os) and for floating-point numbers.

#### Expected results

*   Adapted test scripts for Lunatik
*   Lunatik library for testing the Lua C API
*   Test Report at least for x86\_64 and ARM64

#### Prerequisites

*   Lua and C programming languages
*   Experience with the Lua-C API (nice to have)
*   Experience with Linux kernel (nice to have)

#### Skill level

*  Intermediate

#### Project size

*  Medium (175 hours)

#### Mentors

*  [Guilherme Salazar](mailto:gsz@acm.org)
*  [Lourival Vieira Neto](mailto:lourival.neto@gmail.com)  

* * *

### Lunatik package for Linux distros

[Lunatik](https://github.com/luainkernel/lunatik/) is a framework for scripting the Linux kernel with Lua. For example, Lunatik can be used for scripting the Linux networking subsystem (as presented at Netdev [0x14](https://netdevconf.info/0x14/session.html?talk-linux-network-scripting-with-lua) and [0x17](https://netdevconf.info/0x17/sessions/talk/scripting-the-linux-routing-table-with-lua.html)) among other [examples](https://github.com/luainkernel/lunatik#examples).

The purpose of this project is to create Lunatik packages for some Linux distributions including, at least, Ubuntu, OpenWRT and VyOS. This project should also provide the documentation and templates for creating packages for new Lunatik libraries.

#### Expected results

*   Lunatik packages for Linux distros (at least, Ubuntu, OpenWRT, VyOS)
*   Submit packages to upstream repositories
*   Documentation and templates

#### Prerequisites

*   Lua and C programming languages
*   Experience with build tools and package managers (highly desirable)
*   Experience with the Lua-C API (nice to have)
*   Experience with Linux kernel (nice to have)

#### Skill level

*  Intermediate

#### Project size

*  Small (90 hours)

#### Mentors

*  [Marcel Moura](mailto:marcel.stanley@gmail.com)
*  [Lourival Vieira Neto](mailto:lourival.neto@gmail.com)  

* * *

### Terminal UI library for Lua

Lua has several core libraries that work across platforms; luasocket (networking), luafilesystem (file system), and luasystem (time, random, terminal). The latter library, luasystem, provides the primitives to handle terminal operations, albeit they are fundamentally different on Posix and Windows based systems.

The purpose of this project is to create a new library that builds on luasystems terminal primitives to build basic UI elements for user interaction in a cross-platform way. This should not be anything like curses, but the simple user interactions like;

- headers and footers
- progress indicators/bars
- prompts; yes/no, ok/cancel
- reading line inputs; reading a filename or other strings
- hidden inputs; for secrets
- etc.

#### Expected results

*   a new library build on top of LuaSystem
*   Windows and Posix
*   API design with consistency across platforms
*   Documentation and examples

#### Prerequisites

*   Lua programming language
*   Experience with terminals (nice to have)

#### Skill level

*  Beginner

#### Project size

*  Small (90 hours)

#### Mentors

*  [Thijs Schreijer](mailto:thijs@thijsschreijer.nl)

* * *

### Conntrack and NAT support for Lunatik

Connection tracking (conntrack) is a fundamental component of the Linux kernel's networking stack. It is part of the Netfilter framework and is responsible for monitoring active network connections passing through the system. Conntrack maintains a state table, allowing the kernel to track packets as part of a flow and apply connection-oriented filtering, NAT (Network Address Translation), and stateful firewalling.

NAT is used to modify IP addresses and ports in packet headers to facilitate address translation, load balancing, and security enforcement. The Linux kernel provides APIs to manipulate NAT and connection tracking through the Netfilter framework.

The purpose of this project is to port conntrack and NAT data structures and kernel APIs to lunatik. These are present under:
*   `net/netfilter/conntrack.h`
*   `net/netfilter/nf_conntrack_common.h`
*   `net/netfilter/conntrack_tuple.h`
*   `net/netfilter/nf_conntrack_core.h`
*   `net/netfilter/nf_nat.h`

This projects builds upon the GSoC 2024 Project ['Lunatik binding for Netfilter'](https://summerofcode.withgoogle.com/archive/2024/projects/BIJAPZjf). For complete reference on the relevant kernel headers and data structures, refer to the following [gist](https://gist.github.com/sheharyaar/cbbd43037fa43fd391e52964347a2bc9).

#### Expected results

*   Allow fetching the conntrack entries and connection information
*   Ability to conntrack add entries from lua programs that need to perform NAT. Example use case - L7 load balancing using netfilter in lua
*   Ability to perform NAT for atleast inet protocols

#### Prerequisites

*   Lua and C programming languages
*   Linux Networking
*   Experience with Linux Kernel (highly desirable)
*   Experience with Netfilter subsystem (good to have)

#### Skill level

*  Challenging

#### Project size

*  Medium (175 hours) or Large (350 hours)

#### Mentors

*  [Lourival Vieira Neto](mailto:lourival.neto@gmail.com) and [Mohammad Shehar Yaar Tausif](mailto:sheharyaar48@gmail.com)

* * *
