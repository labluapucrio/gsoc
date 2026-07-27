## Project

Develop a library for Lua [1](https://github.com/renatomaia/loski) that allows Lua programs to access features provided by the platform's underlying operating system (OS) kernel, such as process control, network access, file system, event notification, etc.

### Brief explanation

Standard Lua distribution is based mostly on standard ANSI C libraries only. Therefore, many functionalities provided by modern platforms (like process control, file system operations, network communication, kernel event notification, etc.) are only available through third-party libraries that are developed independently and might not integrate.

The project has three main goals:

* Design a simple and easy API that allows for different implementations over various platforms (POSIX, Linux, MacOSX, Windows, etc.) yet allowing use of a basic set of features that are provided by most popular plataforms.

* Design an internal architecture that facilitate the replacement of the actual implementation of the features provided by the library (create process, use sockets, inspect file systems, etc). This is important to make porting the library to other platoforms easier.

* Provide a basic/standard implemenation of features provided by the library based on the codebase of existing Lua libraries that already export features of the underlying platform like LuaSocket[2](http://w3.impa.br/~diego/software/luasocket/), LuaFileSystem[3](http://keplerproject.github.io/luafilesystem/) and others.

### Expected results

A set of Lua libraries implemented at least in one major operating system platform. The library shall provide support for:

* Creation and manipulation of processes, and possibly inter-process comunication mechanisms, such as pipes.
* Creation and maniputation of sockets (TCP and UDP).
* Inspection of the local file system, possibly including file attributes and permissions.
* Notification of kernel events like process termination, socket data availability, file modification, etc.

The implementation shall also be flexible enough to facilitate the portability for other platforms.

### Knowledge prerequisites

* Programming in C.
* Familiarity with concepts of the Lua language.
* Programming with the system API of some popular platform, such as Linux, FreeBSD, Windows, etc.

### Skill level

Hard

### Mentor

Renato Maia

### Links

[1](https://github.com/renatomaia/loski) Prototype at <https://github.com/renatomaia/loski>

[2](http://w3.impa.br/~diego/software/luasocket/) LuaSocket <http://w3.impa.br/~diego/software/luasocket/>

[3](http://keplerproject.github.io/luafilesystem/) LuaFileSystem <http://keplerproject.github.io/luafilesystem/>
