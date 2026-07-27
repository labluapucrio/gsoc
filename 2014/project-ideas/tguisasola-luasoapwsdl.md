## Project

Add support for WSDL generation to LuaSOAP

## Brief explanation

[LuaSOAP](http://tomasguisasola.github.io/luasoap/) [1] is a library to
ease the use of [SOAP](http://www.w3.org/TR/soap/) [2].  LuaSOAP provides
a very simple API that convert Lua tables to and from XML documents.
It also offers a simple way to invoke remote Web Services without having
to deal directly with SOAP messages.  In fact, LuaSOAP also provides
a simple way to offer Web Services -- the server side -- but it lacks
support for WSDL generation of the offered services.

[WSDL](http://www.w3.org/TR/wsdl) [3] is an XML format for describing
network services.  It is used to describe operations and messages --
with its types -- offered by Web Services.  Since Lua code does not
include type information, automatic generation has to be based on some
kind of hand-made declarative information.

## Expected results

* Define the format to describe complementary WSDL information in Lua
* Implement an automatic generator of WSDL documents
* Test and document everything

## Knowledge prerequisites

Lua programming; client-server web architecture; SOAP and WSDL specifications.

* Basic programming in Lua is mandatory
* Web programming experience is very appreciated but not mandatory
* SOAP and WSDL specifications could be learned during the project

## Skill level

Simple

## Mentor

Tomás Guisasola

## Links

[1] LuaSOAP:   http://tomasguisasola.github.io/luasoap/
[2] SOAP:      http://www.w3.org/TR/soap/
[3] WSDL:      http://www.w3.org/TR/wsdl

