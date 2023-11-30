# superheroes-docker

Use this NGINX container nginx.conf if you using Docker Desktop


worker_processes 1;

events { worker_connections 1024; }

http {

    sendfile on;

    upstream web-site {
        server host.docker.internal:5000;
    }

    server {
        listen 8080;
        server_name $hostname;
        location / {
            proxy_pass         http://web-site;
            proxy_redirect     off;
            proxy_http_version 1.1;
            proxy_cache_bypass $http_upgrade;
            proxy_set_header   Upgrade $http_upgrade;
            proxy_set_header   Connection keep-alive;
            proxy_set_header   Host $host;
            proxy_set_header   X-Real-IP $remote_addr;
            proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header   X-Forwarded-Proto $scheme;
            proxy_set_header   X-Forwarded-Host $server_name;
        }
    }
}


and please run this command first for .Net Web API 6, 


dotnet publish -c Release -o dotnet-three

Put the dotnet-three directory inside the superheroes-docker directory, make sure you have a Dockerfile inside the dotnet-three directory