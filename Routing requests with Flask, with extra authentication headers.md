---
title: 'Routing requests with Flask, with extra authentication headers'
created: '2024-03-05T06:53:30.000Z'
modified: '2024-03-06T03:14:54.295Z'
---

# Routing requests with Flask, with extra authentication headers

Run the following like:

```bash
pip3 install gunicorn
gunicorn --bind localhost:8001 <file_name_without_extension>:app
```

```python
import argparse

import requests
from flask import Flask, Response, request

import json

parser = argparse.ArgumentParser(description='Argument Parser with Default Parameters')

parser.add_argument('--source_port', type=int, default=8000, help='Source Port Number')

args, _ = parser.parse_known_args()

print("Source Port:", args.source_port)

source_port = args.source_port

app = Flask(__name__)

sess = requests.Session()

AUTH_TOKEN = "auth_token"
AUTH_HEADER_KEY = "Auth"
GET = "GET"
POST = "POST"

ALLOWED_METHODS = [GET, POST]

@app.route('/', defaults={'path': ''}, methods=ALLOWED_METHODS)
@app.route('/<path:path>', methods=ALLOWED_METHODS)
def chat_completions(path):
    url = f'http://localhost:{source_port}{request.full_path}' 
    # full path is prefixed with /
    request_headers = dict(request.headers)
    auth = request_headers.get(AUTH_HEADER_KEY, None)
    if auth != AUTH_TOKEN:
        return Response(json.dumps({"state": "unauthorized", "message": "Unauthorized access"}), status = 401)
    no_auth_headers = {k:v for k,v in request_headers.items() if k !=AUTH_HEADER_KEY}
    
    if request.method == GET:
        response = sess.get(url, stream=True, headers=no_auth_headers)
    else:
        response = sess.post(url, stream=True, headers=no_auth_headers, data=request.data, files=request.files, json=request.json)
        # response = sess.post(url, stream=True, headers=no_auth_headers, data=request.data, form=request.form, files=request.files, json=request.json)

    def generate():
        for chunk in response.iter_content(chunk_size=1024):
            yield chunk
            
    return Response(generate(), content_type=response.headers['content-type'], headers = dict(response.headers))

if __name__ == '__main__':
    app.run()
```
