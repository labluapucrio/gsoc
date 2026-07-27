## Project

Add class-based object-oriented programming to [Typed Lua](https://github.com/andremm/typedlua) [1].

### Brief explanation

Typed Lua is a strict superset of Lua that provides optional
type annotations, and compile-time type checking.
More precisely, Typed Lua is implemented as a programming language
that extends Lua syntax to add optional type annotations.
The compiler uses static types to perform compile-time type checking,
but also allows Lua code to coexist with Typed Lua code, and generate
Lua code that runs in unmodified Lua implementations.

### Expected results

Typed Lua intended use is as an application language, and we view that
policies for organizing a program in modules and writing object-oriented
programs should be part of the language and enforced by its optional type
system. An application language is a programming language that helps
programmers develop applications from scratch until these applications
evolve to complex systems rather than just scripts.
This project aims to add class-based object-oriented programming to
Typed Lua through the definition of classes, interfaces, and modules,
as a way to help Lua programmers better structure their code.

### Knowledge prerequisites

Lua, Object-Oriented Programming, and Type Systems

### Skill level

Hard

### Mentor

[Fabio Mascarenhas](http://www.dcc.ufrj.br/~fabiom/) [2]

### Links

[1] Typed Lua: <https://github.com/andremm/typedlua>

[2] Fabio Mascarenhas: <http://www.dcc.ufrj.br/~fabiom/>

