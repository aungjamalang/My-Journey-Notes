
The Nautilus development team has provided requirements to the DevOps team for a new application development project, specifically requesting the establishment of a Git repository. Follow the instructions below to create the Git repository on the `Storage server` in the Stratos DC:  

1. Utilize `yum` to install the `git` package on the `Storage Server`.
2. 1. Create a bare repository named `/opt/official.git` (ensure exact name usage).


### Solution

### **1. Install Git using yum**

```
sudo yum install git -y
```

This will install the Git package on the server.
### **2. Create the bare repository**

A _bare_ repository is used for sharing and collaboration (no working directory).

```
sudo mkdir -p /opt/official.git
sudo git init --bare /opt/official.git
```

### **3. Verify the repository**

```
ls -lah /opt/official.git
```

You should see directories like `branches/`, `hooks/`, `info/`, `objects/`, `refs/`, and files like `HEAD`, `config`, `description`.

✅ At this point, you’ll have a **bare Git repository at `/opt/official.git`** ready for your developers.


# 1. Pushing to a **bare repo** (✅ correct, safe)

Server side:

`mkdir -p /opt/official.git cd /opt/official.git git init --bare`

Developer side:

`git clone user@server:/opt/official.git cd official echo "Hello Bug Bounty" > readme.txt git add readme.txt git commit -m "Initial commit" git push origin main`

- Works fine ✅.
    
- Bare repo doesn’t have a working directory, so `main` branch just points to the new commit.
    
- Other developers can safely pull and work.

