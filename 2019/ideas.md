<!-- Archived from http://www.lua.inf.puc-rio.br/gsoc/ideas2019.html; this is the ideas list as published for GSoC 2019. -->

## Ideas List - Google Summer of Code 2019

  - [C Header File Parser in Lua Using Clang AST](#pallene)
  - [Low-Power Interrupt-Based Drivers in Céu-Arduino](#ceu)
  - [Apolo: a Library to aid the Creation of Scripts in Lua, replacing Shell Scripts and Windows Batch Files](#apolo)
  - [A Parser Generator with Semi-Automatic Error Recovery based on LPeg(Label)](#lpeg)
  - [Develop an in-kernel DNS over HTTPS server for Lunatik](#lunatik_dns)
  - [Develop I/O API for Lunatik](#lunatik_io)
  - [Google Cloud IoT Core Interface in Lua](#iot)

  

-----

<a id="pallene"></a>

### C Header File Parser in Lua Using Clang AST

#### Brief Explanation

[Pallene](http://www.inf.puc-rio.br/~hgualandi/papers/Gualandi-2018-SBLP.pdf) is a statically-typed companion language for Lua. Its main goal is improving Lua's performance by rewriting its code with static-type annotations. One of the features we want to incorporate in Pallene eventually is an FFI to C. Since Pallene is statically typed, it may call C efficiently. This feature requires Pallene to parse C header files to manipulate its structures and call its functions.

In this project, you should write a parser to C header files using Clang AST. Clang AST is a C++ library that parses a C file and generates an abstract syntax tree (AST). Because we wrote the Pallene compiler in Lua, we need a Lua library that takes as input a C file and generate as output a Lua representation for C declarations. This library should be written from scratch separately from Pallene.

#### Tools

  - Clang AST (http://clang.llvm.org/docs/IntroductionToTheClangAST.html)
  - Lua C API (https://www.lua.org/pil/24.html)

#### Expected Results

  - Define a Lua representation for C declarations
  - Implementing a Lua library that parses C using Clang AST
  - Automated tests and documentation of the Library

#### Knowledge Prerequisites

  - C++
  - Lua C API

#### Skill Level

Intermediate

#### Mentor

[Gabriel de Quadros Ligneul](mailto:gqligneul@gmail.com)

  

-----

<a id="ceu"></a>

### Low-Power Interrupt-Based Drivers in Céu-Arduino

#### Background

Currently, most sensing operations in Arduino libraries freeze the rest of the application until they complete, e.g.:

  - Reading an analog pin with [analogRead](https://www.arduino.cc/en/Reference/AnalogRead) takes about 100 microseconds to complete.
  - Measuring a distance with an [ultrasonic sensor](http://playground.arduino.cc/Code/NewPing) takes about 30 milliseconds.

The use of interrupts allows programs to remain executing while sensing operations progress and complete.

In this project, the student will develop interrupt-based device drivers in the programming language Céu aiming for high concurrency and energy efficiency.

*Céu-Arduino* supports the development of Arduino applications in the programming language Céu:

  - Source Code: <https://github.com/ceu-lang/ceu-arduino/>
  - Documentation: [https://ceu-lang.github.io/ceu-arduino/](http://ceu-lang.github.io/ceu-arduino/)
  - Chat: [https://gitter.im/ceu-lang/ceu](https://gitter.im/fsantanna/ceu)

Céu is a reactive language that aims to offer a higher-level and safer alternative to C:

  - Home Page: <http://www.ceu-lang.org/>
  - Source code: <https://github.com/ceu-lang/ceu/>

Céu-Arduino empowers the development of Arduino applications with the following extensions:

  - Awaiting events in direct/sequential style.
  - Parallel lines of execution with
      - safe abortion;
      - deterministic behavior (in contrast with threads).
  - Asynchronous loops for heavy computations.
  - Interrupt-driven operation mode.
  - Seamless integration with standard Arduino (e.g., `digitalWrite`, `random`, etc).

Céu supports [interrupts](https://github.com/ceu-lang/ceu-arduino#switching-a-led-with-interrupts) as a primitive construct, reducing programming efforts considerably.

Céu-Arduino already provides interrupt-based drivers for a [variety of peripherals](https://github.com/ceu-arduino/), such as external pins, timers, ADC, SPI, I2C, and the USART.

#### The Project

The project consists of developing new interrupt-based drivers for Céu-Arduino for additional devices:

  - SPI peripherals
  - I2C peripherals
  - Libraries built on top of other drivers (e.g., RF transceiver, ultrasonic sensor, accelerometer).

We also expect the student to develop at least one complete application to evaluate its functionality and energy consumption.

#### Tools

  - [Céu](https://github.com/ceu-lang/ceu/) is the programming language used in Céu-Arduino.
  - [Céu-Arduino](https://github.com/ceu-lang/ceu-arduino/) is the Céu binding for Arduino.
  - [Arduino MEGA](https://store.arduino.cc/usa/arduino-mega-2560-rev3) or equivalent.
  - A sort of Arduino peripherals.

#### Prerequisites

**We expect the student to own the Arduino board and peripherals.**

We also expect the student to know **C** and **interrupt services routines** in Arduino microcontrollers.

We ask applicants to complete the following activities *before* the application period:

1.  Install Céu and Céu-Arduino and compile and test some existing examples.
2.  Create a simple example in Céu-Arduino using some sensors and actuators (not necessarily using interrupts).
3.  Create a simple example in C that uses interrupt-driven analog reads.
4.  Fork our [Céu-Arduino](https://github.com/ceu-lang/ceu-arduino/) project on *github* and commit the new examples.

#### Skill level

Hard

#### Mentor

[Francisco Sant'Anna](http://www.ceu-lang.org/chico)

  

-----

<a id="apolo"></a>

### Apolo: a Library to aid the Creation of Scripts in Lua, replacing Shell Scripts and Windows Batch Files

#### Background

Scripts are needed for many different tasks. For example, some programs need some environment adjustments to be run properly (PATH adjustments, set up plugin directories, etc.). These scripts are usually Shell scripts in Unix-like operating systems and .BAT scripts in Windows. To avoid the problems associated with these kinds of scripts (unintuitive syntax being one of them), many people choose other languages for the task, like Perl, Python or Ruby. While these languages usually work well for the given goal, when the platform doesn't provide interpreters for these languages natively, they become another dependency that either the user has to pull in or the developer has to bundle together with their program - which can be a problem, considering that these interpreters are usually several megabytes in size.

It's already possible to write launcher scripts in Lua today, since Lua is just as much of a general-purpose programming language as the ones mentioned above. Also, with a size of a few hundred kilobytes, the weight a Lua interpreter will put on the distribution of a program is negligible for most applications, making it a very good fit in that regard.

However, pure Lua lacks some core functionalities needed by launcher scripts, making it necessary for the developer to select a set of libraries that suits their purpose (e.g. filesystem manipulation); also, many convenience features present in Bash and the languages above are not present in Lua. So, while it's possible to write these kinds of scripts in Lua, it is not as convenient as it is in the languages above.

#### The Project

[Apolo](https://gitlab.com/luizromario/apolo) is a library created with the goal of making writing scripts in Lua as convenient as writing them in, say, Python or Perl, by removing the need to select a set of necessary variables for the task and providing an API with similar functionalities.

Although some things are already implemented, like running processes, filesystem navigation and manipulation and environment manipulation, it's still on a very early stage. Ideally, we'd like to make it possible to write anything you'd write in Bash without the need for external variables, but, in order of importance, here's what we'd like to see implemented:

  - Basic syntax and commands from Bash (\`which\`, filtering, etc.)
  - Something similar to Bash's double-ticks
  - Redirecting IO
  - Piping
  - Management of processes in the background (you can currently run background processes, but they're completely detached)
  - Make it possible to build an \`apolo\` binary that includes the Apolo library built-in.
  - Other features (like dialogs) are welcome if there's time for them

It's very important that most things that are convenient to do in Bash are at least almost as convenient to do in Lua + Apolo, which is why, for example, there should be no external dependencies besides Lua 5.3. It's also important to make Apolo run on at least Linux and Windows.

#### Tools

  - The [Lua progamming language](https://lua.org).
  - Windows and Linux (at least).
  - [GCC](https://gcc.gnu.org) or [Clang](https://clang.llvm.org).
  - [MinGW](http://www.mingw.org/) (for Windows).

#### Prerequisites

We expect the student to know C, how to build Lua, how to use, write, and build Lua libraries (both pure Lua libraries and C libraries, which includes knowing the C API), how to deploy Lua libraries together with Lua (how to use \`LUA\_PATH\` and \`LUA\_CPATH\`). We also expect the user to have some knowledge of Bash.

Before the application period, the student should do the following, on both Linux and Windows:

1.  Download and build the latest version of Lua
2.  Build Apolo linking to the version of Lua built in the previous step
3.  Take some moderately sized (at least 50 loc) real shell script and rewrite it using only Lua + Apolo
4.  Fork the Apolo repo and commit the example

#### Skill level

Medium

#### Mentor

[Luiz Romário Santana Rios](mailto:romariorios@protonmail.com)

  

-----

<a id="lpeg"></a>

### A Parser Generator with Semi-Automatic Error Recovery based on LPeg(Label)

#### Brief explanation

[Parsing Expression Grammars](http://bford.info/pub/lang/peg) (PEGs) are an expressive formalism for the design and implementation of top-down parsers with local backtracking. [LPeg](http://www.inf.puc-rio.br/~roberto/lpeg/) is a tool that provides an implementation of PEGs for Lua, while [LPegLabel](https://github.com/sqmedeiros/lpeglabel/) is an extension of LPeg with some facilities for error reporting and recovery.

The goal of this project is to build a parser generator on top of the new version of LPegLabel. This new tool should make easier the description of a parser for a programming language and should also implement an [algorithm](https://dl.acm.org/citation.cfm?id=3264638) to automatically annotate a PEG with labels, in order to provide a quasi-automatic error recovery mechanism.

#### Tools

  - [LPegLabel](https://github.com/sqmedeiros/lpeglabel/)
  - [LPeg](http://www.inf.puc-rio.br/~roberto/lpeg/)

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

<a id="lunatik_dns"></a>

### Develop an in-kernel DNS over HTTPS server for Lunatik

#### Brief explanation

[Lunatik](http://netbsd.org/~lneto/dls14.pdf) is a kernel-level Lua interpreter version for scripting the Linux kernel. For example, it allows users to [filter packets using Lua scripts](http://netbsd.org/~lneto/eurobsdcon14.pdf).

[DNS over HTTPS](https://tools.ietf.org/html/rfc8484) is a new secure way of requesting encrypted DNS queries to prevent eavesdropping and improve users privacy.

[ULP (Upper Layer Protocol)i](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/Documentation/networking/tls.txt?h=v5.0-rc4) is a new feature merged recently in the Linux kernel which allows user-space programs to attach L7 functionalities to the in-kernel socket structure.

The purpose of this project is to implement an in-kernel encrypted DNS server using Lunatik and its [ULP binding](https://github.com/sav/ulp-lua). We expect also adjustments on ULP binding, documentation and benchmarks as part of this project.

#### Expected results

  - DNS over HTTPS server for Lunatik
  - Documentation and benchmarks

#### Knowledge prerequisites

C, Lua, OS, Networking (and some courage :) )

You must be comfortable reading technical documentation, such as RFCs.

#### Skill Level

Advanced

#### Mentors

[Pedro Tammela](mailto:pctammela@gmail.com), [Lourival Vieira Neto](mailto:lourival.neto@gmail.com), [Ana Lúcia de Moura](mailto:analuciadm@gmail.com)

  

-----

<a id="lunatik_io"></a>

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

[Lourival Vieira Neto](mailto:lourival.neto@gmail.com), [Ana Lúcia de Moura](mailto:analuciadm@gmail.com), [Pedro Tammela](mailto:pctammela@gmail.com)

  

-----

<a id="iot"></a>

### Google Cloud IoT Core Interface in Lua

#### Background

**Cloud IoT Core** is a fully managed service that allows to easily and securely connect, manage, and ingest data from millions of globally dispersed devices.

Cloud IoT Core, in combination with other services on Google Cloud IoT platform, provides a complete solution for collecting, processing, analyzing, and visualizing IoT data in real time to support improved operational efficiency.

The interface with Cloud IoT Core is through APIs, with examples in the following programming languages: C\#, Go, Java, NODE.JS, PHP, Python, Ruby.

**Android Things** allows Android developers to create solutions for IoT, from prototype to production quickly.

#### The Project

[Lua](http://www.lua.org) is considered one of the most suitable programming languages for use in the area of IoT - Internet of Things. This [video](https://vimeo.com/292779036) produced by ACM presents the main information on Lua and its possible use in IoT.

The project consists of developing an interface, in Lua, for the set of Cloud IoT Core APIs, through two REST resources:

  - cloudiot methods, to facilitate device manager tasks
  - cloudiotdevice methods, to facilitate device communication over the HTTP bridge

In addition, the project aims to offer a library of functions that will allow the development of applications for IoT in development environments that use Lua, such as Love 2D and Corona platforms, similarly as in Android Things.

#### Tools

  - The language [Lua](http://www.lua.org) will be used in the project
  - Information about IoT-targeted services offered by Google can be accessed on the [Cloud IoT Core pages](https://cloud.google.com/iot-core/)
  - Frameworks application development in Lua, such as [Love 2D](https://love2d.org/) or [Corona](https://docs.coronalabs.com/)
  - A list of IoT devices, low cost and simple to operate, will be provided for the tests to be performed

#### Prerequisites

We expect the student to have a heavy knowledge about Lua (including the Lua/C interface) and an intermediate knowledge about the area of IoT- internet of things and the use of REST interface with web-based systems

We ask applicants to complete the following activities before the application period:

  - Sign up for a free trial on [Google Cloud Platform](https://cloud.google.com/)
  - Study the features and set of APIs offered by Google Cloud IoT
  - Accomplish some testing with a device for IoT, using one of the indicated devices in the list to be provided and one of the suggested development frameworks

#### Skill level

Intermediate

#### Mentor

[Fernando Jefferson](mailto:fjefferson@inf.puc-rio.br)
