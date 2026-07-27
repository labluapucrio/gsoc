<!-- Archived from http://www.lua.inf.puc-rio.br/gsoc/ideas2018.html; this is the ideas list as published for GSoC 2018. -->

## Ideas List - Google Summer of Code 2018

  - [Interrupt-based drivers in Céu-Arduino for Cortex-M0 microcontrollers](#ceu)
  - [A Parser Generator with Semi-Automatic Error Recovery based on LPeg(Label)](#lpeg)
  - [Titan Fiber-Based Coroutines](#titan)
  - [Develop I/O API for Lunatik](#lunio)
  - [Develop Socket API for Lunatik](#lunsoc)
  - [Update the Lua Binding to libgit2](#libgit)

  

-----

<a id="ceu"></a>

### Interrupt-based drivers in Céu-Arduino for Cortex-M0 microcontrollers

#### Background

Currently, most operations in Arduino libraries freeze the rest of the application until they complete, e.g.:

  - Reading an analog pin with [analogRead](https://www.arduino.cc/en/Reference/AnalogRead) takes about 100 microseconds to complete.
  - Measuring a distance with an [ultrasonic sensor](http://playground.arduino.cc/Code/NewPing) takes about 30 milliseconds.

The use of interrupts allows programs to remain executing while the operation progresses and completes. However, programming with interrupts is hard and error prone.

Céu-Arduino supports the development of Arduino applications in the programming language Céu:

  - Source Code: <https://github.com/fsantanna/ceu-arduino/>
  - Documentation: <http://fsantanna.github.io/ceu-arduino/>
  - Chat: <https://gitter.im/fsantanna/ceu>

Céu is a reactive language that aims to offer a higher-level and safer alternative to C:

  - Home Page: <http://www.ceu-lang.org/>
  - Source code: <https://github.com/fsantanna/ceu/>

Céu-Arduino empowers the development of Arduino applications with the following extensions:

  - Awaiting events in direct/sequential style.
  - Parallel lines of execution with
      - safe abortion;
      - deterministic behavior (in contrast with threads).
  - Asynchronous loops for heavy computations.
  - Interrupt-driven operation mode.
  - Seamless integration with standard Arduino (e.g., `digitalWrite`, `random`, etc).

Céu supports [interrupts](https://github.com/fsantanna/ceu-arduino#switching-a-led-with-interrupts) as a primitive construct, reducing programming efforts considerably.

Céu-Arduino already provides some interrupt-based drivers for AVR microcontrollers, such as for [external pins, timers, ADC, SPI, and the USART](https://github.com/fsantanna/ceu-arduino/tree/master/include/arduino/isr).

#### The Project

The project consists of developing new interrupt-based drivers for Cortex-M0 microcontrollers, e.g.:

  - ADC
  - SPI and I2C buses
  - EEPROM
  - Real-time clock
  - Some libraries built on top of these drivers (e.g., RF transceiver, ultrasonic sensor, accelerometer).

#### Tools

  - [Céu](https://github.com/fsantanna/ceu/) is the programming language used in Céu-Arduino.
  - [Céu-Arduino](https://github.com/fsantanna/ceu-arduino/) is the Céu binding for Arduino.
  - [Mini Ultra Pro](http://www.rocketscream.com/blog/docs-item/mini-ultra-pro-hookup-guide/) is a Cortex-M0-based Arduino development board.
  - A sort of Arduino peripherals.

#### Prerequisites

**We expect the student to own an Arduino board and peripherals.**

We also expect the student to know **C** and **interrupt services routines** in Arduino microcontrollers.

We ask applicants to complete the following activities *before* the application period:

1.  Install Céu and Céu-Arduino and compile and test some existing examples.
2.  Create a simple example in Céu-Arduino using some sensors and actuators (not necessarily using interrupts).
3.  Create a simple example in C that uses interrupt-driven analog reads.
4.  Fork our [Céu-Arduino](https://github.com/fsantanna/ceu-arduino/) project on *github* and commit the new examples.

#### Skill level

Hard

#### Mentor

[Francisco Sant'Anna](http://www.ceu-lang.org/chico)

  

-----

<a id="lpeg"></a>

### A Parser Generator with Semi-Automatic Error Recovery based on LPeg(Label)

#### Brief explanation

[Parsing Expression Grammars](http://bford.info/pub/lang/peg) (PEGs) are an expressive formalism for the design and implementation of top-down parsers with local backtracking. [LPeg](http://www.inf.puc-rio.br/~roberto/lpeg/) is a tool that provides an implementation of PEGs for Lua, while [LPegLabel](https://github.com/sqmedeiros/lpeglabel/) is an extension of LPeg with some facilities for error reporting and recovery.

The goal of this project is to build a parser generator on top of the new version of LPegLabel. This new tool should make easier the description of a parser for a programming language and should also implement an algorithm to automatically annotate a PEG with labels, in order to provide a quasi-automatic error recovery mechanism.

#### Tools

  - [LPegLabel](https://github.com/sqmedeiros/lpeglabel/)
  - [LPeg](http://www.inf.puc-rio.br/~roberto/lpeg/)
  - [parser-gen](https://github.com/vsbenas/parser-gen/)

#### Expected results

  - A parser generator tool
  - The (re)writing of at least 2 parsers with the new tool, including [*lua-parser*](https://github.com/andremm/lua-parser), with a robust error recovering mechanism.
  - A proper documentation

#### Prerequisites

We expect the applicants to have a solid knowledge of *parsing* and to develop familiarity with LPeg and LPegLabel before the project starts. The applicant should have used at least one parser generator tool, such as yacc/bison, ANTLR, JavaCC, PEG.js, etc.

For this reason, we will ask the applicants to perform some activities **before** the application period.

#### Skill level

Advanced

#### Mentor

[Sérgio Medeiros](https://sites.google.com/site/sqmedeiros/)

  

-----

<a id="titan"></a>

### Titan Fiber-Based Coroutines

#### Brief Explanation

[Titan](http://titan-lang.org) is a new programming language, designed to be a statically-typed, ahead-of-time compiled sister language to Lua. Titan is in active development and, by the time of GSoC 2018, will already have had its first public release. The main goal of Titan is **predictable performance**, getting close to or surpassing what is possible with LuaJIT while being easy for Lua programmers. Several important use cases of Lua and LuaJIT, such as <span>OpenResty</span>, rely on Lua coroutines for exposing a blocking, synchronous API to Lua scripts while working on top of an asynchronous, non-blocking native API. The goal of this GSoC project is to add coroutine support to Titan, using the **fiber** APIs of the major operating systems, so similar APIs can be built in Titan. This should be done without changes to the Lua virtual machine and runtime system, although custom versions of the Lua standard library functions that create and manage coroutines should be necessary.

#### Expected Results

  - Being able to yield from Lua code that has been called from Titan
  - Expose a coroutine API similar to the one that Lua scripts use for Titan coide

#### Knowledge Prerequisites

C, Lua, OS APIs for cooperative multithreading (fibers)

#### Skill Level

Advanced

#### Mentor

[Fabio Mascarenhas](https://www.dcc.ufrj.br/~fabiom/index.en.html)  

-----

<a id="lunio"></a>

### Develop I/O API for Lunatik

#### Brief explanation

[Lunatik](http://netbsd.org/~lneto/dls14.pdf) is a kernel-level Lua interpreter version for scripting the Linux kernel. For example, it allows users to [filter packets using Lua scripts](http://netbsd.org/~lneto/eurobsdcon14.pdf).

The main difference between Lunatik and regular user-level Lua is that Lunatik has no support for standard libraries that depend on the operating system (e.g., io and os) and for floating-point numbers. The purpose of this project is to develop a Lunatik library to provide I/O functionality to kernel scripts. This API should provide access to the file system internals and be implemented as a Linux loadable kernel module, binding the kernel internal implementation for the file user-level API.

#### Expected results

  - Lunatik I/O Library
  - Documentation and Benchmarks

#### Knowledge prerequisites

C, Lua, OS (and some courage :) )

#### Skill level

Advanced

#### Mentor

[Lourival Vieira Neto](mailto:lneto@NetBSD.org)

  

-----

<a id="lunsoc"></a>

### Develop Socket API for Lunatik

#### Brief explanation

[Lunatik](http://netbsd.org/~lneto/dls14.pdf) is a kernel-level Lua interpreter version for scripting the Linux kernel. For example, it allows users to [filter packets using Lua scripts](http://netbsd.org/~lneto/eurobsdcon14.pdf).

The main difference between Lunatik and regular user-level Lua is that Lunatik has no support for standard libraries that depend on the operating system (e.g., io and os) and for floating-point numbers. The purpose of this project is to develop a Lunatik library to provide network functionality to kernel scripts. This API should provide access to the network internals and be implemented as a Linux loadable kernel module, binding the kernel internal implementation for the socket user-level API.

#### Expected results

  - Lunatik Socket Library
  - Documentation and Benchmarks

#### Knowledge prerequisites

C, Lua, OS (and some courage :) )

#### Skill level

Advanced

#### Mentors

[Lourival Vieira Neto](mailto:lneto@NetBSD.org)  
[Pedro Tammela](mailto:pctammela@gmail.com)

  

-----

<a id="libgit"></a>

### Update the Lua Binding to libgit2

#### Brief explanation

[libgit2](https://libgit2.github.com/) is a portable, pure C89 implementation of the Git core methods provided as a linkable library with a solid API with zero dependencies. It is currently used in a variety of git-based applications such as GitHub, GitLab and BitBucket. libgit2 has bindings with multiple programming languages such Ruby, Python, Erlang, Go, Lua and many others.

The project consists in updating (or rewriting) the Lua binding to libgit2 ([luagit2](https://github.com/libgit2/luagit2))

#### Expected results

  - Working luagit2 library compatible with the most recent versions of libgit2 and Lua
  - A luagit2 module uploaded to [LuaRocks](http://luarocks.org/)
  - Proper documentation
  - Bi-weekly blog posts about the development process

#### Prerequisites

  - Good knowledge of C
  - Lua

#### Skill level

Medium

#### Mentors

[Etiene Dalcol](http://etiene.net/main/about)  
[Edward Thomson](mailto:ethomson@edwardthomson.com)
