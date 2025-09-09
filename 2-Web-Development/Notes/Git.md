
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

```
mv /tmp/index.html 
/usr/src/kodekloudrepos/official/ 
cd /usr/src/kodekloudrepos/official
```

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


# Delete Git Branch


The Nautilus developers are engaged in active development on one of the project repositories located at /usr/src/kodekloudrepos/ecommerce. During testing, several test branches were created, and now they require cleanup. Here are the requirements provided to the DevOps team: On the Storage server in Stratos DC, delete a branch named xfusioncorp_ecommerce from the /usr/src/kodekloudrepos/ecommerce Git repository.

1. **Switch to the repo directory**
    

`cd /usr/src/kodekloudrepos/ecommerce`

2. **Check available branches** (to confirm the branch exists)
    

`git branch`

You should see `xfusioncorp_ecommerce` in the list.

3. **Delete the branch**
    

`git branch -d xfusioncorp_ecommerce`

> ⚠️ Note: `-d` only works if the branch is fully merged into its upstream.  
> If it’s not merged and you still want to delete it, use:

`git branch -D xfusioncorp_ecommerce`

4. **Verify deletion**
    

`git branch`

The branch should no longer appear.

# OR


1. **Switch to a safe branch** (e.g. `master` or `main`):
    

`git checkout master`

(if your repo uses `main`, replace `master` with `main`).

2. **Now delete the unwanted branch**:
    

`git branch -D xfusioncorp_ecommerce`

3. **Verify**:
    

`git branch`

You should no longer see `xfusioncorp_ecommerce` in the list.

# Exam

### 1. **SSH into the storage server**

`ssh sarah@<storage_server_ip>`

Password: `S3cure321`

---

### 2. **Go to the repo directory**

`cd /home/sarah/story-blog-t1q8`

---

### 3. **Check the Git status**

`git status`

This will show you which files are in the staging area (`Changes to be committed`).

---

### 4. **Commit the staged files**

`git commit -m "Added the lion and mouse story"`

---

### 5. **Verify commit**

`git log --oneline -1`

You should see the latest commit with the message:  
`Added the lion and mouse story`


One of the nautilus developers added some data under `/usr/src/kodekloudrepos/demo-t2q6` repository, however they later realised that there is a typo in one of the files. Let's fix the typo.

  

In the `lion-and-mouse.txt` file, `LION` is mis-spelt as `LIOON`. Please fix it and then commit the changes with a commit message: `Fix typo in story title`

Use below credentials to SSH into the storage server and to complete this task.

`Username:` sarah  
`Password:` S3cure321

### 1. **SSH into the storage server**

`ssh sarah@<storage_server_ip>`

Password: `S3cure321`

---

### 2. **Navigate to the repository**

`cd /usr/src/kodekloudrepos/demo-t2q6`

---

### 3. **Open the file and fix the typo**

Edit the file using `vi` or `nano`:

`vi lion-and-mouse.txt`

(or)

`nano lion-and-mouse.txt`

Find the word **`LIOON`** and change it to **`LION`**.  
Save and exit.

---

### 4. **Stage the changes**

`git add lion-and-mouse.txt`

---

### 5. **Commit the fix**

`git commit -m "Fix typo in story title"`

---

### 6. **Verify**

`git log --oneline -1`

You should see:

`<commit-hash> Fix typo in story title`




A new repository named `/usr/src/kodekloudrepos/demo-t2q5` was created recently and some data was added in it. Now one of the developers wanted to use this repository further to add/update some data.

  

Checkout the `master` branch under repo `/usr/src/kodekloudrepos/demo-t2q5`.

Use below credentials to SSH into the storage server and to complete this task.

`Username:` sarah  
`Password:` S3cure321


