Intermediate Nginx Concepts

1. Reverse Proxy

A reverse proxy is a server that sits between client devices and backend servers, forwarding client requests to the appropriate backend server. Nginx is widely used as a reverse proxy due to its efficiency and flexibility.

***Configuring Nginx as a Reverse Proxy***

To configure Nginx as a reverse proxy, you'll need to set up a server block that listens for incoming requests and forwards them to one or more backend servers.   

```bash
server {
    listen 80;
    server_name yourdomain.com;

    location / {
        proxy_pass http://backend_server;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
```

**Explanation:**
-  `proxy_pass`: Specifies the backedn server where requests should be forwarded;
-   `proxy_set_header`: Passes client information to the backend server, such as the original IP address and protocol.

**Setting Up Reverse Proxy with Load Balancing**

 Load balancing distributes incoming requests across multiple backend servers to ensure no single server becomes overwhelmed. Nginx supports several load-balancing algorithms:

-   Round-Robin : Distributes requests evenly across all backend servers.

```bash
upstream backend_servers{
    server backend1.example.com;
    server backend2.example.com;
}

server{
    listen 80;
    server_name yourdomain.com;

    location / {
        proxy_pass http://backend_servers;
    }
}
```
-   Least Connections: Directs requests to the server with the fewer active connections.

```bash
upstream backend_servers {
    least_conn;
    server backend1.example.com;
    server backend2.example.com;
}
```
-   IP Hash: Route requests from the same client IP backend server.

```bash
upstream backend_servers {
    ip_hash;
    server backend1.example.com;
    server backend2.example.com;
}
```