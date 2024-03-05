---
title: 'Routing requests with Flask, with extra authentication parameters'
created: '2024-03-05T06:53:30.378Z'
modified: '2024-03-05T06:54:09.253Z'
---

# Routing requests with Flask, with extra authentication parameters

```python
llm_port = 8000
auth_port = 8001

import requests
from flask import Flask, Response, request

app = Flask(__name__)

sess = requests.Session()

AUTH_TOKEN = "auth_token"
AUTH_HEADER_KEY = "Auth"
GET = "GET"

import json


@app.route('/', defaults={'path': ''}, methods=['GET', 'POST'])
@app.route('/<path:path>', methods=['GET', 'POST'])
def chat_completions(path):
    url = f'http://localhost:{llm_port}{request.full_path}'  # Replace with the streaming URL
    # full path is prefixed with /
    request_headers = dict(request.headers)
    auth = request_headers.get(AUTH_HEADER_KEY, None)
    if auth != AUTH_TOKEN:
        return Response(json.dumps({"state": "unauthorized", "message": "Unauthorized access"}), status = 401)
    no_auth_headers = {k:v for k,v in request_headers.items() if k !=AUTH_HEADER_KEY}
    
    if request.method == GET:
        response = sess.get(url, stream=True, headers=no_auth_headers, data=request.data)
    else:
        response = sess.post(url, stream=True, headers=no_auth_headers, data=request.data)

    def generate():
        for chunk in response.iter_content(chunk_size=1024):
            yield chunk
            
    return Response(generate(), content_type=response.headers['content-type'], headers = dict(response.headers))

if __name__ == '__main__':
    app.run(port=auth_port)
```
