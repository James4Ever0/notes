---
title: Favicon hashes creation and usage
created: '2024-05-13T08:34:24.651Z'
modified: '2024-05-13T09:19:09.541Z'
---

# Favicon hashes creation and usage

To create favicon hash, run:

```python
import requests

def perform_get_request_with_insecure_and_redirects(url: str):
    response = requests.get(url, verify=False, allow_redirects=True, timeout=15)
    return response


def get_favicon_url(url: str):
    return f"{url}/favicon.ico"


def process_url_and_get_favicon_hash(url: str):
    try:
        favicon_url = get_favicon_url(url)
        InfoConsole.positive("Processing favicon URL:", favicon_url)
        response = perform_get_request_with_insecure_and_redirects(favicon_url)
        favicon = codecs.encode(response.content, "base64")
        _hash = mmh3.hash(favicon)
        _hash = str(_hash)
```

You can use favicon hash in Shodan like: ``

In ZoomEye like: ``
