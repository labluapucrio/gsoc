## Project

Develop a binary serialization format with support for dynamically types values and an RPC protocol for dynamically typed invocations based on this format.

### Brief explanation

Most RMI protocols available today are either focused on inefficient representation formats for typing information [1](http://www.omg.org/spec/CORBA/3.3/Interoperability/PDF) [2](http://hessian.caucho.com) [3](https://developers.google.com/protocol-buffers/), or on invocations where the typing information are predefined and static, therefore are absent on the data sent through the wire [5](http://www.json.org) [4](http://www.w3.org/TR/soap/) [6](http://www.caucho.com/resin-3.0/protocols/burlap.xtp). Few protocols are designed to work efficiently with typed data. Invocations with typed data work well with the RPC model because it allows the identification of deployment problems (mismatch interfaces) and facilitate the dynamic evolution of distributed systems. A protocol for dynamically typed RPC should be based on a efficient serialization format for typed data, that is, information about how the data should be interpreted.

The goal of this project is to design and implement a serialization binary serialization format with the following requirements:

* Primitive data: numeric formats (integer and floating-point), characters and boolean.

* Structured data: serialization of usual structured data like records, arrays, maps, tuples, union, etc.

* Optional typing: serialization of both raw data and data plus typing information.

* Structurual compatibility: type information should allow to efficiently verify whether two types are compatibile.

* Opaque data: allow that a special form of raw data (without typing information) can be ignored without compromising the remains of the stream and that can also be passed along by a receiver that did not interpreted it.

* Semantic information: data types that can extend a standard type with additional semantic information, like a string (sequence of characteres) with an associated charset or a record with an associated class name that provides some behavior over the data on the record.

* Graphs: data with cyclic references.

### Expected results

* An specification of a binary serialization format with support for typed data.
* An implementation of a library for encoding values using this format.

### Knowledge prerequisites

* Basic programming skills (preferably C or Lua).

### Skill level

Hard

### Mentor

Renato Maia

### Links

[1](http://www.omg.org/spec/CORBA/3.3/Interoperability/PDF) GIOP/IIOP (CORBA) <http://www.omg.org/spec/CORBA/3.3/Interoperability/PDF>

[2](http://hessian.caucho.com) Hessian <http://hessian.caucho.com>

[3](https://developers.google.com/protocol-buffers/) Google Protocol Buffers <https://developers.google.com/protocol-buffers/>

[5](http://www.json.org) JSON <http://www.json.org>

[4](http://www.w3.org/TR/soap/) SOAP <http://www.w3.org/TR/soap/>

[6](http://www.caucho.com/resin-3.0/protocols/burlap.xtp) Burlap <http://www.caucho.com/resin-3.0/protocols/burlap.xtp>
