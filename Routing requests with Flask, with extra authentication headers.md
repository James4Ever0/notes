---
title: 'Routing requests with Flask, with extra authentication headers'
created: '2024-03-05T06:53:30.378Z'
modified: '2024-03-05T08:55:07.770Z'
---

# Routing requests with Flask, with extra authentication headers

```python
import argparse

parser = argparse.ArgumentParser(description='Argument Parser with Default Parameters')

parser.add_argument('--source_port', type=int, default=8000, help='Source Port Number')
parser.add_argument('--auth_host', type=str, default=None, help='Authentication Host')
parser.add_argument('--auth_port', type=int, default=8001, help='Authentication Port Number')

args = parser.parse_args()

print("Source Port:", args.source_port)
print("Authentication Host:", args.auth_host)
print("Authentication Port:", args.auth_port)

source_port = args.source_port
auth_host =  args.auth_host
auth_port = args.auth_port

import requests
from flask import Flask, Response, request

app = Flask(__name__)

sess = requests.Session()

AUTH_TOKEN = "auth_token"
AUTH_HEADER_KEY = "Auth"
GET = "GET"

ALLOWED_METHODS = ['GET', 'POST']

import json


@app.route('/', defaults={'path': ''}, methods=ALLOWED_METHODS)
@app.route('/<path:path>', methods=ALLOWED_METHODS)
def chat_completions(path):
    url = f'http://localhost:{source_port}{request.full_path}'  # Replace with the streaming URL
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
    app.run(host=auth_host, port=auth_port)
```
