## Project

Adapt CGILua SAPI launcher to explore all WSAPI features.

### Brief explanation

CGILua [1] is a tool for creating dynamic Web pages and manipulating input
data from Web forms.  One of advantages of CGILua is its abstraction
of the underlying Web server. CGILua can be used with a variety of Web
servers and, for each server, with different launchers. A launcher is
responsible for the interaction of CGILua and the Web server, for example
using ISAPI on IIS or mod_lua on Apache. The reference implementation
of CGILua launchers is Kepler.

WSAPI [2] is an API that abstracts the web server from Lua web
applications. WSAPI provides a set of helper libraries that help with
request processing and output buffering.

Actually CGILua has an implementation of an abstract underlying server
which is almost the same of WSAPI itself. This project proposes a
reimplementation of this layer (called SAPI) to explore WSAPI fully. This
should improve the performance and simpify maintenance.

### Expected results

* Rewrite CGILua library to dispense SAPI module and use WSAPI directly.

### Knowledge prerequisites

Advanced Lua programming is mandatory, since both tools (CGILua and WSAPI)
are not naive software. A good understanding of the Lua environment
concept is particularly necessary in this project.

Web programming experience can be very helpful especially to understand
the context of use of these tools.

### Skill level

Medium

### Mentor

Tomás Guisasola

### Links

[1] CGILua:   <http://keplerproject.github.io/cgilua/>

[2] WSAPI:    <http://keplerproject.github.io/wsapi/>
