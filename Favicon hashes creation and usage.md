---
title: Favicon hashes creation and usage
created: '2024-05-13T08:34:24.651Z'
modified: '2024-05-13T09:26:35.346Z'
---

# Favicon hashes creation and usage

To create favicon hash, run:

```python
import requests
import mmh3
import codecs

def perform_get_request_with_insecure_and_redirects(url: str):
    response = requests.get(url, verify=False, allow_redirects=True, timeout=15)
    return response


def get_favicon_url(url: str):
    return f"{url}/favicon.ico"


def process_url_and_get_favicon_hash(url: str):
    favicon_url = get_favicon_url(url)
    response perform_get_request_with_insecure_and_redirects(favicon_url)
    favicon = codecs.encode(response.content, "base64")
    _hash = mmh3.hash(favicon)
    _hash = str(_hash)
    return _hash

if __name__ == "__main__":
    url = "https://www.baidu.com"
    icon_hash = process_url_and_get_favicon_hash(url)
    print(f"icon hash for url '{url}':", icon_hash)
```

You can use favicon hash in Shodan like: `http.favicon.hash:<favicon_hash>`

In ZoomEye like: `iconhash:"<favicon_hash>"`
