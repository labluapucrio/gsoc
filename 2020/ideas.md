<!-- Archived from http://www.lua.inf.puc-rio.br/gsoc/ideas2020.html; this is the ideas list as published for GSoC 2020. -->

## Ideas List - Google Summer of Code 2020

  - [A Parser Generator with Semi-Automatic Error Recovery based on LPeg(Label)](#lpeg)
  - [Lua Hook on kTLS](#ktls)
  - [Lazy Configuration validator for LuaFormatter](#luaformatter)
  - [Modules in Pallene](#pallene_modules)
  - [Extending the support of Céu in the Céu-Arduino IDE](#ceu)

  

-----

<a id="lpeg"></a>

### A Parser Generator with Semi-Automatic Error Recovery based on LPeg(Label)

#### Brief explanation

[Parsing Expression Grammars](http://bford.info/pub/lang/peg) (PEGs) are an expressive formalism for the design and implementation of top-down parsers with local backtracking. [LPeg](http://www.inf.puc-rio.br/~roberto/lpeg/) is a tool that provides an implementation of PEGs for Lua, while [LPegLabel](https://github.com/sqmedeiros/lpeglabel/) is an extension of LPeg with some facilities for error reporting and recovery.

The goal of this project is to build a parser generator on top of the new version of LPegLabel. This new tool should make easier the description of a parser for a programming language and should also implement a [conservative algorithm](https://arxiv.org/abs/1905.02145) to automatically annotate a PEG with labels, in order to provide an automatic error recovery mechanism.

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

<a id="ktls"></a>

### Lua Hook on kTLS

#### Brief explanation

[Lunatik](https://github.com/luainkernel/lunatik) is a kernel-level Lua interpreter version for scripting the Linux kernel. For example, it allows users to filter packets using Lua scripts. [kTLS](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/Documentation/networking/tls.rst?h=v5.5) is a new socket type provided by Linux that transparently handles the encryption and decryption of TLS messages.

[ULP (Upper Layer Protocol)](https://elixir.bootlin.com/linux/latest/source/net/ipv4/tcp_ulp.c) is a new feature merged recently in the Linux kernel which allows user-space programs to attach [L7 functionalities](https://en.wikipedia.org/wiki/OSI_model#Layer_7:_Application_Layer) to the in-kernel socket structure. kTLS is implemented via ULP.

The purpose of this project is to implement a kernel level Lua hook inside the kTLS infrastructure. This way we could use Lua scripts to inspect the contents of the HTTP messages transparently inside the kernel.

#### Expected results

  - Lua hook inside kTLS
  - A reference application
  - Documentation and benchmarks

#### Prerequisites

C, Lua, make, OS, networking (and some courage ;))

#### Skill level

Advanced

#### Mentor

[Pedro Tammela](mailto:pctammela@gmail.com)

  

-----

<a id="luaformatter"></a>

### Lazy Configuration validator for LuaFormatter

#### Brief explanation

[LuaFormatter](https://github.com/Koihik/LuaFormatter) is a code formatter for Lua inspired by LLVM's ['clang-format'](https://clang.llvm.org/docs/ClangFormat.html). It helps projects keep a even code style in Lua scripts while being easy to integrate with many different code editors.

The purpose of this project is to implement a lazy configuration validator. Right now, LuaFormatter doesn't check if the configuration values makes sense before using it. For example, a clueless user could use a negative value in a field where the range expected is \[0, ∞).

We expect the validator to detect this kind of error and report to the user in a nice, helpful way.

#### Expected results

  - Lazy configurator validator
  - Unit tests
  - Documentation

#### Prerequisites

C++/C, Git

#### Skill level

Easy

#### Mentors

[Pedro Tammela](mailto:pctammela@gmail.com), [Shaobang Wen](mailto:koihik@hotmail.com)

  

-----

<a id="pallene_modules"></a>

### Modules in Pallene

[Pallene](https://github.com/pallene-lang/pallene) is a typed companion language for Lua. Its syntax is similar to Lua, but with added type annotations. These types allow the Pallene compiler to generate code that is much more efficient than the Lua interpreter. Pallene is ideally suited for writing performant extension modules for Lua.

Pallene is evolving at a rapid pace, and there are still many features missing from the language. One of them module imports and exports. Currently, Pallene modules can be used by Lua, but the Pallene module cannot directly require other Pallene or Lua modules. Implementing this feature would allow programmers to write larger programs in Pallene.

In this project, you will have to get inside the guts of the Pallene compiler. The compiler itself is written in Lua and C, and it generates C code, so knowing both languages is a prerequisite.

To add support for separately-compiled modules, we will need to develop a file format for describing the interface of a Pallene module, describing all it's exported types and functions. This interface file should be able to describe the interface of Pallene modules, and also of Lua modules used by Pallene. Then, we will need to extend the Pallene compiler so that it can generate these interface files after compiling a module, and also so that it can use these interface files when one Pallene module requires a Lua or Pallene module. We also expect that some changes will be necessary in the parser, type checker, and code generator, to support using types and functions declared in a separate module.

This is a hard project, so we are expecting students that are looking for a challenge. Nevertheless, the student will have the full support of the mentors. If you are interested, please contact the mentors by email to get started with Pallene development.

#### Prerequisites

  - Lua programming language
  - C programming language
  - C API for Lua
  - Compilers

#### Skill Level

Hard

#### Mentors

[Hugo Gualandi](mailto:hgualandi@inf.puc-rio.br), [Gabriel Ligneul](mailto:gqligneul@gmail.com)

  

-----

<a id="ceu"></a>

### Extending the support of Céu in the Céu-Arduino IDE

#### Background

Céu is a reactive language that aims to offer a higher-level and safer alternative to C:

  - Home Page: <http://www.ceu-lang.org>
  - Source code: <https://github.com/ceu-lang/ceu>

Céu-Arduino IDE is a modified version of the Arduino IDE that supports developing apps in Céu with the Céu-Arduino binding. Currently the IDE can open, compile and upload Arduino sketches written in the Céu programming language. It also includes some features such as syntax highlighting for Céu constructs, Céu examples for Arduino and Céu-Arduino libraries.

#### The project

The goal of this project is to extend the support of Céu in the IDE by adding more features such as:

  - Adding support for other Céu bindings like pico-céu, this will include adding a GUI tool for viewing the program output.
  - Auto formatting, auto indentation and code folding for Céu code files.
  - Adding a GUI debugger for Céu that can keep track of which trails are active and which are idle.

A plugin architecture could be implemented for the Arduino IDE first, so that these features and future ones could be added in the form of plugins instead of modifying the IDE.

#### Tools

  - Céu programming language
  - Céu-Arduino IDE.
  - Ant for building the IDE from source.

#### Prerequisites

The student should know Java or a similar language (e.g. C\#). We ask applicants to complete the following activities before the application period:

1.  Install Céu, Céu-Arduino and pico-Céu and compile and test some of the existing examples.
2.  Install Apache Ant and download the Céu-Arduino IDE repository from github.
3.  Add a dummy menu in the menu bar and a dummy button in the toolbar.
4.  Fork our Céu-Arduino IDE repository on github and commit your edits.
5.  Build the edited IDE using Ant and add the build as a release to your forked repository.

#### Skill level

Hard

#### Mentors

[Francisco Sant'Anna](mailto:francisco.santanna@gmail.com)
