

# Install Docker CE

**Remove any old versions (optional but recommended):

```
sudo yum remove -y docker docker-client docker-client-latest docker-common docker-latest \
    docker-latest-logrotate docker-logrotate docker-engine
```

**Add required packages and Docker repo:

```
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

**Install Docker CE:

```
sudo yum install -y docker-ce docker-ce-cli containerd.io
```

**Install Docker Compose

```
sudo yum install -y docker-compose
```

**Option 2: If repo doesn’t have it (common in CentOS), install via binary:

```
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

**Start Docker Service
```
sudo systemctl start docker
sudo systemctl enable docker
```

**Verify it’s running:

```
systemctl status docker
```

At this point:

- **Docker CE is installed**
    
- **Docker Compose is installed**
    
- **Docker service is running and enabled**