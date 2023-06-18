---
title: 'Incremental testing, build tools, cacheing'
created: '2023-06-16T03:55:12.384Z'
modified: '2023-06-18T04:07:24.858Z'
---

# Incremental testing, build tools, cacheing

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
