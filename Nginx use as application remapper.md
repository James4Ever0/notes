---
title: Nginx use as application remapper
created: '2024-03-07T06:07:06.871Z'
modified: '2024-03-08T01:53:39.556Z'
---

# Nginx use as application remapper

After installing nginx, a default page is created under `/var/www/html` and config files are at `/etc/nginx`.

Run `sudo systemctl restart nginx` after config modification.

---

Edit the file at `/etc/nginx/sites-available/default`:

```nginx
server {
  listen 80;
  server_name localhost;

  location /app1 {
    proxy_pass http://localhost:8000;
  }

  location /app2 { # websocket support
    proxy_pass http://localhost:8001;

		proxy_http_version 1.1;
		proxy_set_header Upgrade $http_upgrade;
		proxy_set_header Connection "upgrade";
  }
}
```

---

If you want to route FastAPI docs to nginx, you have to rewrite contents.

```nginx
server {
	location /vllm/openapi.json {
		proxy_pass http://localhost:8000/openapi.json;
		sub_filter "\"paths\"" "\"servers\": [{\"url\": \"/vllm\"}], \"paths\"";
		sub_filter_types application/json;
	}

	location /vllm/ {
		proxy_pass http://localhost:8000/;
		sub_filter "openapi.json" "vllm/openapi.json";
		sub_filter_once off;

	}
}
```
