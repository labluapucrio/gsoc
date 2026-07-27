<!-- Archived from http://www.lua.inf.puc-rio.br/gsoc/ideas2015.html; this is the ideas list as published for GSoC 2015. -->

## Ideas' List - Google Summer of Code 2015

  - [LuaRocks add-ons system](#luarocks)
  - [Port Lua Test Suite to NetBSD Kernel](#kerneltest)
  - [Elasticsearch Lua client (elasticsearch-lua)](#elastic)
  - [Add support for left recursion to LPeg](#lpeg)
  - [Switch Typed Lua from optional typing to gradual typing](#typed)
  - [Adapt CGILua SAPI launcher to explore all WSAPI features](#cgilua)
  - [Add support for WSDL generation to LuaSOAP](#luasoap)
  - [Add support for prepared statements in LuaSQL](#luasql)
  - [Multi-CPU usage in VLC](#vlc)
  - [Multi-CPU usage in wireshark](#wireshark)
  - [Develop a binary serialization format with support for dynamically types values and an RPC protocol for dynamically typed invocations based on this format.](#dynserial)
  - [Develop a library for Lua that allows Lua programs to access features provided by the platform's underlying operating system (OS) kernel, such as process control, network access, file system, event notification, etc.](#loski)
  - [Port an SDL-based C++ open source game to Céu](#ceu)

  

-----

<a id="luarocks"></a>

### LuaRocks add-ons system

<a id="briefexplanation"></a>

#### Brief explanation

[LuaRocks](http://luarocks.org) is a package manager for Lua modules. Since version 1.0, the format of the package specification file (rockspec) was unchanged, in the name of compatibility. For the next major release of LuaRocks, we intend to make a backward-compatible revision to the format. However, instead of guessing which features will be needed in the forthcoming years, the idea is to make the format extensible through *add-ons*, as discussed in this [Lua Workshop 2014 talk](https://www.youtube.com/watch?v=WiZqfpZLSA8).

There are two sides to making an application extensible: defining hooks to the application where extensions will plug into, and defining a public API, which is the parts of the application that the extensions will see/access.

This includes major design work, and the student is not expected to do this alone: the design part will be discussed with the mentor and the LuaRocks community at large through the [LuaRocks mailing list](https://lists.sourceforge.net/lists/listinfo/luarocks-developers). The coding part, of course, is up to the student.

The best way to evaluate new APIs is to put them to work: the second phase of the project will be to write some add-ons, to exercise the new features. Two features that are often requested by the community are support for running tests and generating documentation files: these would make great add-ons.

<a id="expectedresults"></a>

#### Expected results

  - Extending the LuaRocks rockspec reader to allow new entries created by add-ons
  - A system of hooks in LuaRocks to trigger actions programmed by add-ons
  - A sandbox environment for presenting a restricted API to add-ons
  - Add-ons for running tests and generating documentation

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

  - Lua - comfortable writing code for Lua 5.x (LuaRocks runs in Lua 5.1-5.3)
  - LuaRocks - experience with writing rockspecs (if you never wrote any, pick a module that's not yet available in the LuaRocks repository and give it a try\!)
  - Git (experience with the Github workflow is a bonus)

<a id="skilllevel"></a>

#### Skill level

Medium

<a id="mentor"></a>

#### Mentor

[Hisham Muhammad](http://hisham.hm/)

  

-----

<a id="kerneltest"></a>

### Port Lua Test Suite to NetBSD Kernel

<a id="briefexplanation"></a>

#### Brief explanation

[The NetBSD Operating System](http://www.netbsd.org) has a kernel-level Lua interpreter version for [scripting its kernel](http://netbsd.org/~lneto/dls14.pdf). For example, it allows users to [filter packets using Lua scripts](http://netbsd.org/~lneto/eurobsdcon14.pdf).

The main difference between kernel Lua and regular user-level Lua is that kernel Lua doesn't have support for standard libraries that depend on operating system (e.g., io and os) and for floating-point numbers. The purpose of this project is to port the [Lua Test Suite](http://www.lua.org/tests/) to NetBSD kernel. That is, to adapt scripts from Lua test suite and develop a [NetBSD loadable kernel module](http://www.home.unix-ag.org/bmeurer/NetBSD/howto-lkm.html) containing the C portion of Lua test suite.

<a id="expectedresults"></a>

#### Expected results

  - Adapted test scripts for kernel Lua
  - Kernel module for testing the [Lua C API](http://www.lua.org/manual/5.3/manual.html#4)

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

  - C, Lua (and some patience :) )

<a id="skilllevel"></a>

#### Skill level

Medium

<a id="mentor"></a>

#### Mentor

[Lourival Vieira Neto](mailto:lourival.neto@gmail.com)

  

-----

<a id="elastic"></a>

### Elasticsearch Lua client (elasticsearch-lua)

<a id="briefexplanation"></a>

#### Brief explanation

[Elasticsearch](http://elasticsearch.com/) is a distributed and scalable search engine. It is written in Java and, besides the transport protocol (Java to Java), it offers a very complete REST API accessed through [JSON](http://json.org/)

Elasticsearch clients for different scripting languages such as Python, PHP and Perl have already been developed. However, a client for [Lua](http://lua.org/) is still not available.

This project aims to create a complete Lua client to access Elasticsearch.

<a id="expectedresults"></a>

#### Expected results

  - A complete Lua client to access the Elasticsearch REST API.

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

  - Lua - medium (socket and metatable experience is important)
  - Elasticsearch - basic/medium
  - JSON - medium
  - HTTP - basic/medium

<a id="skilllevel"></a>

#### Skill level

Medium

<a id="mentor"></a>

#### Mentor

[Pablo Musa](http://www.inf.puc-rio.br/~pmusa/)

  

-----

<a id="typed"></a>

### Switch Typed Lua from optional typing to gradual typing

<a id="briefexplanation"></a>

#### Brief explanation

[Typed Lua](https://github.com/andremm/typedlua) is an optional type system for Lua, and its main goal is to provide static type checking for Lua. To do that, Typed Lua extends the syntax of Lua 5.3 to introduce optional type annotations, and performs local type inference to detect more precise types for unannotated expressions. Even though the compiler warns the programmer about type errors, it always removes the type annotations to generate Lua code that runs in unmodified Lua implementations, and this code does not insert any run-time checks that ensure safety between dynamically typed and statically typed code.

<a id="expectedresults"></a>

#### Expected results

The aim of this project is to make the Typed Lua compiler insert run-time checks in the [gradual typing](http://wphomes.soic.indiana.edu/jsiek/what-is-gradual-typing/) style. These run-time checks are assertions that inspect the interaction between dynamically typed and statically typed code to guarantee that dynamically typed code does not violate statically typed code. We also expect an evaluation of these run-time checks to identify what is the overhead that they introduce in the execution of the generated code.

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

Lua and Type Systems

<a id="skilllevel"></a>

#### Skill level

Hard

<a id="mentor"></a>

#### Mentor

André Murbach Maidl

  

-----

<a id="cgilua"></a>

### Adapt CGILua SAPI launcher to explore all WSAPI features.

<a id="briefexplanation"></a>

#### Brief explanation

[CGILua](http://keplerproject.github.io/cgilua/) is a tool for creating dynamic Web pages and manipulating input data from Web forms. One of advantages of CGILua is its abstraction of the underlying Web server. CGILua can be used with a variety of Web servers and, for each server, with different launchers. A launcher is responsible for the interaction of CGILua and the Web server, for example using ISAPI on IIS or mod\_lua on Apache. The reference implementation of CGILua launchers is Kepler.

[WSAPI](http://keplerproject.github.io/wsapi/) is an API that abstracts the web server from Lua web applications. WSAPI provides a set of helper libraries that help with request processing and output buffering.

Actually CGILua has an implementation of an abstract underlying server which is almost the same of WSAPI itself. This project proposes a reimplementation of this layer (called SAPI) to explore WSAPI fully. This should improve the performance and simpify maintenance.

<a id="expectedresults"></a>

#### Expected results

  - Rewrite CGILua library to dispense SAPI module and use WSAPI directly.

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

Advanced Lua programming is mandatory, since both tools (CGILua and WSAPI) are not naive software. A good understanding of the Lua environment concept is particularly necessary in this project.

Web programming experience can be very helpful especially to understand the context of use of these tools.

<a id="skilllevel"></a>

#### Skill level

Medium

<a id="mentor"></a>

#### Mentor

Tomás Guisasola

  

-----

<a id="luasoap"></a>

### Add support for WSDL generation to LuaSOAP

<a id="briefexplanation"></a>

#### Brief explanation

[LuaSOAP](http://tomasguisasola.github.io/luasoap/) is a library to ease the use of [SOAP](http://www.w3.org/TR/soap/). LuaSOAP provides a very simple API that convert Lua tables to and from XML documents. It also offers a simple way to invoke remote Web Services without having to deal directly with SOAP messages. In fact, LuaSOAP also provides a simple way to offer Web Services -- the server side -- but it lacks support for WSDL generation of the offered services.

[WSDL](http://www.w3.org/TR/wsdl) is an XML format for describing network services. It is used to describe operations and messages -- with its types -- offered by Web Services. Since Lua code does not include type information, automatic generation has to be based on some kind of hand-made declarative information.

<a id="expectedresults"></a>

#### Expected results

  - Define the format to describe complementary WSDL information in Lua
  - Implement an automatic generator of WSDL documents
  - Test and document everything

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

Lua programming; client-server web architecture; SOAP and WSDL specifications.

  - Basic programming in Lua is mandatory
  - Web programming experience is very appreciated but not mandatory
  - SOAP and WSDL specifications could be learned during the project

<a id="skilllevel"></a>

#### Skill level

Medium

<a id="mentor"></a>

#### Mentor

Tomás Guisasola

  

-----

<a id="luasql"></a>

### Add support for prepared statements in LuaSQL

<a id="briefexplanation"></a>

#### Brief explanation

[LuaSQL](http://www.keplerproject.org/luasql/) is a generic interface from Lua to a DBMS. It aims at portability over performance, but it allows extensions to suit the particularities of each DBMS.

The inclusion of support for prepared statements in LuaSQL has been discussed thoroughly some time ago, but since each DBMS offers very different APIs there is no standard that could be defined to assure portability between them. Anyway the demand persists.

This project proposes the addition of a minimal API that would allow each driver to implement prepared statements according to its DBMS restrictions.

<a id="expectedresults"></a>

#### Expected results

  - Adapt the API to each LuaSQL driver according to its particularities
  - Implement the new functions to each driver
  - Test and document everything

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

C, Lua and C API for Lua:

  - C is mandatory.
  - Knowledge of the C API for Lua is mandatory, although it is not too difficult to be learned during the project.
  - Basic programming in Lua is very helpful, but not mandatory, since the examples and test-cases are very simple.

<a id="skilllevel"></a>

#### Skill level

Hard

<a id="mentor"></a>

#### Mentor

Tomás Guisasola

  

-----

<a id="vlc"></a>

### Multi-CPU usage in VLC

<a id="briefexplanation"></a>

#### Brief explanation:

[VLC](https://wiki.videolan.org/VLC_media_player/) is a free and open source cross-platform multimedia player and framework that plays most multimedia files as well as DVD, Audio CD, VCD, and various streaming protocols. Lua scripts can be added to VLC for tasks such as playlist construction and service discovery. Such tasks may involve a lot of parsing and communication and could benefit from using multiple CPUs when available. The purpose of this project is to include support for multi-CPU usage in VLC, using [luaproc](http://askyrme.github.io/luaproc/), a library that allows programmers to create multiple independent execution flows of Lua code that can run inparallel, communicating only via message-passing.

<a id="expectedresults"></a>

#### Expected results:

Multi-CPU support in VLC.

<a id="knowledgeprerequisite"></a>

#### Knowledge prerequisite:

C, Lua

<a id="skilllevel"></a>

#### Skill level:

Medium

<a id="mentor"></a>

#### Mentor:

Alexandre Skyrme

  

-----

<a id="wireshark"></a>

### Multi-CPU usage in wireshark

<a id="briefexplanation"></a>

#### Brief explanation:

The [wireshark network protocol analyser](http://www.wireshark.org/) allows programmers to use Lua to write dissectors, post-dissectors and taps. Dissectors are protocol analysers, while post-dissectors are executed after all others dissectors, and taps are used to collect information after packet dissection. Protocol dissection can involve time constraints, and it would be nice to benefit from multi-CPU processing power in dissector script. The purpose of this project is to include support for multi-CPU usage in wireshark, using [luaproc](http://askyrme.github.io/luaproc/), a library that allows programmers to create multiple independent execution flows of Lua code that can run inparallel, communicating only via message-passing.

<a id="expectedresults"></a>

#### Expected results:

We expect the support for Multi-CPU usage in wireshark.

<a id="knowledgeprerequisite"></a>

#### Knowledge prerequisite:

C, Lua

<a id="skilllevel"></a>

#### Skill level:

Medium

<a id="mentor"></a>

#### Mentor:

Alexandre Skyrme

  

-----

<a id="lpeg"></a>

### Add support for left recursion to [LPeg](http://www.inf.puc-rio.br/~roberto/lpeg/)

<a id="briefexplanation"></a>

#### Brief explanation

Parsing Expression Grammars (PEGs) are an expressive formalism for designing and implementing top-down parsers with local backtracking. A frequently missed feature of PEGs is left recursion, which is commonly used in Context-Free Grammars (CFGs) to encode left-associative operations.

There is a [formal extension to the PEGs formalism](http://arxiv.org/pdf/1207.0443.pdf) that allows the use of left-recursive rules in a PEG grammar and that was implemented by some PEG-based tools, such as [LPegLJ](https://github.com/sacek/LPegLJ) and [IronMeta](http://ironmeta.sourceforge.net/).

The aim of this project is to create a fork of [LPeg](http://www.inf.puc-rio.br/~roberto/lpeg/), an implementation of PEGs for Lua based on a virtual parsing machine.

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

C, Lua and Parsing Expression Grammars

<a id="skilllevel"></a>

#### Skill level

Hard

<a id="mentor"></a>

#### Mentor

[Sérgio Medeiros](https://sites.google.com/site/sqmedeiros/)

  

-----

<a id="dynserial"></a>

### Develop a binary serialization format with support for dynamically types values and an RPC protocol for dynamically typed invocations based on this format.

<a id="briefexplanation"></a>

#### Brief explanation

Most RMI protocols available today are either focused on inefficient representation formats for typing information (e.g. [GIOP/IIOP (CORBA)](http://www.omg.org/spec/CORBA/3.3/Interoperability/PDF), [Hessian](http://hessian.caucho.com), [Google Protocol Buffers](https://developers.google.com/protocol-buffers/)) or on invocations where the typing information are predefined and static, therefore are absent on the data sent through the wire (e.g. [SOAP](http://www.w3.org/TR/soap/), [JSON](http://www.json.org), [Burlap](http://www.caucho.com/resin-3.0/protocols/burlap.xtp)).

Few protocols are designed to work efficiently with typed data. Invocations with typed data work well with the RPC model because it allows the identification of deployment problems (mismatch interfaces) and facilitate the dynamic evolution of distributed systems. A protocol for dynamically typed RPC should be based on a efficient serialization format for typed data, that is, information about how the data should be interpreted.

The goal of this project is to design and implement a serialization binary serialization format with the following requirements:

  - Primitive data: numeric formats (integer and floating-point), characters and boolean.
  - Structured data: serialization of usual structured data like records, arrays, maps, tuples, union, etc.
  - Optional typing: serialization of both raw data and data plus typing information.
  - Structural compatibility: type information should allow to efficiently verify whether two types are compatibile.
  - Opaque data: allow that a special form of raw data (without typing information) can be ignored without compromising the remains of the stream and that can also be passed along by a receiver that did not interpreted it.
  - Semantic information: data types that can extend a standard type with additional semantic information, like a string (sequence of characteres) with an associated charset or a record with an associated class name that provides some behavior over the data on the record.
  - Graphs: data with cyclic references.

<a id="expectedresults"></a>

#### Expected results

  - An specification of a binary serialization format with support for typed data.
  - An implementation of a library for encoding values using this format.

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

  - Programming in C (medium to advanced).
  - Familiarity with concepts of the Lua language.
  - Data structures and formats (endianess, two's complement, IEEE 754, memory pointes, etc).
  - Network protocols fundamentals.

<a id="skilllevel"></a>

#### Skill level

Hard

<a id="mentor"></a>

#### Mentor

Renato Maia

  

-----

<a id="loski"></a>

### Develop a library for Lua that allows Lua programs to access features provided by the platform's underlying operating system (OS) kernel, such as process control, network access, file system, event notification, etc.

<a id="briefexplanation"></a>

#### Brief explanation

Standard Lua distribution is based mostly on standard ANSI C libraries only. Therefore, many functionalities provided by modern platforms (like process control, file system operations, network communication, kernel event notification, etc.) are only available through third-party libraries that are developed independently and might not integrate.

The project has three main goals:

  - Design a simple and easy API that allows for different implementations over various platforms (POSIX, Linux, MacOSX, Windows, etc.) yet allowing use of a basic set of features that are provided by most popular plataforms.
  - Design an internal architecture that facilitate the replacement of the actual implementation of the features provided by the library (create process, use sockets, inspect file systems, etc). This is important to make porting the library to other platoforms easier.
  - Provide a basic/standard implementation of features provided by the library based on the codebase of existing Lua libraries that already export features of the underlying platform like [LuaSocket](http://w3.impa.br/~diego/software/luasocket/), [LuaFileSystem](http://keplerproject.github.io/luafilesystem/) and others.

A prototype for the proposed library is available [here](https://github.com/renatomaia/loski).

<a id="expectedresults"></a>

#### Expected results

A set of Lua libraries implemented at least in one major operating system platform. The library shall provide support for:

  - Creation and manipulation of processes, and possibly inter-process comunication mechanisms, such as pipes.
  - Creation and maniputation of sockets (TCP and UDP).
  - Inspection of the local file system, possibly including file attributes and permissions.
  - Notification of kernel events like process termination, socket data availability, file modification, etc.

The implementation shall also be flexible enough to facilitate the portability for other platforms.

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

  - Programming in C.
  - Familiarity with concepts of the Lua language.
  - Programming with the system API of some popular platform, such as Linux, FreeBSD, Windows, etc.

<a id="skilllevel"></a>

#### Skill level

Hard

<a id="mentor"></a>

#### Mentor

Renato Maia

  

-----

<a id="ceu"></a>

### Port an SDL-based C++ open source game to Céu

<a id="about-ceu"></a>

#### About Céu

Céu is a programming language that targets system-level development of reactive systems.

For a little introduction about the language, please watch the video in our front page:  
<http://ceu-lang.org/>

Céu appeared last year on "StrangeLoop" and the "Future Programming Workshop":  
<http://www.future-programming.org/program.html>

<a id="briefexplanation"></a>

#### Brief explanation

Port to Céu an existing C++ open source game of considerable size (30-50k lines of code).

Here are some possible projects to look for:

  - <http://en.wikipedia.org/wiki/List_of_open-source_video_games>
  - <http://www.reddit.com/r/opensourcegames>

<a id="expectedresults"></a>

#### Expected results

  - A working implementation of the game
  - A report about the experience of using Céu in the context of game development, also comparing the implementations in terms of code complexity (e.g., lines of code), resource usage (CPU, memory), etc.

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

  - SDL
  - C

(Previous experience with Céu is of course not required.)

Linux, Mac or Windows?

The current distribution of Céu is only available for Linux.  
A student using another operating system is also welcome, as long as she/he has the skills to build the development environment by her/himself.  
The compiler of Céu depends on gcc, lua-5.1, and lua-lpeg.

<a id="recommendations"></a>

#### Recommendations

Last year LabLua had over 15 submissions for only 4 slots.  
(Note that we will only know the number of slots for this year **after** the students submit the proposals.)

It is highly recommended that the student installs Céu, compiles some examples, possibly making something very simple from scratch (or changing some existing example).  
For us, this is important to see if the student will be able to keep track of the project.  
For the student, this initial experience is important to ensure that the expectations with the project match the reality.

If the student has participated in other open source projects, it is also recommended that she/he tell us about that experience

<a id="skilllevel"></a>

#### Skill level

Medium

<a id="mentor"></a>

#### Mentor

Francisco Sant'Anna
