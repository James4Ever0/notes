---
title: peewee related notes
created: '2022-10-27T09:56:36.857Z'
modified: '2022-10-27T10:30:30.567Z'
---

# peewee related notes

## extensions

[peewee extension docs](https://www.osgeo.cn/peewee/peewee/sqlite_ext.html#sqlite-ext)

## full-text search

[official doc on full-text search](https://peewee-orm.com/blog/using-sqlite-full-text-search-with-python/)

[how to use ftsmodel](https://www.osgeo.cn/peewee/peewee/sqlite_ext.html#FTSModel)

Peewee包括 SQLite extension module 它提供了许多特定于sqlite的功能，例如 full-text search ， json extension support 还有更多。如果您想使用这些出色的功能，请使用 SqliteExtDatabase 从 playhouse.sqlite_ext 模块：

```python
from playhouse.sqlite_ext import SqliteExtDatabase

sqlite_db = SqliteExtDatabase('my_app.db', pragmas={
    'journal_mode': 'wal',  # WAL-mode.
    'cache_size': -64 * 1000,  # 64MB cache.
    'synchronous': 0})  # Let the OS manage syncing.
```

## enhancement proposals

[enhancement for doing get/update/create at the same time](https://github.com/coleifer/peewee/issues/2639)

[enhancement to simplify the BaseModel boilerplate code ](https://github.com/coleifer/peewee/issues/2637)
