---
title: Nginx use as application remapper
created: '2024-03-07T06:07:06.000Z'
modified: '2024-07-01T09:34:19.753Z'
---

# Nginx use as application remapper

for more accurate results, use [nginx-geoip2](https://frankindev.com/2021/10/20/nginx-geoip2)

to disable access by ip origin while exclude certain ranges, you can do this:

```bash
apt install -y libnginx-mod-http-geoip libgeoip
```

```nginx
http {
  geoip_country /usr/share/GeoIP/GeoIP.dat;
	geoip_proxy <internal_ip_ranges>;

	geo $external_ip {
		default 1;
    <custom_exclusion_range> 0;
	}

  log_format geologfmt '$remote_addr - $remote_user <$geoip_country_code> [$time_local] '
                           '"$request" $status $body_bytes_sent '
                           '"$http_referer" "$http_user_agent"';

	access_log /var/log/nginx/access.log geologfmt;
}

server {
  # boolean operator in nginx
  # better do this with njs instead
  set $a 0;
  set $b 0;
  if ($geoip_country_code != "<YOUR_COUNTRY_CODE>"){
    set $a 1;
  }
  if ($external_ip){
    set $a 1$a;
  }
  if ($a = 11){
    set $b 1;
  }
  if ($b){return 444;}
}
```

remember to restart nginx service afterwards

---

enable http basic auth

```bash
sudo htpasswd -c /etc/nginx/passwd <username>
```

```nginx
server {
  auth_basic "<auth_window_title>";
  auth_basic_user_file passwd;
}
```

---

Run nginx with debug info:

```nginx
# within /etc/nginx/nginx.conf
http {
    access_log /var/log/nginx/access.log debug;
    error_log /var/log/nginx/error.log debug;
}

```

---

Remap a range of ports to suburl:

```nginx
location ~ /server/(1[0-9][0-9][0-9][0-9]) {
    proxy_pass http://localhost:$1/;
}
```

---

To handle CORS errors, one can write:

```nginx

	location /api/ {
		# add_header Access-Control-Allow-Origin *;
		add_header Access-Control-Allow-Origin $http_origin;
		add_header 'Access-Control-Allow-Headers' 'Content-Type';

		if ($request_method = OPTIONS) {
			add_header Access-Control-Allow-Origin *;
			add_header 'Access-Control-Allow-Methods' 'GET, POST, OPTIONS';
			add_header 'Access-Control-Allow-Headers' 'Content-Type, x-requested-with';
			add_header 'Access-Control-Max-Age' 1728000;
			add_header 'Content-Type' 'text/plain; charset=utf-8';
			return 204;
		}
		proxy_pass http://localhost:7861/;
		# proxy_set_header X-Forwarded-Prefix /api;

		sub_filter "openapi.json" "api/openapi.json";
		# sub_filter "SwaggerUIBundle({" "SwaggerUIBundle({ basePath: '/api', 'servers': [{url:'/api'}],";
		sub_filter "static-offline-docs" "api/static-offline-docs";
		sub_filter_once off;
	}
```

---

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
    proxy_set_header Origin ""; // to prevent unwanted 403
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
