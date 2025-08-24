

### **1. Install nginx**

```
sudo yum install nginx -y
```

### **2. Enable and start nginx**

```
sudo systemctl enable --now nginx
```

### **3. Edit /etc/nginx/nginx.conf for 3 websites**


- Example
```
http {
    # existing configs like log_format, etc.

    upstream backend_servers {
        # Load balancing algorithms:
        # round_robin (default), least_conn, ip_hash
        least_conn;

        server 10.0.0.11:8080 max_fails=3 fail_timeout=30s;
        server 10.0.0.12:8080 max_fails=3 fail_timeout=30s;
        server 10.0.0.13:8080 max_fails=3 fail_timeout=30s;
    }

    server {
        listen 80;
        server_name _;

        location / {
            proxy_pass http://backend_servers;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }
    }
}

```


# 🔹 Load Balancing Methods in NGINX

### 1. **Round Robin** (default)

- No directive needed, enabled by default.
    
- Requests are sent to servers in order.
    

```
upstream backend {     
	server 10.0.0.11;     
	server 10.0.0.12; 
	}
	
```

---

### 2. **Least Connections**

- Sends requests to the server with the fewest active connections.
    
```
upstream backend {
    least_conn;
    server 10.0.0.11;
    server 10.0.0.12;
}

```


---

### 3. **IP Hash**

- Ensures the same client IP always goes to the same server (sticky sessions).
    

```
upstream backend {
    ip_hash;
    server 10.0.0.11;
    server 10.0.0.12;
}

```