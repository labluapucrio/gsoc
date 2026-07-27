## Project:

Concurrent Lua scripts execution in Redis

### Brief explanation:

Redis is a popular open source key-value store that supports scripting using the Lua programming language. Howerer, Redis uses the same Lua interpreter to run all the commands so  while the script is running no other client can execute commands. The objective of this project is to support parallel script execution without loosing their atomicity and cluster support.

### Expected results:

A fork of Redis with support for concurrent Lua scripts executions, leveraging the use of more complex and slow scripts.

### Knowledge prerequisite:

C, Lua, Redis, pthreads

### Skill level:

Medium

### Mentor:

Noemi Rodriguez
