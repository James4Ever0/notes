---
title: Python continue decoding despite error
created: '2024-07-01T09:37:13.022Z'
modified: '2024-07-01T09:42:31.893Z'
---

# Python continue decoding despite error

When using `chardet` you may get some confidence mark over a particular file. If that number is below one then you may face issues when decoding.

Specify `error=<error_handle_strategy>` can mitigate this issue.

The default is 'strict' meaning that encoding errors raise a UnicodeEncodeError.  Other possible values are 'ignore', 'replace' and 'xmlcharrefreplace' as well as any other name registered with codecs.register_error that can handle UnicodeEncodeErrors.
