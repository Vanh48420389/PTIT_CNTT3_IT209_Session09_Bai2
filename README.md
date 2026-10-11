# Báo Cáo Thực Hành Bài 2: Khởi Chạy Nginx Với Port Mapping

## 1. Khởi chạy Container Nginx (chế độ ngầm, map port 8080:80)
```bash
$ docker run -d -p 8080:80 --name my-web nginx:alpine
2ac19e3e3e68966da1f37963f0f7fcce15e09bc995398d88dc69423b6be2f259
```

## 2. Kiểm tra trạng thái Container (docker ps)
```bash
$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED                  STATUS                  PORTS                                     NAMES
2ac19e3e3e68   nginx:alpine   "/docker-entrypoint.…"   Less than a second ago   Up Less than a second   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   my-web
```

## 3. Kiểm tra phản hồi Web Server (curl http://localhost:8080)
```bash
$ curl -i http://localhost:8080
  % Total    % Received % Xferd  Average Speed  Time    Time    Time   Current
                                 Dload  Upload  Total   Spent   Left   Speed
  0      0   0      0   0      0      0      0                              0100    896 100    896   0      0   3941      0                              0100    896 100    896   0      0   2699      0                              0100    896 100    896   0      0   1865      0                              0
HTTP/1.1 200 OK
Server: nginx/1.31.6
Date: Sun, 11 Oct 2026 16:17:37 GMT
Content-Type: text/html
Content-Length: 896
Last-Modified: Tue, 15 Sep 2026 14:18:52 GMT
Connection: keep-alive
ETag: "6aa953cc-380"
Accept-Ranges: bytes

<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, nginx is successfully installed and working.
Further configuration is required for the web server, reverse proxy, 
API gateway, load balancer, content cache, or other features.</p>

<p>For online documentation and support please refer to
<a href="https://nginx.org/">nginx.org</a>.<br/>
To engage with the community please visit
<a href="https://community.nginx.org/">community.nginx.org</a>.<br/>
For enterprise grade support, professional services, additional 
security features and capabilities please refer to
<a href="https://f5.com/nginx">f5.com/nginx</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

## 4. Dọn dẹp Container
```bash
$ docker stop my-web && docker rm my-web
my-web
my-web
```
