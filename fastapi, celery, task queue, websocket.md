---
title: 'fastapi, celery, task queue, websocket'
created: '2023-04-02T10:40:24.782Z'
modified: '2023-04-04T07:40:37.741Z'
---

# fastapi, celery, task queue, websocket

enable render option `trim_blocks` and `lstrip_blocks` with `jinja2` to avoid whitespace and indentation nightmare.

----

always remember to import `uvicorn` if you want to run without the `uvicorn` executable

----

generate [nodejs client](https://fastapi.tiangolo.com/advanced/generate-clients/) from `openapi.json`

[fastapi-code-generator](https://pypi.org/project/fastapi-code-generator/) to generate python code

----

create doc inside code: [adding metadata](https://fastapi.tiangolo.com/tutorial/metadata/)

----

to share lock across process, use [redis lock](https://pypi.org/project/python-redis-lock/) or filelock.

to share lock across forked process in the same worker, use `multiprocessing.Lock()`

----

fastapi can generate openapi json and doc page

websockets are async. will it block the server?

[using websocket in fastapi](https://fastapi.tiangolo.com/zh/advanced/websockets/)

[celery advance usage](https://medium.com/pythonistas/a-complete-guide-to-production-ready-celery-configuration-5777780b3166#:~:text=The%20task%20can%20catch%20this%20to%20clean%20up,try%3A%20return%20do_work%20%28%29%20except%20SoftTimeLimitExceeded%3A%20cleanup_in_a_hurry%20%28%29)

[celery and fastapi](https://derlin.github.io/introduction-to-fastapi-and-celery/03-celery/#:~:text=Celery%20doesn%27t%20provide%20an%20obvious%20way%20to%20limit,is%20already%20running%2C%20he%20should%20get%20an%20error.)

happen to found akismet (proprietary wordpress spam protection). oss alternatives are:

- [Youtube Spammer Purge](https://github.com/ThioJoe/YT-Spammer-Purge)
- [forget spam comment](https://github.com/thegulshankumar/forget-spam-comment/) (js plugin for wordpress)
