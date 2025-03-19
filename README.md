# LabLua - Programming Language Research

![](http://www.lua.inf.puc-rio.br/images/site_header.png)

Ideas List - Google Summer of Code 2025
---------------------------------------

In this page we introduce some of the projects that are are working with us this year under the LabLua umbrella and list some potential ideas for GSoC 2025 projects.

If you are a contributor candidate, feel free to get in touch with us via our [Matrix](https://matrix.to/#/#lablua:matrix.org), [mailing list](mailto:labluagsoc@googlegroups.com) or by sending an email to one of our mentors. You can apply using one of the ideas in the list or you can bring your own idea. Either way, don't leave it to the last minute =).

Please use our [application template](/apply.md) to prepare your proposal and take a look at our [successful projects](http://www.lua.inf.puc-rio.br/gsoc/blog2024.html) from last year.

| :exclamation:  Important note on AI usage |
|:---------------------------|
| GSoC is about learning and growing your personal skills. Using AI to code for you will not help you reach that goal. If you are eager to learn, then don't use AI to write your code. AI is improving quickly and provides great opportunities and research and learning, but you should write your own code. <br/><br/>As mentors we're here to mentor you, not your bot. |

* * *

*   [Documentation generator tool for the Teal language](#documentation-generator-tool-for-the-teal-language)
*   [Port Lua Test Suite to Lunatik](#port-lua-test-suite-to-lunatik)
*   [Lunatik binding for Human Interface Devices (HID) drivers](#lunatik-binding-for-human-interface-devices-hid-drivers)
*   [Lunatik package for Linux distros](#lunatik-package-for-linux-distros)
*   [Terminal UI library for Lua](#terminal-ui-library-for-lua)
*   [Conntrack and NAT support for Lunatik](#conntrack-and-nat-support-for-lunatik)
*   [Prepared Statements for LuaSQL](#add-support-for-prepared-statements-for-luasql)
*   [Lunatik Binding for Linux Traffic Control (TC) and eBPF Maps](#lunatik-binding-for-linux-traffic-control-tc-and-ebpf-maps)

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

### Lunatik binding for Human Interface Devices (HID) drivers

[Lunatik](https://github.com/luainkernel/lunatik/) is a framework for scripting the Linux kernel with Lua. For example, Lunatik can be used for scripting the Linux networking subsystem (as presented at Netdev [0x14](https://netdevconf.info/0x14/session.html?talk-linux-network-scripting-with-lua) and [0x17](https://netdevconf.info/0x17/sessions/talk/scripting-the-linux-routing-table-with-lua.html)) among other [examples](https://github.com/luainkernel/lunatik#examples).

The purpose of this project is to create a Lunatik library for binding the [Linux HID APIs](https://docs.kernel.org/hid/index.html) to allow developers to write new HID drivers using Lua. This project might leverage the [Lunatik device library](https://github.com/luainkernel/lunatik#device), which allows the creation of character device drivers using Lua. Moreover, this project should also port at least one HID driver to Lua.

#### Expected results

*   Lunatik HID library
*   HID driver examples in Lua
*   Benchmark comparison between the original HID drivers and their Lua implementation

#### Prerequisites

*   Lua and C programming languages
*   Experience with the Lua-C API (highly desirable)
*   Experience with Linux kernel (highly desirable)

#### Skill level

*  Intermediate

#### Project size

*  Medium (175 hours) or Large (350 hours)

#### Mentors

*  [Lourival Vieira Neto](mailto:lourival.neto@gmail.com)

#### Matrix room

* [#lunatik](https://matrix.to/#/#lunatik:matrix.org)

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

#### Matrix room

* [#lunatik](https://matrix.to/#/#lunatik:matrix.org)

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

#### Matrix room

* [#lunatik](https://matrix.to/#/#lunatik:matrix.org)

* * *

### Terminal UI library for Lua

Lua has several core libraries that work across platforms; luasocket (networking), luafilesystem (file system), and [luasystem](https://github.com/lunarmodules/luasystem) (time, random, terminal). The latter library, [luasystem](https://github.com/lunarmodules/luasystem), provides the primitives to handle terminal operations, albeit they are fundamentally different on Posix and Windows based systems.

The purpose of this project is to shape the new [`terminal.lua` library](https://github.com/lunarmodules/terminal.lua) that builds on [luasystems terminal primitives](https://lunarmodules.github.io/luasystem/topics/03-terminal.md.html) to build basic UI elements for user interaction in a cross-platform way. This should not be anything like curses, but the simpler user interactions like;

- progress indicators/bars
- prompts; yes/no, ok/cancel
- reading line inputs; reading a filename or other strings
- hidden inputs; for secrets
- headers and footers (basics for full-screen apps)
- More complex full screen app support (panels, drawing/re-drawing)
- etc.

### Things to consider

The library should be general purpose, adhering the the Lua principle of 'mechanisms over policies'. This means for example that it should be possible to use it sync as well as async (coroutines), and it shouldn't force control over the main application loop, etc. A developer using the library should be able to make his/her own choice.

Besides that terminals are challenging to work with. There are many control codes to control the terminal, however querying the terminal is very limited. There is no way to request current color status or cursor visibility for example.

### Some explorations to get started:

- what are terminals to begin with? a great explanation [part 1](https://blog.nelhage.com/2009/12/a-brief-introduction-to-termios/), and [part 2](https://blog.nelhage.com/2009/12/a-brief-introduction-to-termios-termios3-and-stty/)
- read up on terminals and streams; `stdin`, `stdout`, and `stder`; especially the latter two, when to use what?
- what does LuaSystem offer for platform compatibility, see [LuaSystem terminal docs](https://lunarmodules.github.io/luasystem/topics/03-terminal.md.html)
- check the [existing code base](https://github.com/lunarmodules/terminal.lua)


#### Expected results

*   API that makes it easy to work around terminal limitations
*   API design with consistency across platforms
*   updated `terminal.lua` build on top of LuaSystem, ready for a first release
*   works on Windows and Posix
*   including tests, documentation and examples

#### Prerequisites

*   Lua programming language
*   Experience with terminals (nice to have)

#### Skill level

*  Beginner

#### Project size

*  Medium (175 hours)

#### Mentors

*  [Thijs Schreijer](mailto:thijs@thijsschreijer.nl)

#### Matrix room

* [#lunarmodules](https://matrix.to/#/#lunarmodules:matrix.org)

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

*  [Lourival Vieira Neto](mailto:lourival.neto@gmail.com)
*  [Mohammad Shehar Yaar Tausif](mailto:sheharyaar48@gmail.com)

#### Matrix room

* [#lunatik](https://matrix.to/#/#lunatik:matrix.org)

* * *

### Add support for prepared statements for LuaSQL

['LuaSQL'](https://github.com/lunarmodules/luasql) is a generic interface from Lua to a DBMS. It aims at portability over performance, but it allows extensions to suit the particularities of each DBMS.

The inclusion of support for prepared statements in LuaSQL has been discussed thoroughly some time ago, but since each DBMS offers very different APIs there is no standard that could be defined to assure portability between them. Anyway the demand persists.

This project proposes the addition of a minimal API that would allow each driver to offer prepared statements according to its DBMS restrictions and mechanisms.

#### Expected results

*   Propose a new API that would be flexibly enough to cover the main features of each database respecting each different mechanisms of defining prepared statements
*   Implement the new API into one or more drivers
*   Test and document everything

#### Prerequisites

*   C programming languages
*   Experience with any database C API (highly desirable)
*   Experience with Lua-C API (highly desirable)
*   Experience with Lua (good to have)

#### Skill level

*  Challenging

#### Project size

*  Large (350 hours)

#### Mentors

*  [Tomás Guisasola](mailto:tomasguisasola@gmail.com)

#### Matrix room

* [#lunarmodules](https://matrix.to/#/#lunarmodules:matrix.org)

* * *

### Lunatik Binding for Linux Traffic Control (TC) and eBPF Maps

This project aims to create **Lunatik bindings for the Linux Traffic Control (TC) subsystem and eBPF maps** to enable efficient and programmable network traffic control. These bindings will allow **Lua scripts** to manipulate TC and interact with **eBPF maps**, providing a flexible interface for traffic shaping, filtering, and monitoring.  

This work is **heavily inspired by** the [luaxdp](https://github.com/luainkernel/lunatik?tab=readme-ov-file#xdp) binding, which integrates Lua with **XDP (eXpress Data Path)** using eBPF. Given that **TC and XDP both utilize eBPF**, this new binding (*luatc*) will **reuse and adapt parts of the luaxdp codebase**, ensuring consistency and maintainability.

[Linux Traffic Control (TC)](https://man7.org/linux/man-pages/man8/tc.8.html) is a subsystem of the Linux kernel that allows administrators to **manage network packet transmission**, enabling features like **traffic shaping, queuing, scheduling, and policing**. It is widely used for **bandwidth control, Quality of Service (QoS), and network performance optimization**.

Configuring TC using traditional tools can be **complex and static**, making it difficult to implement **custom traffic processing logic**. **Lunatik**, a Lua-based kernel scripting interface, can simplify this process by allowing users to write **Lua scripts** that dynamically interact with **TC queuing disciplines (qdiscs), classes, and filters**.

Additionally, this project will introduce **support for eBPF maps** within Lunatik. [eBPF maps](https://docs.kernel.org/bpf/maps.html) are a key component of eBPF, providing **efficient storage and retrieval of structured data between user space and kernel space**. This functionality will **not be restricted to the TC binding (*luatc*)**, but will be implemented **as a general feature in Lunatik**, enabling **other kernel extensions** to leverage eBPF maps.

#### Expected results

* A fully functional **Lunatik binding for the TC subsystem**, allowing Lua scripts to configure and manipulate network traffic.
* **Support for eBPF maps in Lunatik**, enabling efficient **data sharing between Lua scripts and eBPF programs**.
* **Integration with the existing luaxdp codebase**, reusing and adapting components where possible.
* **Clear documentation and examples**, demonstrating how to use *luatc* for **network traffic control** and **eBPF maps for data storage**.

#### Prerequisites

*   Lua and C programming languages
*   Linux Networking
*   Experience with Linux Kernel (highly desirable)
*   Experience with Traffic Control (TC) subsystem (good to have)
*   Experience with eBPF maps (good to have)

#### Skill level

*  Challenging

#### Project size

*  Large (350 hours)

#### Mentors

*  [Lourival Vieira Neto](mailto:lourival.neto@gmail.com)
*  [Savio Sena](mailto:savio.sena@gmail.com)

#### Matrix room

* [#lunatik](https://matrix.to/#/#lunatik:matrix.org)

* * *

