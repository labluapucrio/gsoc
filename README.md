# LabLua - Programming Language Research

![](http://www.lua.inf.puc-rio.br/images/site_header.png)

Project Ideas List - Google Summer of Code 2026
-----------------------------------------------

In this page we introduce some of the projects that are are working with us this year under the LabLua umbrella and list some potential ideas for GSoC 2026 projects.

If you are a contributor candidate, feel free to get in touch with us via our [Matrix](https://matrix.to/#/#lablua:matrix.org), [mailing list](mailto:labluagsoc@googlegroups.com) or by sending an email to one of our mentors. You can apply using one of the ideas in the list or you can bring your own idea. Either way, don't leave it to the last minute =).

Please use our [application template](/apply.md) to prepare your proposal and take a look at our [successful projects](http://www.lua.inf.puc-rio.br/gsoc/blog2025.html) from last year.

| :exclamation:  Important note on AI usage |
|:---------------------------|
| GSoC is about learning and growing your personal skills. Using AI to code for you will not help you reach that goal. If you are eager to learn, then don't use AI to write your code. AI is improving quickly and provides great opportunities for research and learning, but you should write your own code. <br/><br/
>We further ask you not to use an AI to create a "smart" looking application for
any of the proposed projects.  Instead do your homework, look at the
prerequisites and starting points we provided you with.  Get familiar with the
code base and only then write your application, in your words, using your
skills.
>As mentors we're here to mentor you, not your bot.
|

* * *

### General Lua Projects

*   [Evaluating Structured Reactive Patterns in Atmos](#evaluating-structured-reactive-patterns-in-atmos)
*   [Add Video Support to pico-sdl and pico-lua](#add-video-support-to-pico-sdl-and-pico-lua)
*   [Prepared Statements for LuaSQL](#add-support-for-prepared-statements-for-luasql)

### Lua Integration

Lua integration means to integrate Lua into an existing program written in
C/C++ to make it scriptable and/or to provide the functionality of software
written in C/C++, typically libraries, to Lua programs.

*   [Bring the libcurl Lua Binding Up to Date and Make it More Lua Friendly](#bring-the-libcurl-lua-binding-up-to-date-and-make-it-More-lua-friendly)
*   [Extend the Server Side Only Lua Websocket Module with a Websocket Client](#extend-the-server-side-only-lua-websocket-module-with-a-websocket-client)
*   [Update the LuaPGSQL Module to PostgreSQL 18](#update-the-luapgsql-module-to-postgresql-18)
*   [A Comprehensive Lua Module for Linux](#a-comprehensive-lua-module-for-linux)
*   [Integrate Lua into OpenRTX, the Free and Open Source Firmware for Digital Ham Radios](#integrate-lua-into-openrtx-the-free-and-open-source-firmware-for-digital-ham-radios)

### Lunatik

Lunatik is a project that brings Lua to the Linux kernel to make it possible
to script the Linux kernel in Lua.

*   [Conntrack and NAT support for Lunatik](#conntrack-and-nat-support-for-lunatik)
*   [Port The Lua Test Suite to Lunatik](#port-the-lua-test-suite-to-lunatik)
*   [Lunatik Binding for Linux Traffic Control (TC) and eBPF Maps](#lunatik-binding-for-linux-traffic-control-tc-and-ebpf-maps)
*   [Lunatik Binding for Netlink](#lunatik-binding-for-netlink)
*   [Lunatik Binding for OpenWrt UBUS](#lunatik-binding-for-openwrt-ubus)
*   [Lunatik Binding for sched-ext](#lunatik-binding-for-sched-ext)

* * *

## Detailed Description of Project Ideas

### Evaluating Structured Reactive Patterns in Atmos

[Atmos](https://github.com/atmos-lang/atmos/) is an experimental
programming language that compiles to Lua 5.4 and reconciles structured
concurrency and event-driven programming.

[pico-lua](https://github.com/fsantanna/pico-sdl/tree/main/lua/) is a a Lua
binding to [pico-sdl](https://github.com/fsantanna/pico-sdl/)), a graphics
library for 2D games and applications based on SDL.

In this project, we will combine Atmos with pico-lua ("pico-atmos") to
develop graphical applications using structured reactive primitives, such as
`await`/`emit`, `par`/`par_or`/`par_and`, and `spawn`/`task`.

A [previous case study](https://fsantanna.github.io/pingus/) rewrote
the game logic of [Pingus](https://pingus.github.io/) using structured reactive
programming.
That study identified **5 control-flow patterns** commonly found in
game development:

1.  **Finite State Machines** --- entities whose behavior maps event
    occurrences to transitions between states (e.g., double-click
    detection, character animations).
2.  **Continuation Passing** --- long-lasting activities that carry an
    action to execute next upon completion (e.g., interactive dialogs,
    menu transitions).
3.  **Dispatching Hierarchies** --- container entities that
    automatically forward stimuli to managed children (e.g., redraw and
    update callbacks).
4.  **Lifespan Hierarchies** --- container entities whose termination
    automatically destroys managed children (e.g., UI containers,
    particle systems).
5.  **Signaling Mechanisms** --- entities that communicate explicitly
    when no hierarchy relationship exists between them (e.g., key
    shortcuts, screen pausing).

This project proposes to **port an existing graphical application to
pico-atmos**, systematically applying and evaluating these patterns.

The contributor will select a game (written in any language) that contemplate
these five patterns above.
Good candidates include well-known open-source games with menus, animations,
entity hierarchies, and inter-entity communication --- for example, games built
with [LÖVE](https://love2d.org/) or other Lua frameworks.

The project has two interleaved tracks:

*   **Implementation** --- Incrementally port the game to pico-atmos,
    replacing callbacks, state variables, and dispatching code with
    Atmos constructs (`await`/`emit`, `par`/`par_or`, `spawn`, `task`,
    pattern matching, etc.).
*   **Evaluation** --- For each rewritten module, classify the applied
    patterns, compare lines of code, and document qualitative observations
    (readability, expressiveness, limitations encountered).

#### Expected results

*   A port of the chosen application running on pico-atmos.
*   A document evaluating the control-flow patterns and the whole process.
*   Source code published in a public repository with clear commit
    history showing the incremental porting process.

#### Prerequisites

*   Programming experience in Lua and at least one other language
    (C, C++, or Python).
*   Familiarity with 2D game development concepts (game loop, sprites,
    collision detection, state machines).
*   Willingness to learn Atmos (the
    [manual](https://github.com/atmos-lang/atmos/blob/main/doc/manual-out.md)
    and existing games
    [Birds](https://github.com/atmos-lang/pico-birds/) and
    [Rocks](https://github.com/atmos-lang/pico-rocks/) serve as
    learning material).
*   Reading the Pingus case study:
    [web version](https://fsantanna.github.io/pingus/) and
    [SBGames 2018 paper](http://www.ceu-lang.org/chico/ceu_sbgames18_pre.pdf).

#### Skill level

*   Hard

#### Project size

*   Medium (175 hours) or Large (350 hours), depending on the
    complexity of the chosen game.

#### Mentors

*   [Francisco Sant'Anna](mailto:francisco.santanna@gmail.com)

### Add Video Support to pico-sdl and pico-lua

[pico-sdl][pico-sdl] is a simple educational 2D graphics library for C.

[pico-lua][pico-lua] is the Lua binding for `pico-sdl`, enabling rapid
prototyping and scripting of interactive applications.

[pico-sdl]: https://github.com/fsantanna/pico-sdl/
[pico-lua]: https://github.com/fsantanna/pico-sdl/tree/main/lua/

This project aims to extend `pico-sdl` and `pico-lua` to support synchronized
audio/video playback.
The project should support, at least, raw formats, such as YUV video and PCM
audio.

More specifically, this project proposes a `pico.video` and `pico.audio`
sub-modules to manipulate media files and play them following SDL2's streaming
texture and audio queue APIs.

Audio/video synchronization should follow time-based frame scheduling, in which
the expected frame number is calculated from a delta elapsed time to properly
construct a timeline.

#### Expected results

*   C implementation of audio/video sub-modules for `pico-sdl`
*   Lua bindings for the audio/video module for `pico-lua`
*   Synchronized A/V playback demo application
*   Documentation and API reference
*   Optional: FFmpeg integration for MP4/compressed formats

#### Prerequisites

*   Lua and C programming languages
*   Experience with the Lua C API
*   SDL multimedia API (nice to have)
*   Experience with video formats and codecs (nice to have)

#### Skill level

*   Intermediate

#### Project size

*   Small (90 hours) or Medium (175 hours)

#### Mentors

*   [Francisco Sant'Anna](mailto:francisco.santanna@gmail.com)

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
*   Experience with Lua C API (highly desirable)
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


### Bring the libcurl Lua Binding Up to Date and Make it More Lua Friendly

['libcurl'](https://curl.se/libcurl/) is the de-facto standard network transfer
library to handle all kind of network requests.

A Lua binding for libcurl exists ['LuaCURL'](https://github.com/arcapos/luacurl)
but it has not seen much development activity recently.

The goal of this project is to bring the libcurl Lua binding up to the current
state of libcurl and provide all (or at least most) of libcurls functionality
to Lua.  At the same time LuaCURL should be made more Lua friendly (instead of
just providing libcurls functions to Lua.) E.g. LuaCURL currently uses integer
constants taken from libcurl for LuaCURL options, but Lua has the paradigm
of using strings for options.  So this should be reworked to use strings.

### Some explorations to get started

*   The ['libcurl'](https://curl.se/libcurl/) website
*   ['The Lua Integration Guide'](https://lua.msys.ch) by Marc Balmer

#### Expected results

*   A LuaCURL module that is in par with libcurl
*   Make LuaCURL more "Lua-ish", e.g. no more integer constants
*   Ensure that LuaCURL remains agnostic of the libcurl version it is compiled
    against (i.e. check the libcurl version at runtime to only provide to Lua
    what is available in the underlying libcurl)
*   Test and document everything

#### Prerequisites

*   Be proficient in the C programming language
*   Experience with the Lua C API
*   Experience with cURL and networking in general
*   Experience with Lua

#### Skill level

*  Medium to advanced

#### Project size

*  Medium (175 hours) or Large (350 hours)

#### Mentors

*  [Marc Balmer](mailto:mhbalmer@gmail.com)
*  [Thijs Schreijer](thijs@thijsschreijer.nl)

#### Matrix room

* [#lua-integration](https://matrix.to/#/#lua-integration:matrix.org)

***

### Extend the Server Side Only Lua Websocket Module with a Websocket Client

Websockets are a common way for clients, e.g. a webbrowser, to communicate
with server applications over a persistent connection, the Websocket.

With ['luawebsocket'](https://github.com/arcapos/luawebsocket) a server side
only implementation of Websockets exists for Lua, i.e. it allows to write
Websocket Servers in Lua.

The goal of this project is to add client functionality to the luawebsocket
module so that Lua programs can be first class Websocket clients.

### Some explorations to get started

*   [The Websocket Standard](https://websockets.spec.whatwg.org)
*   ['The Lua Integration Guide'](https://lua.msys.ch) by Marc Balmer

#### Expected results

*   Add a client side Websocket implementation to luawebsocket
*   Test and document everything

#### Prerequisites

*   Be proficient in the C programming language
*   Experience with the Lua C API
*   Experience with Websockets and networking in general
*   Experience with Lua

#### Skill level

*  Medium to advanced

#### Project size

*  Medium (175 hours) or Large (350 hours)

#### Mentors

*  [Marc Balmer](mailto:mhbalmer@gmail.com)
*  [Thijs Schreijer](thijs@thijsschreijer.nl)

#### Matrix room

* [#lua-integration](https://matrix.to/#/#lua-integration:matrix.org)

***

### Update the LuaPGSQL Module to PostgreSQL 18

PostgreSQL is the most advanced open source database system and it is in very
wide use.

With ['luapgsql'](https://github.com/arcapos/luapgsql) a Lua client interface
exists that is based on PostgreSQLs libpq C client library.  It aims at being
feature complete and support all functionality of PostgreSQL itself, that
includes advanced features like asnychronous notifications etc. It has, however,
not been updated since ca. PostgreSQL version 16.

The goal of this project is to bring the Lua PostgreSQL client module up to
date with the current PostgreSQL 18 version while at the same make a critical
review of the module and ensure its readyness to be used in a Lua environment
and to add Lua idioms where needed.  On suche existing "Luaism" is e.g. that
a PostgreSQL result set can be directly converted to a Lua table.

A second goal is to write an extensive set of example programs in Lua to serve
as a base and guide for developers that want to include PostgreSQL in their
Lua programs.

### Some explorations to get started

*   ['libpq - the C client interface'](https://www.postgresql.org/docs/current/libpq.html)
*   ['The Lua Integration Guide'](https://lua.msys.ch) by Marc Balmer

#### Expected results

*   Review and extend where needed the Lua PostgreSQL client module
*   Add a comprehensive set of example programs
*   Test and document everything

#### Prerequisites

*   Be proficient in the C programming language
*   Experience with the Lua C API
*   Experience with PostgreSQL in general and libpq in special
*   Experience with Lua

#### Skill level

*  Medium to advanced

#### Project size

*  Medium (175 hours) or Large (350 hours)

#### Mentors

*  [Marc Balmer](mailto:mhbalmer@gmail.com)
*  [Thijs Schreijer](thijs@thijsschreijer.nl)

#### Matrix room

* [#lua-integration](https://matrix.to/#/#lua-integration:matrix.org)

***

### A Comprehensive Lua Module for Linux

Linux offers a rich programming interface for C programmers and we aim with
this project to make this interface available to Lua.

With ['lualinux'](https://github.com/arcapos/lualinux) a Lua module to use
the Linux programming interface exists, but it is far from complete.  It
already has a modular approach, so that Lua programs don't have to load a
"monster" binding, but just so much as is needed.  Part of the project is
to review this modularization.

The module tries to mimick a bit what is done in C:  You include, e.g. syslog.h
when you want to use the syslog() function in your C program.  Likewise in Lua
you would require 'syslog' to use the syslog functionality.

The goal of this project is to make as much as possible of the Linux programming
interface available to Lua programs and try use Lua paradigms where possible.
For example, while in C header files #defines for constants are used, in Lua
we prefer strings for options.  In the end the module should provide the
Linux programming interface in a Lua friendly style.

A second goal is to write an extensive set of example programs in Lua to serve
as a base and guide for developers that want to use the Linux programming
interface in their Lua programs.

### Some explorations to get started

*   ['The Linux Programming Interface'](https://man7.org/tlpi/) by Michael
    Kerrisk
*   ['The Lua Integration Guide'](https://lua.msys.ch) by Marc Balmer

#### Expected results

*   Complete as much as possible the Linux module for Lua
*   Add a comprehensive set of example programs
*   Test and document everything

#### Prerequisites

*   Be proficient in the C programming language
*   Experience with the Lua C API
*   Experience with the Linux programming interface
*   Experience with Lua

#### Skill level

*  Advanced

#### Project size

*  Medium (175 hours) or Large (350 hours)

#### Mentors

*  [Marc Balmer](mailto:mhbalmer@gmail.com)
*  [Thijs Schreijer](thijs@thijsschreijer.nl)

#### Matrix room

* [#lua-integration](https://matrix.to/#/#lua-integration:matrix.org)

***

### Integrate Lua into OpenRTX, the Free and Open Source Firmware for Digital Ham Radios

Most firmware for digital ham radios is proprietary and uses patented commercial
voice codecs based on the AMBE+2 chips made by HSI.

OpenRTX, on the other hand, provides a completely free, non patent-encumbered
alternative that uses the M17 protocol for voice and data communication.  M17
uses the free and opensource Code 2 voice codec.

Making OpenRTX scriptable pursues several goals:  First it is another showcase
of integrating Lua into an operating system kernel, something that has
previously been done for the Linux and NetBSD kernel, with the difference that
OpenRTX, which uses the Miosix kernel, runs in a restricted embedded
environment. Secondly, having a radio that can be scripted allows for new
applications that have never been done before with a radio.  It opens a door to
unprecedented experimentation.

### Some explorations to get started

*   ['The OpenRTX Project'](https://openrtx.org/#/)
*   ['The M17 Project'](https://m17project.org/)
*   ['The Miosix OS Kernel'](https://miosix.org/)
*   ['The Lua Integration Guide'](https://lua.msys.ch) by Marc Balmer

#### Expected results

*   Make OpenRTX scriptable
*   Add a comprehensive set of example scripts
*   Test and document everything

#### Prerequisites

*   Be proficient in the C programming language
*   Experience with the Lua C API
*   Experience with Lua
*   Experience with embedded system
*   Have an amateur radio license and callsign

#### Skill level

*  Advanced

#### Project size

*  Large (350 hours)

#### Mentors

*  [Marc Balmer](mailto:mhbalmer@gmail.com) HB9SSB
*  [Silvano Seva](mailto:silseva@fastwebnet.it) IU2KWO, OpenRTX project leader


#### Matrix room

* [#lua-integration](https://matrix.to/#/#lua-integration:matrix.org)

***

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
*  [Carlos Carvalho](carloslack@gmail.com)

#### Matrix room

* [#lunatik](https://matrix.to/#/#lunatik:matrix.org)

* * *

### Port The Lua Test Suite to Lunatik

[Lunatik](https://github.com/luainkernel/lunatik/) is a framework for scripting the Linux kernel with Lua. For example, Lunatik can be used for scripting the Linux networking subsystem (as presented at Netdev [0x14](https://netdevconf.info/0x14/session.html?talk-linux-network-scripting-with-lua) and [0x17](https://netdevconf.info/0x17/sessions/talk/scripting-the-linux-routing-table-with-lua.html)) among other [examples](https://github.com/luainkernel/lunatik#examples).

The purpose of this project is to port the [Lua Test Suite](https://www.lua.org/tests/) to Lunatik. That is, to adapt scripts from the Lua Test Suite and develop a Linux loadable kernel module containing its C portion. This project might leverage the [GSoC 2015 project](http://www.lua.inf.puc-rio.br/gsoc/blog2015.html#kerneltest) developed by [Guilherme Salazar](/cdn-cgi/l/email-protection#2a4d59506a4b49470445584d), which ported the Lua Test Suite to the [NetBSD kernel](https://man.netbsd.org/lua.4).

The main difference between the kernel Lua and regular user-level Lua is that kernel Lua doesn't have support for standard libraries that depend on operating system (e.g., io and os) and for floating-point numbers.

#### Expected results

*   Adapted test scripts for Lunatik
*   Lunatik library for testing the Lua C API
*   Test Report at least for x86\_64 and ARM64

#### Prerequisites

*   Lua and C programming languages
*   Experience with the Lua C API (nice to have)
*   Experience with Linux kernel (nice to have)

#### Skill level

*  Beginner

#### Project size

*  Small (90 hours) or Medium (175 hours)

#### Mentors

*  [Guilherme Salazar](mailto:gsz@acm.org)
*  [Lourival Vieira Neto](mailto:lourival.neto@gmail.com)

#### Matrix room

* [#lunatik](https://matrix.to/#/#lunatik:matrix.org)

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

### Lunatik Binding for Netlink

This project aims to implement a Netlink binding for Lunatik, allowing Lua
scripts running in kernel space to interact with Netlink-based kernel
subsystems and user space applications.

The binding should support Generic Netlink, enabling bidirectional
communication with user space, and expose kernel APIs that are only available
via Netlink, such as the cfg80211 subsystem. It should also allow the
extraction of data from Netfilter hooks through Netlink.

As part of the project, luafib should be reimplemented entirely in Lua, using
the new Netlink binding.

#### Expected results

* Netlink communication between kernel-space Lua and user space
* Lua interfaces for Netlink-only kernel subsystems (e.g., cfg80211)
* Support for extracting data from Netfilter via Netlink
* A pure Lua reimplementation of luafib
* Documentation and usage examples

#### Prerequisites

*   Lua and C programming languages
*   Linux Networking
*   Basic understanding of Netlink and Sockets
*   Experience with Linux Kernel (highly desirable)

#### Skill level

*   Intermediate

#### Project size

*  Medium (175 hours) or Large (350 hours)

#### Mentors

*  [Lourival Vieira Neto](mailto:lourival.neto@gmail.com)
*  [Mohammad Shehar Yaar Tausif](mailto:sheharyaar48@gmail.com)

#### Matrix room

* [#lunatik](https://matrix.to/#/#lunatik:matrix.org)

***

### Lunatik Binding for OpenWrt UBUS

This project aims to implement a UBUS binding for Lunatik, allowing Lua scripts
running in kernel space to interact directly with the OpenWrt configuration and
management bus.

UBUS is OpenWrt’s IPC mechanism, widely used for system configuration, status
reporting, and service control. It is built on top of libubus and libubox, and
uses UNIX Domain Sockets for communication between clients and services.

With the recent addition of UNIX Domain Socket support in Lunatik, this project
proposes creating a native Lunatik API for UBUS, enabling both read and write
access to the bus directly from kernel-space Lua scripts. This would allow
Lunatik-based logic to query system state, react to configuration changes, and
interact with OpenWrt services in a structured and consistent way.

#### Expected results

* A Lua API exposing core UBUS functionality
* Support for reading from and writing to the UBUS bus
* Integration based on UNIX Domain Sockets
* Example scripts demonstrating interaction with OpenWrt configuration and services
* Documentation of the API

#### Prerequisites

*   Lua and C programming languages
*   Familiarity with OpenWrt architecture
*   Basic understanding of UBUS, libubus, and libubox

#### Skill level

*   Beginner

#### Project size

*  Medium (175 hours) or Large (350 hours)

#### Mentors

*  [Arif Alam](mailto:arif.alam@netexperience.com)
*  [Marcel Moura](mailto:marcel.stanley@gmail.com)
*  [Lourival Vieira Neto](mailto:lourival.neto@gmail.com)

#### Matrix room

* [#lunatik](https://matrix.to/#/#lunatik:matrix.org)

***

### Lunatik Binding for sched-ext

Recently, sched-ext was added to the Linux kernel, introducing a framework that
allows scheduler extensions implemented using eBPF. This mechanism enables
custom scheduling policies to be developed and dynamically attached to the
kernel scheduler, without modifying core scheduler code.

sched-ext has already been used to implement experimental and unconventional
schedulers, including a example of a scheduler based on astrology,
highlighting both the flexibility of the framework and its suitability for
rapid experimentation.

This project aims to create a Lunatik integration API for sched-ext, following
a design similar to luaxdp, enabling Lua callbacks to be invoked from sched-ext
hooks in order to implement process scheduling policies. The project also
includes exporting the required scheduler-related kernel APIs to Lua, allowing
policies to be expressed clearly and concisely.

The expected outcome is a new binding, luasched, along with example scheduling
policies implemented in Lua, and a comparative evaluation against eBPF
implementations in terms of performance and code clarity.

#### Expected results

*  A new Lunatik binding for sched-ext (luasched)
*  A Lua API exposing sched-ext hooks and required scheduler primitives
*  Support for implementing process scheduling policies using Lua callbacks
*  Example scheduling policies implemented in Lua
*  Benchmark comparisons between Lua-based sched-ext policies and eBPF equivalents
*  Code clarity and maintainability comparisons between Lua and eBPF approaches
*  Documentation and usage examples

#### Prerequisites

*  Lua and C programming languages
*  Linux kernel internals
*  Basic understanding of Linux scheduling
*  Familiarity with eBPF and sched-ext is a plus

#### Skill level

*  Intermediate

#### Project size

*  Small (90 hours) or Medium (175 hours)

#### Mentors

*  [Lourival Vieira Neto](mailto:lourival.neto@gmail.com)
*  [Mohammad Shehar Yaar Tausif](mailto:sheharyaar48@gmail.com)
*  [Enderson Maia](mailto:endersonmaia@gmail.com)

#### Matrix room

*  [#lunatik](https://matrix.to/#/#lunatik:matrix.org)

***
