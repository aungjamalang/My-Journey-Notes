
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


### **3. Fork the repo**


- You can fork the repo for private
- You can fork the repo for public


# Update Git Repository with Sample HTML File


### 1. Copy the file from jump host to storage server

From the **jump host**, copy the `index.html` file to the storage server under `/tmp/` (or directly to repo path):

`scp /path/to/index.html storage_server:/tmp/`

> Replace `storage_server` with the actual hostname or IP of your storage server.

---

### 2. Move file into the repository

SSH into the **storage server**:

`ssh storage_server`

Move the file into the repo directory:

`mv /tmp/index.html /usr/src/kodekloudrepos/official/ cd /usr/src/kodekloudrepos/official`

---

### 3. Git add and commit

Make sure you are inside the repo:

```
git status 
git add index.html 
git commit -m "Add sample index.html file"
```

---

### 4. Push to master branch

Push changes to the remote repository:

`git push origin master`

---

✅ Done! The `index.html` is now inside `/usr/src/kodekloudrepos/official`, committed, and pushed to `master`.

