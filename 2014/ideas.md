<!-- Archived from http://www.lua.inf.puc-rio.br/gsoc/ideas2014.html; this is the ideas list as published for GSoC 2014. -->

## Ideas' List - Google Summer of Code 2014

The same ideas, as one file per project, are in [`project-ideas/`](project-ideas/).

  - [Adapt CGILua SAPI launcher to explore all WSAPI features.](#cgilua)
  - [Add class-based object-oriented programming to Typed Lua.](#typedlua)
  - [Add labeled failures to LPeg](#lpeg)
  - [Add support for WSDL generation to LuaSOAP](#luasoap)
  - [Add support for prepared statements in LuaSQL.](#luasql)
  - [Concurrent Lua scripts execution in Redis](#luaredis)
  - [Create a library to help "memory leak" detection in Lua](#lualeak)
  - [Develop a binary serialization format with support for dynamically types values and an RPC protocol for dynamically typed invocations based on this format.](#dynserial)
  - [Develop a library for Lua that allows Lua programs to access features provided by the platform's underlying operating system (OS) kernel, such as process control, network access, file system, event notification, etc.](#loski)
  - [Multi-CPU usage in VLC](#vlc)
  - [Multi-CPU usage in wireshark](#wireshark)
  - [Porting Gameduino demos to the programming language Céu.](#gameduino)
  - [Send/Receive support for main script in the luaproc library](#luaproc)
  - [Thread-safe Lua](#threadsafelua)
  - [luashare - data sharing among parallel execution flows of Lua code](#luashare)

<a id="cgilua"></a>

### Adapt CGILua SAPI launcher to explore all WSAPI features.

<a id="briefexplanation"></a>

#### Brief explanation

CGILua \[1\] is a tool for creating dynamic Web pages and manipulating input data from Web forms. One of advantages of CGILua is its abstraction of the underlying Web server. CGILua can be used with a variety of Web servers and, for each server, with different launchers. A launcher is responsible for the interaction of CGILua and the Web server, for example using ISAPI on IIS or mod\_lua on Apache. The reference implementation of CGILua launchers is Kepler.

WSAPI \[2\] is an API that abstracts the web server from Lua web applications. WSAPI provides a set of helper libraries that help with request processing and output buffering.

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

<a id="links"></a>

#### Links

\[1\] CGILua: <http://keplerproject.github.io/cgilua/>

\[2\] WSAPI: <http://keplerproject.github.io/wsapi/>

<a id="typedlua"></a>

### Add class-based object-oriented programming to [Typed Lua](https://github.com/andremm/typedlua) \[1\].

<a id="briefexplanation"></a>

#### Brief explanation

Typed Lua is a strict superset of Lua that provides optional type annotations, and compile-time type checking. More precisely, Typed Lua is implemented as a programming language that extends Lua syntax to add optional type annotations. The compiler uses static types to perform compile-time type checking, but also allows Lua code to coexist with Typed Lua code, and generate Lua code that runs in unmodified Lua implementations.

<a id="expectedresults"></a>

#### Expected results

Typed Lua intended use is as an application language, and we view that policies for organizing a program in modules and writing object-oriented programs should be part of the language and enforced by its optional type system. An application language is a programming language that helps programmers develop applications from scratch until these applications evolve to complex systems rather than just scripts. This project aims to add class-based object-oriented programming to Typed Lua through the definition of classes, interfaces, and modules, as a way to help Lua programmers better structure their code.

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

Lua, Object-Oriented Programming, and Type Systems

<a id="skilllevel"></a>

#### Skill level

Hard

<a id="mentor"></a>

#### Mentor

[Fabio Mascarenhas](http://www.dcc.ufrj.br/~fabiom/) \[2\]

<a id="links"></a>

#### Links

\[1\] Typed Lua: <https://github.com/andremm/typedlua>

\[2\] Fabio Mascarenhas: <http://www.dcc.ufrj.br/~fabiom/>

<a id="lpeg"></a>

### Add labeled failures to [LPeg](http://www.inf.puc-rio.br/~roberto/lpeg/) \[1\].

<a id="briefexplanation"></a>

#### Brief explanation

Parsing Expression Grammars (PEGs) are an expressive formalism for designing and implementing top-down parsers with local backtracking. However, PEGs do not support the error handling techniques that are often implemented in top-down parsers, because these techniques assume the parser reads the input without backtracking.

Parsing Expression Grammars for Lua (LPeg) is a pattern-matching tool based on PEGs. Although it is quick and easy to write parsers using LPeg, like PEGs, it does not provide any support to the programmer handle parsing errors.

<a id="expectedresults"></a>

#### Expected results

There is an extension to the PEGs formalism that introduces [labeled failures](http://www.inf.puc-rio.br/~roberto/docs/sblp2013-1.pdf) as a way to annotate and label grammar pieces that should not fail \[2\]. In this approach, each label may be tied to a specific error message and resembles the concept of exceptions from programming languages. The aim of this project is to create a LPeg fork that implements this error reporting technique.

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

C, Lua, and Parsing Expression Grammars

<a id="skilllevel"></a>

#### Skill level

Hard

<a id="mentor"></a>

#### Mentor

[Roberto Ierusalimschy](http://www.inf.puc-rio.br/~roberto)

<a id="links"></a>

#### Links

\[1\] LPeg: <http://www.inf.puc-rio.br/~roberto/lpeg/>

\[2\] Exception Handling for Error Reporting in Parsing Expression Grammars: <http://www.inf.puc-rio.br/~roberto/docs/sblp2013-1.pdf>

\[3\] Roberto Ierusalimschy: <http://www.inf.puc-rio.br/~roberto>

<a id="luasoap"></a>

### Add support for WSDL generation to LuaSOAP

<a id="briefexplanation"></a>

#### Brief explanation

[LuaSOAP](http://tomasguisasola.github.io/luasoap/) \[1\] is a library to ease the use of [SOAP](http://www.w3.org/TR/soap/) \[2\]. LuaSOAP provides a very simple API that convert Lua tables to and from XML documents. It also offers a simple way to invoke remote Web Services without having to deal directly with SOAP messages. In fact, LuaSOAP also provides a simple way to offer Web Services -- the server side -- but it lacks support for WSDL generation of the offered services.

[WSDL](http://www.w3.org/TR/wsdl) \[3\] is an XML format for describing network services. It is used to describe operations and messages -- with its types -- offered by Web Services. Since Lua code does not include type information, automatic generation has to be based on some kind of hand-made declarative information.

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

Easy

<a id="mentor"></a>

#### Mentor

Tomás Guisasola

<a id="links"></a>

#### Links

\[1\] LuaSOAP: http://tomasguisasola.github.io/luasoap/ \[2\] SOAP: http://www.w3.org/TR/soap/ \[3\] WSDL: http://www.w3.org/TR/wsdl

<a id="luasql"></a>

### Add support for prepared statements in LuaSQL.

<a id="briefexplanation"></a>

#### Brief explanation

LuaSQL \[1\] is a generic interface from Lua to a DBMS. It aims at portability over performance, but it allows extensions to suit the particularities of each DBMS.

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

<a id="links"></a>

#### Links

\[1\] LuaSQL: <http://www.keplerproject.org/luasql/>

<a id="luaredis"></a>

### Concurrent Lua scripts execution in Redis

<a id="briefexplanation"></a>

#### Brief explanation:

Redis is a popular open source key-value store that supports scripting using the Lua programming language. Howerer, Redis uses the same Lua interpreter to run all the commands so while the script is running no other client can execute commands. The objective of this project is to support parallel script execution without loosing their atomicity and cluster support.

<a id="expectedresults"></a>

#### Expected results:

A fork of Redis with support for concurrent Lua scripts executions, leveraging the use of more complex and slow scripts.

<a id="knowledgeprerequisite"></a>

#### Knowledge prerequisite:

C, Lua, Redis, pthreads

<a id="skilllevel"></a>

#### Skill level:

Medium

<a id="mentor"></a>

#### Mentor:

Noemi Rodriguez

<a id="lualeak"></a>

### Create a library to help "memory leak" detection in Lua \[1\].

<a id="briefexplanation"></a>

#### Brief explanation

Memory leak in garbage collected languages happens when the program allocates a memory, then finish using it but does not free3 the memory block. In this case, all pointers to this block and the block itself are valid, however the data will never be accessed again by the program.

Lua is a dynamic typed language with garbage collection that as other garbage-collected languages has many reported issues related to memory leak. Your task would be to create a library to help memory leak detection in Lua.

<a id="expectedresults"></a>

#### Expected results

  - A library that helps memory leak detection in Lua.

There is no restriction if the library should: \* use a combination of heap-differencing and fine-grained allocation tracking \* detect when objects exceed their expected lifetimes \* detect when an object becomes stale \* track growing data structures to check whether they are leaking or not.

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

A memory leak detection tool will need to monitor and understand objects behavior and maybe interact with the garbage collector. Since Lua is implemented in ANSI C and this tool will need access to the language internals, C is mandatory.

Understanding garbage collection techniques can be very helpful, mainly the incremental mark-and-sweep collector technique, which Lua implements.

Programming in Lua is not mandatory, however, understanding the language structure will be very important. For example, Lua has different types of objects, but only one data structuring mechanism.

<a id="skilllevel"></a>

#### Skill level

Hard

<a id="mentor"></a>

#### Mentor

Roberto Ierusalimschy \[2\]

<a id="links"></a>

#### Links

\[1\] Lua: <http://lua.org/>

\[2\] Roberto: <http://www.inf.puc-rio.br/~roberto>

<a id="dynserial"></a>

### Develop a binary serialization format with support for dynamically types values and an RPC protocol for dynamically typed invocations based on this format.

<a id="briefexplanation"></a>

#### Brief explanation

Most RMI protocols available today are either focused on inefficient representation formats for typing information [1](http://www.omg.org/spec/CORBA/3.3/Interoperability/PDF) [2](http://hessian.caucho.com) [3](https://developers.google.com/protocol-buffers/), or on invocations where the typing information are predefined and static, therefore are absent on the data sent through the wire [5](http://www.json.org) [4](http://www.w3.org/TR/soap/) [6](http://www.caucho.com/resin-3.0/protocols/burlap.xtp). Few protocols are designed to work efficiently with typed data. Invocations with typed data work well with the RPC model because it allows the identification of deployment problems (mismatch interfaces) and facilitate the dynamic evolution of distributed systems. A protocol for dynamically typed RPC should be based on a efficient serialization format for typed data, that is, information about how the data should be interpreted.

The goal of this project is to design and implement a serialization binary serialization format with the following requirements:

  - Primitive data: numeric formats (integer and floating-point), characters and boolean.

  - Structured data: serialization of usual structured data like records, arrays, maps, tuples, union, etc.

  - Optional typing: serialization of both raw data and data plus typing information.

  - Structurual compatibility: type information should allow to efficiently verify whether two types are compatibile.

  - Opaque data: allow that a special form of raw data (without typing information) can be ignored without compromising the remains of the stream and that can also be passed along by a receiver that did not interpreted it.

  - Semantic information: data types that can extend a standard type with additional semantic information, like a string (sequence of characteres) with an associated charset or a record with an associated class name that provides some behavior over the data on the record.

  - Graphs: data with cyclic references.

<a id="expectedresults"></a>

#### Expected results

  - An specification of a binary serialization format with support for typed data.
  - An implementation of a library for encoding values using this format.

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

  - Basic programming skills (preferably C or Lua).

<a id="skilllevel"></a>

#### Skill level

Hard

<a id="mentor"></a>

#### Mentor

Renato Maia

<a id="links"></a>

#### Links

[1](http://www.omg.org/spec/CORBA/3.3/Interoperability/PDF) GIOP/IIOP (CORBA) <http://www.omg.org/spec/CORBA/3.3/Interoperability/PDF>

[2](http://hessian.caucho.com) Hessian <http://hessian.caucho.com>

[3](https://developers.google.com/protocol-buffers/) Google Protocol Buffers <https://developers.google.com/protocol-buffers/>

[5](http://www.json.org) JSON <http://www.json.org>

[4](http://www.w3.org/TR/soap/) SOAP <http://www.w3.org/TR/soap/>

[6](http://www.caucho.com/resin-3.0/protocols/burlap.xtp) Burlap <http://www.caucho.com/resin-3.0/protocols/burlap.xtp>

<a id="loski"></a>

### Develop a library for Lua [1](https://github.com/renatomaia/loski) that allows Lua programs to access features provided by the platform's underlying operating system (OS) kernel, such as process control, network access, file system, event notification, etc.

<a id="briefexplanation"></a>

#### Brief explanation

Standard Lua distribution is based mostly on standard ANSI C libraries only. Therefore, many functionalities provided by modern platforms (like process control, file system operations, network communication, kernel event notification, etc.) are only available through third-party libraries that are developed independently and might not integrate.

The project has three main goals:

  - Design a simple and easy API that allows for different implementations over various platforms (POSIX, Linux, MacOSX, Windows, etc.) yet allowing use of a basic set of features that are provided by most popular plataforms.

  - Design an internal architecture that facilitate the replacement of the actual implementation of the features provided by the library (create process, use sockets, inspect file systems, etc). This is important to make porting the library to other platoforms easier.

  - Provide a basic/standard implemenation of features provided by the library based on the codebase of existing Lua libraries that already export features of the underlying platform like LuaSocket[2](http://w3.impa.br/~diego/software/luasocket/), LuaFileSystem[3](http://keplerproject.github.io/luafilesystem/) and others.

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

<a id="links"></a>

#### Links

[1](https://github.com/renatomaia/loski) Prototype at <https://github.com/renatomaia/loski>

[2](http://w3.impa.br/~diego/software/luasocket/) LuaSocket <http://w3.impa.br/~diego/software/luasocket/>

[3](http://keplerproject.github.io/luafilesystem/) LuaFileSystem <http://keplerproject.github.io/luafilesystem/>

<a id="vlc"></a>

### Multi-CPU usage in VLC

<a id="briefexplanation"></a>

#### Brief explanation:

VLC is a free and open source cross-platform multimedia player and framework that plays most multimedia files as well as DVD, Audio CD, VCD, and various streaming protocols. Lua scripts can be added to VLC for tasks such as playlist construction and service discovery. Such tasks may involve a lot of parsing and communication and could benefit from using multiple CPUs when available. The purpose of this project is to include support for multi-CPU usage in VLC, using luaproc, a library that allows programmers to create multiple independent execution flows of Lua code that can run inparallel, communicating only via message-passing.

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

Noemi Rodriguez

<a id="wireshark"></a>

### Multi-CPU usage in wireshark

<a id="briefexplanation"></a>

#### Brief explanation:

The wireshark network protocol analyser \[1\] allows programmers to use Lua to write dissectors, post-dissectors and taps. Dissectors are protocol analysers, while post-dissectors are executed after all others dissectors, and taps are used to collect information after packet dissection. Protocol dissection can involve time constraints, and it would be nice to benefit from multi-CPU processing power in dissector script. The purpose of this project is to include support for multi-CPU usage in wireshark, using luaproc, a library that allows programmers to create multiple independent execution flows of Lua code that can run inparallel, communicating only via message-passing.

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

Noemi Rodriguez

\[1\] http://www.wireshark.org/

<a id="gameduino"></a>

### Porting Gameduino demos to the programming language Céu.

<a id="briefexplanation"></a>

#### Brief explanation

Gameduino \[1\] is an Arduino-based \[2\] open-source hardware platform for games. It is composed of a touchscreen, an embedded GPU, headphone jack, accelerometer, and a microSD slot. The associated software package contains dozen of demos and four complete games (e.g. Space Invarders and Chess) developed in C. Gameduino was a successful Kickstarter project in 2013 \[3\].

Céu \[4\] is a concurrent programming language that offers a safer and higher-level alternative to C. It targets embedded systems such as Arduino. Céu was designed in the Lablua.

<a id="expectedresults"></a>

#### Expected results

  - Port the Gameduino demos from C to Céu.
  - Compare the codebases in C and Céu with respect to quantitative measures such as lines of code, memory consumption and CPU usage.

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

C and Céu:

  - C is mandatory.
  - Céu is a C-based language and can be learned during the project.

<a id="skilllevel"></a>

#### Skill level

Medium

<a id="mentor"></a>

#### Mentor

Francisco Sant'Anna is a post-doc at Lablua and the designer of Céu.

<a id="links"></a>

#### Links

\[1\] Gameduino: <http://excamera.com/sphinx/gameduino2/>

\[2\] Arduino: <http://arduino.cc/>

\[3\] Kickstarter: <https://www.kickstarter.com/projects/2084212109/gameduino-2-this-time-its-personal>

\[4\] Céu: <http://www.ceu-lang.org/>

<a id="luaproc"></a>

### Send/Receive support for main script in the luaproc library

<a id="briefexplanation"></a>

#### Brief explanation

luaproc is a concurrent programming library for the Lua programming language. It allows programmers to create multiple independent execution flows of Lua code, called Lua processes, that can run in parallel with underlying multithreading support. Lua processes can only communicate through message passing. However, the main Lua script from where the library is loaded and initial Lua processes are created, cannot send or receive messages. The purpose of this project is to implement the required changes in luaproc to allow the main Lua script to communite with spawned Lua processes through message passing.

<a id="expectedresults"></a>

#### Expected results

An updated version of the luaproc library where it is possible for the main Lua script to send messages to and to receive messages from spawned Lua processes.

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

C, Lua, pthreads

<a id="skilllevel"></a>

#### Skill level

Medium

<a id="mentor"></a>

#### Mentor

Noemi Rodriguez

<a id="threadsafelua"></a>

### Thread-safe Lua

<a id="briefexplanation"></a>

#### Brief explanation

The Lua programming language includes cooperative multithreading support through coroutines. However, this form of multithreading is not designed to exploit parallelism. The Lua C API allows programmers to create independent Lua states, which store interepreter-related data, that can be used to execute code as if it was executed from within a coroutine. This has been used by libraries, such as luaproc and Lua Lanes, to implement concurrency models based on system threads that can exploit parallelism. The Lua C API also allows programmers to create new (userland) threads within the same Lua state. These threads share data with the parent state and thus can potentially lead to race conditions if executed in parallel. The purpose of this project is to implement a fork of the standard Lua interpreter that is internally thread-safe, i.e., that allows multiple (userland) threads within the same Lua state to execute in parallel without internal interpreter data races.

<a id="expectedresults"></a>

#### Expected results

A fork implementation of the latest version of the interpreter of the Lua programming language that is internally thread-safe.

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

C, Lua, pthreads

<a id="skilllevel"></a>

#### Skill level

Hard

<a id="mentor"></a>

#### Mentor

Noemi Rodriguez

<a id="luashare"></a>

### luashare - data sharing among parallel execution flows of Lua code

<a id="briefexplanation"></a>

#### Brief explanation

luaproc is a concurrent programming library for the Lua programming language. It allows programmers to create multiple independent execution flows of Lua code, called Lua processes, that can run in parallel with underlying multithreading support. Lua processes can only communicate through message passing. However, messages cannot hold tables, only basic data types like numbers, strings and booleans. To send tables, programmers must serialize data on the sender and de-serialize it on the receiver. Apart from the implementation overhead, there can also be a performance cost to serialize and de-serialize data. Therefore, it would be useful to allow table references to be sent in messages, so instead of copying data, memory would be shared. Assuming the Lua interpreter is thread-safe, the purpose of this project is to implement a variation of the luaproc library where instead of having completely independent Lua processes, data could be shared, in a controlled way, among Lua processes.

<a id="expectedresults"></a>

#### Expected results

new concurrent programming library for the Lua programming language, based on the principles of the luaproc programming library, that would allow for controlled data sharing among parallel execution flows of Lua code.

<a id="knowledgeprerequisites"></a>

#### Knowledge prerequisites

C, Lua, pthreads

<a id="skilllevel"></a>

#### Skill level

Medium

<a id="mentor"></a>

#### Mentor

Noemi Rodriguez
