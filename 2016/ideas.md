<!-- Archived from http://www.lua.inf.puc-rio.br/gsoc/ideas2016.html; this is the ideas list as published for GSoC 2016. -->

## Ideas List - Google Summer of Code 2016

  - [Update elasticsearch-lua](#elasticsearch_update)
  - [Elasticsearch and Sailor](#elasticsearch_sailor)
  - [Improve elasticsearch-lua tests and build](#elasticsearch_tests)
  - [Next Generation of the LuaRocks test suite](#luarocks)
  - [Enhancements to LibScript, a cross-language scripting library](#libscript)
  - [Implement core Typed Lua in Haskell](#typed)
  - [Extending the online tutorial of Céu with Emscripten and SDL](#ceu)
  - [Develop I/O API for NetBSD Kernel Lua](#netbsd)
  - [Adapt CGILua SAPI launcher to explore all WSAPI features](#cgilua)
  - [Add support for prepared statements in LuaSQL](#luasql)
  - [Improving the Quality of Error Messages in PEG Parsers](#peg)
  - [Assembler and Disassembler for Lua 5.3](#lad)
  - [Add class-based object-oriented programming to Typed Lua](#typedlua)
  - [Improve the HTTPS module of LuaSec](#luasec)

  

-----

<a id="elasticsearch_update"></a>

### Update elasticsearch-lua

#### Brief explanation

[Elasticsearch](https://www.elastic.co/products/elasticsearch) is a distributed and scalable search engine. It is written in Java and, besides the transport protocol (Java to Java), it offers a very complete REST API accessed through [JSON](http://json.org/). [elasticsearch-lua](https://github.com/DhavalKapil/elasticsearch-lua/) is a Lua library that allows Lua applications to easily comunicate with Elasticsearch clusters.

Currently, elasticsearch-lua is built on top of Elasticsearch 1.7 but does not implement all possible Elasticsearch features. Moreover, Elasticsearch is already in version 2.2 and many new features are available.

This project aims to implement the missing features from 1.7 and also add the new features from Elasticsearch 2.2.

#### Expected results

An updated Lua client to access the Elasticsearch REST API compatible with the latest version (currently 2.2).

#### Knowledge prerequisites

  - Lua - medium
  - JSON - medium
  - HTTP - medium
  - Elasticsearch - medium

#### Skill level

Medium

#### Mentor

[Pablo Musa](http://www.inf.puc-rio.br/~pmusa/)

  

-----

<a id="elasticsearch_sailor"></a>

### Elasticsearch and Sailor

#### Brief explanation

[Elasticsearch](https://www.elastic.co/products/elasticsearch) is a distributed and scalable search engine. It is written in Java and, besides the transport protocol (Java to Java), it offers a very complete REST API accessed through [JSON](http://json.org/). [elasticsearch-lua](https://github.com/DhavalKapil/elasticsearch-lua/) is a Lua library that allows Lua applications to easily communicate with Elasticsearch clusters.

[Sailor](http://sailorproject.org/) is a web framework in the Lua programming language. Like Lua, it is open sourced under the MIT License, which is extremely permissive. Sailor applications are structured in a model-view-controller (MVC) architecture.

This project aims the development of a search module that integrates elasticsearch-lua into Sailor.

#### Expected results

A search functionality that is easy to use and integrate to a website using Sailor. Internally, a new form.search method in the form module that exposes a search text input and a search model similar to the current database one.

#### Knowledge prerequisites

  - Lua - medium
  - Sailor - not required
  - Elasticsearch - basic
  - Web Development - medium

#### Skill level

Easy/Medium

#### Mentor

[Pablo Musa](http://www.inf.puc-rio.br/~pmusa/)

  

-----

<a id="elasticsearch_tests"></a>

### Improve elasticsearch-lua tests and build

#### Brief explanation

[Elasticsearch](https://www.elastic.co/products/elasticsearch) is a distributed and scalable search engine. It is written in Java and, besides the transport protocol (Java to Java), it offers a very complete REST API accessed through [JSON](http://json.org/). [elasticsearch-lua](https://github.com/DhavalKapil/elasticsearch-lua/) is a Lua library that allows Lua applications to easily comunicate with Elasticsearch clusters.

Currently, elasticsearch-lua has small build automation, only 19 library tests and no code coverage.

This project aims to implement more robust build automation.

#### Expected results

An integration for code coverage, automated build tests (already working) and a large set of tests that cover most part of the code.

#### Knowledge prerequisites

  - Lua - basic
  - Elasticsearch - basic/medium
  - Continous Integration - basic

#### Skill level

Easy

#### Mentor

[Pablo Musa](http://www.inf.puc-rio.br/~pmusa/)

  

-----

<a id="libscript"></a>

### Enhancements to LibScript, a cross-language scripting library

#### Brief explanation

[LibScript](http://hishamhm.github.io/libscript) is a library for cross-language scripting: it allows code written in one scripting language to call function written in a different language, and allows C programs to support various scripting languages via a single interface. LibScript currently supports Python, Ruby, Lua and Perl, and it only supports passing simple values as arguments (strings, numbers, booleans).

This project has two goals:

  - supporting a wider set of functions - support passing and receiving structured data types such as lists and dictionaries. An idea of how to do this to pass data by-copy, using JSON as an interchange format between languages.
  - supporting more languages - two languages that would be useful to support would be JavaScript (writing a LibScript plugin that links the V8 virtual machine), and [R](https://www.r-project.org) (giving many languages access to the vast array of statistical libraries available in [CRAN](http://cran.us.r-project.org/)).

#### Expected results

  - Enhancements to the existing LibScript plugins, supporting structured data types.
  - New plugins supporting additional languages

#### Knowledge prerequisites

  - C programming - must be comfortable with C code, working with C libraries and learning their APIs
  - Unix shell and tools - Makefile, shell scripting (not being scared of [Autotools](http://www.sourceware.org/autobook/) is a bonus -- if scared, we'll work on it\!)
  - Previous experience in *some* scripting language - any of Python, Ruby, Lua, Perl, JavaScript, etc.
  - Experience with, or willingness to quickly learn Git and the Github workflow
  - Previous experience embedding any scripting language in a C application is a bonus

#### Skill level

Medium/advanced

#### Mentor

[Hisham Muhammad](http://hisham.hm/)

  

-----

<a id="luarocks"></a>

### Next Generation of the LuaRocks test suite

#### Brief explanation

[LuaRocks](http://luarocks.org) is the package manager for Lua modules. It has a test suite with about 80% coverage. However, the test suite is implemented as a big shell script that only does black-box testing: it calls `luarocks` as an external application. Further, it only checks for success and failure of the process, and not if it executed the expected actions, and it runs only on Linux.

The idea of this project is to port the test suite to Lua, using [Busted](https://github.com/Olivine-Labs/busted). This will allow us to extend the test suite by writing smarter tests that check its behavior, write white-box tests of the internals, and also port the test suite to other platforms.

#### Expected results

  - A new test suite, written in Lua.
  - Improved code coverage, by adding white-box tests for parts that are hard-to reach via black-box testing.
  - Initial results running the test suite on Windows (even if we can't run all tests at first).
  - Integrated code coverage results, merging the Linux and Windows runs.

#### Knowledge prerequisites

  - Lua
  - Unix shell and tools - basic shell scripting in order to understand the [current test suite](https://github.com/keplerproject/luarocks/blob/master/test/testing.sh)
  - Experience with, or willingness to quickly learn Git and the Github workflow

#### Skill level

Easy/Medium

#### Mentor

[Hisham Muhammad](http://hisham.hm/)

  

-----

<a id="typed"></a>

### Implement core Typed Lua in Haskell

#### Brief explanation

[Typed Lua](https://github.com/andremm/typedlua) is an optional type system for Lua, and its main goal is to provide static type checking for Lua. To do that, Typed Lua extends the syntax of Lua 5.3 to introduce optional type annotations, and performs local type inference to detect more precise types for unannotated expressions.

The aim of this project is to implement core Typed Lua in Haskell, as a tool to test new features and reason about new typing rules for Typed Lua. Core Typed Lua limits control flow to if and while statements; it has explicit type annotations, explicit scope for variables, explicit method declarations, and explicit method calls.

#### Expected results

  - A type checker written in Haskell that analyses code written in core Typed Lua.

#### Knowledge prerequisites

  - Lua (for understanding regular Typed Lua implementation).
  - Haskell (for implementing the project).
  - Type Systems (for understanding the typing rules).
  - Git (the project repository should be in github).

#### Skill level

Advanced

#### Mentor

[André Murbach Maidl](mailto:amaidl@inf.puc-rio.br)

  

-----

<a id="ceu"></a>

### Extending the online tutorial of Céu with Emscripten and SDL

#### Brief explanation

[Céu](http://ceu-lang.org/) is a programming language that targets system-level development of reactive systems. The language is under development at the LabLua since 2011. For a little introduction about Céu, please watch the video in [our front page](http://ceu-lang.org/). Céu appeared in [Future Programming](http://www.future-programming.org/2014/program.html) and [Curry-On](http://curry-on.org/2015/sessions/structured-synchronous-programming.html) workshops.

Currently, the online tutorial of Céu executes a simulation at the server side:

<http://ceu-lang.org/try.php>

The tutorial works as follows:

1.  User reads about a new concept (\`top/left\` of the page).
2.  User reads an accompanying example (\`top/right\`) with an input (\`bottom/right\`).
3.  User clicks "Run" (\`top/right\`)
    1.  Code is sent to the server.
    2.  Server compiles and executes the code with the provided input.
    3.  User gets an output (\`bottom/left\`).
4.  User changes the code and input to experiment with it (going to step 3).
5.  User advances in the tutorial.

The server-side approach does not provide a reactive and real-time experience, which are the ultimate objectives of the language. We want the online tutorial to offer a more interactive experience for learners of Céu. The client-side tutorial would work as follows:

1.  User reads about a new concept (\`top/left\` of the page).
2.  User sees an example (\`top/right\`) ~~with an input (\`bottom/right\`)~~.
3.  User clicks "Run" (\`top/right\`):
    1.  Code is sent to the server.
    2.  Server compiles the code ~~with the provided input~~ to Javascript and returns it to the client.
    3.  User ~~gets an output (\`bottom/left\`)~~ interacts with the program in real time.
4.  User changes the code ~~and input~~ to experiment with it (going to step 3).
5.  User advances in the tutorial.

#### Tools

[SDL](http://libsdl.org/) is a C-based and cross-platform development library that provides access to audio, keyboard, mouse, joystick, and graphics hardware. Given that Céu interacts well with C, combining Céu and SDL is a viable option for building a visually-appealing interactive tutorial. [Emscripten](https://github.com/kripken/emscripten/) is an LLVM-to-JavaScript compiler. SDL has already [been ported to Emscripten](https://github.com/kripken/emscripten/issues/2404).

Putting it all together, we can build an interactive tutorial for Céu that runs in the browser at the client side.

The bulk of the project is to implement this synergy between C, Céu, SDL, and Emscripten. However, the project also involves other tools: Linux, Git, HTML and PHP.

#### Expected results

  - A working interactive online tutorial for Céu.

As an ultimate goal, we would like to build an incremental tutorial based on [this video](https://vimeo.com/110512582).

#### Prerequisites

We expect the applicants to know **C** well and to develop minimum familiarity with the important tools before the project kicks off.

For this reason, we will ask the applicants to perform two activities \*before\* the application period:

1.  Create a repository on \*Github\* and write a simple "Hello World" page using Emscripten and SDL.
2.  Install Céu and compile some existing SDL examples (without Emscripten).

Both activities should be simple, i.e., nothing more than following tutorials on the web.

#### How to apply

  - [Get in touch](https://gitter.im/fsantanna/ceu-gsoc-2016)
  - Follow the official GSoC instructions.
  - Follow the LabLua instructions.

#### Skill level

Medium

#### Mentor

[Francisco Sant'Anna](http://www.ceu-lang.org/chico)

  

-----

<a id="netbsd"></a>

### Develop I/O API for NetBSD Kernel Lua

#### Brief explanation

[The NetBSD Operating System](http://www.netbsd.org) has a kernel-level Lua interpreter version for [scripting its kernel](http://netbsd.org/~lneto/dls14.pdf). For example, it allows users to [filter packets using Lua scripts](http://netbsd.org/~lneto/eurobsdcon14.pdf).

The main difference between kernel Lua and regular user-level Lua is that kernel Lua doesn't have support for standard libraries that depend on operating system (e.g., io and os) and for floating-point numbers. The purpose of this project is to develop kernel Lua libraries to provide I/O functionality to kernel scripts. This API should provide access both for file system and network. It should be implemented as [NetBSD loadable kernel modules](http://www.home.unix-ag.org/bmeurer/NetBSD/howto-lkm.html) binding the kernel internal implementation for files and sockets user-level API.

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

<a id="cgilua"></a>

### Adapt CGILua SAPI launcher to explore all WSAPI features.

#### Brief explanation

[CGILua](http://keplerproject.github.io/cgilua/) is a tool for creating dynamic Web pages and manipulating input data from Web forms. One of advantages of CGILua is its abstraction of the underlying Web server. CGILua can be used with a variety of Web servers and, for each server, with different launchers. A launcher is responsible for the interaction of CGILua and the Web server, for example using ISAPI on IIS or mod\_lua on Apache. The reference implementation of CGILua launchers is Kepler.

[WSAPI](http://keplerproject.github.io/wsapi/) is an API that abstracts the web server from Lua web applications. WSAPI provides a set of helper libraries that help with request processing and output buffering.

Actually CGILua has an implementation of an abstract underlying server which is almost the same of WSAPI itself. This project proposes a reimplementation of this layer (called SAPI) to explore WSAPI fully. This should improve the performance and simplify maintenance.

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

<a id="luasql"></a>

### Add support for prepared statements in LuaSQL

#### Brief explanation

[LuaSQL](http://www.keplerproject.github.io/luasql/) is a generic interface from Lua to a DBMS. It aims at portability over performance, but it allows extensions to suit the particularities of each DBMS.

The inclusion of support for prepared statements in LuaSQL has been discussed thoroughly some time ago, but since each DBMS offers very different APIs there is no standard that could be defined to assure portability between them. Anyway the demand persists.

This project proposes the addition of a minimal API that would allow each driver to implement prepared statements according to its DBMS restrictions.

#### Expected results

  - Adapt the API to each LuaSQL driver according to its particularities
  - Implement the new functions to each driver
  - Test and document everything

#### Knowledge prerequisites

C, Lua and C API for Lua:

  - C is mandatory.
  - Knowledge of the C API for Lua is mandatory, although it is not too difficult to be learned during the project.
  - Basic programming in Lua is very helpful, but not mandatory, since the examples and test-cases are very simple.

#### Skill level

Hard

#### Mentor

Tomás Guisasola

  

-----

<a id="peg"></a>

### Improving the Quality of Error Messages in PEG Parsers

#### Brief explanation

[Parsing Expression Grammars](http://bford.info/pub/lang/peg) (PEGs) are an expressive formalism for designing and implementing top-down parsers with local backtracking. An issue that users of PEG-based parsers face is poor reporting of syntax errors on the part of PEG-based parsers. [Labeled failures](http://www.inf.puc-rio.br/~roberto/docs/sblp2013-1.pdf) are an extension to PEGs that aims to address this issue by annotating a PEG with labels corresponding to syntax errors, improving the quality of error messages generated by a PEG-based parser.

[LPegLabel](https://github.com/sqmedeiros/lpeglabel/) is an extension of the [LPeg](http://www.inf.puc-rio.br/~roberto/lpeg/) tool that provides an implementation of PEGs with labeled failures. Labels can be used to signal different kinds of errors and to specify which alternative in a labeled ordered choice should handle a given label.

The goal of this project is to rewrite the parsers of some Lua libraries, such as the module *re* from LPeg and *lua-parser*, by using LPegLabel. After this rewriting we should get parsers with better error messages.

#### Tools

  - [LPegLabel](https://github.com/sqmedeiros/lpeglabel/)
  - [LPeg](http://www.inf.puc-rio.br/~roberto/lpeg/)
  - Lua libraries whose parsers will be rewritten

#### Expected results

  - The rewriting of at least 3 parsers by using LPegLabel
  - A proper documentation

A marginal result would be the improvement of the LPegLabel tool based on the difficulties found during the project.

#### Prerequisites

We expect the applicants to know **parsing** well and to develop familiarity with LPeg and LPegLabel before the project starts.

For this reason, we may ask the applicants to perform some activities **before** the application period.

#### How to apply

  - Get in touch.
  - Follow the official GSoC instructions.
  - Follow the LabLua instructions.

#### Skill level

Medium

#### Mentor

[Sérgio Medeiros](https://sites.google.com/site/sqmedeiros/)

  

-----

<a id="lad"></a>

### Assembler and Disassembler for Lua 5.3

#### Brief explanation

Lua is a dynamically typed programming language that runs by interpreting bytecode for a register-based machine. More precisely, Lua programs are interpreted indirectly from source code, that is, they are compiled to bytecode and then executed by the Lua Virtual Machine. This process is done during code execution and it is transparent to final users.

The aim of this project is to create a disassembler and an assembler for Lua 5.3. The disassembler should generate assembly code from either Lua code or bytecode, while the the assembler ought to generate Lua bytecode from assembly code. The assembly syntax should be expressive enough to encode all the instructions that are available at Lua VM.

#### Expected results

  - A disassembler script that converts Lua code/bytecode into assembly instructions.
  - An assembler script that converts assembly instructions into executable Lua bytecode.

#### Knowledge prerequisites

  - Lua (the project should be written in Lua).
  - C (it is important to read the implementation of Lua VM).
  - Git (the project repository should be in github).
  - LPeg is a plus (the assembler parser can be written with LPeg).

#### Skill level

Easy

#### Mentor

[André Murbach Maidl](mailto:amaidl@inf.puc-rio.br)

  

-----

<a id="typedlua"></a>

### Add class-based object-oriented programming to [Typed Lua](https://github.com/andremm/typedlua)

#### Brief explanation

Typed Lua is a strict superset of Lua that provides optional type annotations, and compile-time type checking. More precisely, Typed Lua is implemented as a programming language that extends Lua syntax to add optional type annotations. The compiler uses static types to perform compile-time type checking, but also allows Lua code to coexist with Typed Lua code, and generate Lua code that runs in unmodified Lua implementations.

#### Expected results

Typed Lua intended use is as an application language, and we view that policies for organizing a program in modules and writing object-oriented programs should be part of the language and enforced by its optional type system. An application language is a programming language that helps programmers develop applications from scratch until these applications evolve to complex systems rather than just scripts. This project aims to add class-based object-oriented programming to Typed Lua through the definition of classes and interfaces, as a way to help Lua programmers better structure their code. The backend code generator should be a plugin, so the programmers can choose which OO style or library they want to use.

#### Knowledge prerequisites

Lua, Object-Oriented Programming, and Type Systems

#### Skill level

Hard

#### Mentor

[Fabio Mascarenhas](http://www.dcc.ufrj.br/~fabiom/)

  

-----

<a id="luasec"></a>

### Improve the HTTPS module of LuaSec

#### Brief explanation

[LuaSec](https://github.com/brunoos/luasec/wiki)'s HTTPS module was built on top of [LuaSocket](http://w3.impa.br/~diego/software/luasocket/)'s HTTP and presents some problems due to limited integration.

The aim of this project is to improve HTTPS module, fixing the issues and adding some new features.

#### Expected results

  - Turn the module more self-contained, fixing the dependency problem.
  - Add new features: proxy, SNI (Server Name Indication), etc.
  - Support to HTTP/2 is a plus.

#### Knowledge prerequisites

  - C, Lua, Git, HTTP protocol.

#### Skill level

Easy / Medium

#### Mentor

[Bruno Silvestre](mailto:brunoos@inf.ufg.br)
