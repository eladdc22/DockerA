# Docker module
Writing a DOCKERFILE

---

## Preparations

- Create Directory 
```
mkdir server
```

- Navigate to new Directory 
```
cd server
```

- Create the file
```
touch Dockerfile
```

- Create the server file
```
touch server
```
## Instructions

 - Edit the Dockerfile using (nano, vim, vi ) :
  - for example:
``` 
  vim Dockerfile
```

- Add the following
```
FROM ubuntu:22.04

RUN apt-get -y update && apt-get -y install nginx

COPY server /etc/nginx/sites-available/default

EXPOSE 80/tcp

CMD ["/usr/sbin/nginx", "-g", "daemon off;"]
```

 - Edit the server file using (nano, vim, vi ) :
  - for example:
``` 
  vim server
```

- Add the following
```
server {
    listen 80 default_server;
    listen [::]:80 default_server;

    root /usr/share/nginx/html;
    index index.html index.htm;

    server_name _;
    location / {
        try_files $uri $uri/ =404;
    }
}
```
