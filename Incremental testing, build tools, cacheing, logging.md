---
title: 'Incremental testing, build tools, cacheing, logging'
created: '2023-06-16T03:55:12.384Z'
modified: '2023-07-06T02:42:54.475Z'
---

# Incremental testing, build tools, cacheing, logging

code comparison:

difftastic

c/cpp/c++ code formatting:

clang-format
astyle
Uncrustify

---

how to log error emitted from `better-exceptions`?

----

logging tutorial at [betterstack](https://betterstack.com/community/guides/logging/python/python-logging-best-practices/) & [official](https://docs.python.org/3/howto/logging.html)

other logging libraries: [loguru](https://betterstack.com/community/guides/logging/loguru/) [structlog](https://www.structlog.org/en/stable/) (able to show locals/globals around error)

----

[better-exceptions](https://github.com/qix-/better-exceptions)

----

to ensure the consistency of tests, you need to collect input/output pairs (and compare with expected/actual output), if it is deterministic.

----

monkeytype, pytype (by google), runtype (Dispatch)

----

better assertion

----

[enum class](https://docs.python.org/3/howto/enum.html#enum-class-differences) in python

----

use [cache](https://docs.pytest.org/en/6.2.x/cache.html) in pytest

use redis lru_cache, put decorators to json serializable functions

use build tools, forcing program to read and write files in the process

type checking using mypy

code static analysis

code formatter like black

----

tools:

[pydoit](https://pydoit.org/dependencies.html) with "up to date" signals for non-file objectives

[scons](https://scons.org/doc/production/HTML/scons-user.html#idp105549032593992)

ruby [rake](https://graceful.dev/courses/the-freebies/modules/rake-and-project-automation/topic/episode-131-rake-rules/)
