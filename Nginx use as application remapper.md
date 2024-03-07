---
title: Nginx use as application remapper
created: '2024-03-07T06:07:06.871Z'
modified: '2024-03-07T06:14:37.308Z'
---

# Nginx use as application remapper

After installing nginx, a default page is created under `/var/www/` and config files are at `/etc/nginx`.

If you want to modify nginx configs, run `sudo systemctl restart nginx` after modification.

---

Edit the file at `/etc/nginx/sites-available/default`:

```nginx
server {
  listen 80;
  server_name localhost;

  location /app1 {
    proxy_pass http://localhost:8000;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
  }

  location /app2 {
    proxy_pass http://localhost:8001;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
  }
}

```
