## Project

Add labeled failures to [LPeg](http://www.inf.puc-rio.br/~roberto/lpeg/) [1].

### Brief explanation

Parsing Expression Grammars (PEGs) are an expressive formalism for
designing and implementing top-down parsers with local backtracking.
However, PEGs do not support the error handling techniques that are often
implemented in top-down parsers, because these techniques assume the parser
reads the input without backtracking.

Parsing Expression Grammars for Lua (LPeg) is a pattern-matching tool
based on PEGs.
Although it is quick and easy to write parsers using LPeg, like PEGs, it
does not provide any support to the programmer handle parsing errors.

### Expected results

There is an extension to the PEGs formalism that introduces [labeled
failures](http://www.inf.puc-rio.br/~roberto/docs/sblp2013-1.pdf) as a way
to annotate and label grammar pieces that should
not fail [2].
In this approach, each label may be tied to a specific error message
and resembles the concept of exceptions from programming languages.
The aim of this project is to create a LPeg fork that implements this
error reporting technique.

### Knowledge prerequisites

C, Lua, and Parsing Expression Grammars

### Skill level

Hard

### Mentor

[Roberto Ierusalimschy](http://www.inf.puc-rio.br/~roberto)

### Links

[1] LPeg: <http://www.inf.puc-rio.br/~roberto/lpeg/>

[2] Exception Handling for Error Reporting in Parsing Expression Grammars:
<http://www.inf.puc-rio.br/~roberto/docs/sblp2013-1.pdf>

[3] Roberto Ierusalimschy: <http://www.inf.puc-rio.br/~roberto>

