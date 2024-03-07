---
title: Nginx use as application remapper
created: '2024-03-07T06:07:06.871Z'
modified: '2024-03-07T08:44:56.130Z'
---

# Nginx use as application remapper

After installing nginx, a default page is created under `/var/www/html` and config files are at `/etc/nginx`.

Run `sudo systemctl restart nginx` after config modification.

---

Do not even try to route FastAPI doc to nginx, which is a pain in the ass.

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
