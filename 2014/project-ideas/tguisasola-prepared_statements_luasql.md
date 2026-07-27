## Project

Add support for prepared statements in LuaSQL.

### Brief explanation

LuaSQL [1] is a generic interface from Lua to a DBMS.
It aims at portability over performance, but it allows extensions to
suit the particularities of each DBMS.

The inclusion of support for prepared statements in LuaSQL has been
discussed thoroughly some time ago, but since each DBMS offers very
different APIs there is no standard that could be defined to assure
portability between them.
Anyway the demand persists.

This project proposes the addition of a minimal API that would allow
each driver to implement prepared statements according to its DBMS
restrictions.

### Expected results

* Adapt the API to each LuaSQL driver according to its particularities
* Implement the new functions to each driver
* Test and document everything

### Knowledge prerequisites

C, Lua and C API for Lua:

* C is mandatory.
* Knowledge of the C API for Lua is mandatory, although it is not too
   difficult to be learned during the project.
* Basic programming in Lua is very helpful, but not mandatory, since
   the examples and test-cases are very simple.

### Skill level

Hard

### Mentor

Tomás Guisasola

### Links

[1] LuaSQL:   <http://www.keplerproject.org/luasql/>

