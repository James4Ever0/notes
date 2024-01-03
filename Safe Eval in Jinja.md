---
title: Safe Eval in Jinja
created: '2024-01-03T08:44:56.882Z'
modified: '2024-01-03T08:48:01.419Z'
---

# Safe Eval in Jinja

```python
from jinja2 import Environment
from jinja2 import StrictUndefined
from jinja2.nativetypes import NativeEnvironment


def simple_eval(expr: str, globals_dict: dict = None):
    globals_dict = globals_dict or {}

    env = Environment(variable_start_string='${', variable_end_string='}', undefined=StrictUndefined)
    template = env.from_string(expr).render(**dict(zip(globals_dict.keys(), globals_dict.keys())))

    native_env = NativeEnvironment(undefined=StrictUndefined)
    return native_env.from_string('{{' + template + '}}').render(**globals_dict)


if __name__ == '__main__':
    print(simple_eval('${a}+1', {'a': 1}) == 2)
```
