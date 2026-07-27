<!-- Archived from http://www.lua.inf.puc-rio.br/gsoc/ideas2017.html; this is the ideas list as published for GSoC 2017. -->

## Ideas List - Google Summer of Code 2017

  - [Improve the HTTPS module of LuaSec](#luasec)
  - [Develop I/O API for NetBSD Kernel Lua](#netbsd)
  - [Lua Client for Strava V3 API](#strava)
  - [Editor Support for Typed Lua](#typed)
  - [Parser Generator Based on LPeg(Label)](#peg)
  - [Adapt CGILua SAPI launcher to explore all WSAPI features](#cgilua)
  - [Interrupt-based drivers and libraries for Céu-Arduino](#ceu)
  - [Porting Terra, a tiny IoT Virtual Machine, to Android Devices.](#terradroid)

  

-----

<a id="luasec"></a>

### Improve the HTTPS module of LuaSec

#### Brief explanation

The [LuaSec](https://github.com/brunoos/luasec/wiki) HTTPS module was built on top of [LuaSocket](https://github.com/diegonehab/luasocket) HTTP and its current versions presents some problems due to limited integration.

The aim of this project is to improve the HTTPS module, fixing the issues and adding some new features.

#### Expected results

  - Make the HTTPS module more self-contained, fixing the dependency problem.
  - New features: proxy and SNI (Server Name Indication).
  - Support to HTTP/2 is a plus.

#### Knowledge prerequisites

  - C, Lua, Git, HTTP protocol.

#### Skill level

Easy / Medium

#### Mentor

[Bruno Silvestre](mailto:brunoos@inf.ufg.br)

  

-----

<a id="netbsd"></a>

### Develop I/O API for NetBSD Kernel Lua

#### Brief explanation

[The NetBSD Operating System](http://www.netbsd.org) has a kernel-level Lua interpreter version for [scripting its kernel](http://netbsd.org/~lneto/dls14.pdf). For example, it allows users to [filter packets using Lua scripts](http://netbsd.org/~lneto/eurobsdcon14.pdf).

The main difference between kernel Lua and regular user-level Lua is that kernel Lua has no support for standard libraries that depend on the operating system (e.g., io and os) and for floating-point numbers. The purpose of this project is to develop kernel Lua libraries to provide I/O functionality to kernel scripts. This API should provide access both for file system and network. It should be implemented as [NetBSD loadable kernel modules](http://www.home.unix-ag.org/bmeurer/NetBSD/howto-lkm.html), binding the kernel internal implementation for files and sockets user-level API.

#### Expected results

  - Kernel Lua File Library
  - Kernel Lua Socket Library
  - Documentation and Benchmarks

#### Knowledge prerequisites

C, Lua, OS (and some courage :) )

#### Skill level

Advanced

#### Mentor

[Lourival Vieira Neto](mailto:lneto@NetBSD.org)

  

-----

<a id="strava"></a>

### Lua Client for Strava V3 API

#### Brief explanation

[Strava](https://www.strava.com) is a popular social network for athletes that we can use to track cycling, running or swimming activities and share them with our connections. The [Strava V3 API](https://strava.github.io/api/) is publicly available and developers can use it to access Strava's dataset for creating custom applications. As an example, [RELIVE.cc](https://www.relive.cc/) gets your latest Strava ride and creates a movie of your ride that is played with Google Earth 3D. Although Strava allows developers to create their own applications, its [library support](https://strava.github.io/api/#libraries) is still limited and there is no support for Lua.

The aim of this project is to create a Strava library for Lua, so we can use it to create Strava applications with Lua. We also expect that at least one application example should be developed using the new library. We would like to use [Typed Lua](http://github.com/andremm/typedlua) to define our interfaces, as we might want to move to Typed Lua when it is released.

#### Expected results

  - A Lua Client for Strava V3 API.
  - An example application that uses the Lua library.

#### Knowledge prerequisites

  - Lua.
  - RESTful WebServices.
  - JSON.
  - Github.
  - Running, Cycling or Swimming.

#### Skill level

Medium

#### Mentor

[André Maidl](mailto:amaidl@inf.puc-rio.br)

  

-----

<a id="typed"></a>

### Editor Support for Typed Lua

#### Brief explanation

[Typed Lua](http://github.com/andremm/typedlua) is a statically typed extension of the Lua language. Currently, Typed Lua's user interface is just a command-line compiler that compiles a file at a time. The goal of this project is threefold: first to turn the command-line compiler into a daemon that watches a file tree for changes, recompiling the files whenever they change, and keeping as its internal state all the errors and types extracted from these files. This daemon, or *analysis server*, can then answer to HTTP queries about the files in the tree, with the answers in JSON format. Finally, editor plugins can interface with the server to display error and autocomplete information about the files that the programmer is currently editing.

#### Expected results

  - An analysis server for Typed Lua that watches a directory tree and compiles any Typed Lua source files that change
  - Webservices in the analysis server that serve information (in JSON format) on the source files in the tree about parse/type errors and type information for autocomplete purposes
  - Editor plugins for [Atom](https://atom.io), [VS Code](https://code.visualstudio.com/), and [Zerobrane Studio](https://studio.zerobrane.com/) that connect to the analysis server

#### Prerequisites

Knowledge of Lua, JavaScript, JSON, RESTful webservices, file watching APIs. Knowledge of how the Typed Lua typechecker works is not necessary.

#### Skill level

Medium

#### Mentor

[Fabio Mascarenhas](https://www.dcc.ufrj.br/~fabiom/index.en.html)

  

-----

<a id="peg"></a>

### Parser Generator Based on LPeg(Label)

#### Brief explanation

[Parsing Expression Grammars](http://bford.info/pub/lang/peg) (PEGs) are an expressive formalism for the design and implementation of top-down parsers with local backtracking. [LPeg](http://www.inf.puc-rio.br/~roberto/lpeg/) is a tool that provides an implementation of PEGs for Lua, while [LPegLabel](https://github.com/sqmedeiros/lpeglabel/) is an extension of LPeg with some facilities for error reporting and recovery.

The goal of this project is to build a parser generator on top of LPegLabel. This new tool should make easier the description of commom idioms and should make error reporting more automatic.

The new parse generator will be used to (re)write parsers, such as the [*lua-parser*](https://github.com/andremm/lua-parser).

#### Tools

  - [LPegLabel](https://github.com/sqmedeiros/lpeglabel/)
  - [LPeg](http://www.inf.puc-rio.br/~roberto/lpeg/)
  - Lua libraries whose parsers will be rewritten

#### Expected results

  - A parser generator tool

  - The (re)writing of at least 2 parsers, including *lua-parser*, with the new tool. The description of the parsers using the new tool should be easier than using plain LPeg(Label).

  - A proper documentation
    
    A marginal result would be the improvement of the LPegLabel tool based on the difficulties perceived during the project.

#### Prerequisites

We expect the applicants to have a good knowledge of *parsing* and to develop familiarity with LPeg and LPegLabel before the project starts. The applicant should have used at least one parser generator tool, such as yacc/bison, ANTLR, JavaCC, PEG.js, etc.

For this reason, we may ask the applicants to perform some activities **before** the application period.

#### Skill level

Medium / Advanced

#### Mentor

[Sérgio Medeiros](https://sites.google.com/site/sqmedeiros/)

  

-----

<a id="cgilua"></a>

### Adapt CGILua SAPI launcher to explore all WSAPI features.

#### Brief explanation

[CGILua](http://keplerproject.github.io/cgilua/) is a tool for creating dynamic Web pages and manipulating input data from Web forms. One of advantages of CGILua is its abstraction of the underlying Web server. CGILua can be used with a variety of Web servers and, for each server, with different launchers. A launcher is responsible for the interaction of CGILua and the Web server, for example mod\_lua on Apache. The reference implementation of CGILua launchers is Kepler.

[WSAPI](http://keplerproject.github.io/wsapi/) is an API that abstracts the web server from Lua web applications. WSAPI provides a set of helper libraries that help with request processing and output buffering.

Currently, CGILua has an implementation of an abstract underlying server which is almost the same of WSAPI itself. This project proposes a reimplementation of this layer (called SAPI) to explore WSAPI fully. This should improve the performance and simplify maintenance.

#### Expected results

  - Rewrite CGILua library to dispense SAPI module and use WSAPI directly.

#### Knowledge prerequisites

Advanced Lua programming is mandatory, since both tools (CGILua and WSAPI) are not naive software. A good understanding of the Lua environment concept is particularly necessary in this project.

Web programming experience can be very helpful especially to understand the context of use of these tools.

#### Skill level

Medium

#### Mentor

Tomás Guisasola

  

-----

<a id="ceu"></a>

### Interrupt-based drivers and libraries for Céu-Arduino

#### Background

Currently, most operations in Arduino libraries freeze the rest of the application until they complete:

  - Reading an analog pin with [analogRead](https://www.arduino.cc/en/Reference/AnalogRead) takes about 100 microseconds to complete.
  - Measuring distance with an [ultrasonic sensor](http://playground.arduino.cc/Code/NewPing) takes about 30 milliseconds.

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

Céu-Arduino already provides interrupt-based drivers for [pins, internal timers, and the USART](https://github.com/fsantanna/ceu-arduino/tree/master/include/arduino/isr).

#### The Project

The project consists of developing new interrupt-based drivers and libraries for chips and peripherals, e.g.:

  - Arduino's internal analog-to-digital converter.
  - Arduino's internal SPI and I2C buses.
  - Arduino's internal EEPROM.
  - An [external real-time clock](http://forum.arduino.cc/index.php?topic=278270.0).
  - Some sensor libraries built on top of these drivers, e.g.: ultrasonic, accelerometer, etc.

#### Tools

  - [Céu](https://github.com/fsantanna/ceu/) is the programming language used in Céu-Arduino.
  - [Céu-Arduino](https://github.com/fsantanna/ceu-arduino/) is the Céu binding for Arduino.
  - [Arduino UNO](https://www.arduino.cc/en/Main/ArduinoBoardUno) is an Arduino development board.
  - A sort of Arduino peripherals.

#### Prerequisites

**We expect the student to own an Arduino board and peripherals.**

We also expect the student to know **C** and **interrupt services routines** in Arduino or AVR microcontrollers.

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

<a id="terradroid"></a>

### Porting Terra, a tiny IoT Virtual Machine, to Android Devices.

#### Brief explanation

[Terra](http://www.inf.puc-rio.br/%7Eabranco/terra.html) is a system based on a tiny virtual machine and combines a reactive scripting language with a set of customized components. Originally, Terra was designed to run in WSN/IoT nodes with limited resources. These nodes, typically, have small microcontrolers and communicate using specific radio standards like IEEE 802.15.4 (based on ZigBee). Terra uses Céu-T as its scripting language and implements a component-based virtual machine VM-T to be customized for different application domains. We built VM-T using the [nesC](http://nescc.sourceforge.net/) programming language and the [TinyOS](http://tinyos.net) operating system.

We have already started some initiatives to port Terra to different devices to enable interoperability in heterogeneous IoT network. These initiatives include ports to different operating systems and devices with different levels of resources. These initiatives include the use of radio technologies like IEEE 802.11 standards and the use of Linux on a RaspberryPI device.

The aim of this project is to port Terra Virtual Machine VM-T to Android devices. This port will enable interoperability of Android devices with others devices running Terra, allowing experiments with more powerful mobile devices interacting with a heterogeneous IoT network.

We plan two main development activities. One will be the development of an integration layer between the VM engine and the Android system. The other will be the customization to access some sensors and actuators of the device.

#### Expected results

  - A functional port of Terra VM to Android devices.
  - A set of Terra application examples, including a gateway between different radio standards.

#### Knowledge prerequisites

  - Android - programming in C. (Timer and UDP/IP library)
  - nesC - Desirable basic knowledge.
  - Github.

#### Skill level

Medium

#### Mentor

[Adriano Branco](mailto:abranco@inf.puc-rio.br)
