
# 🛠️ OpenVAS (GVM) Installation Cheat-Sheet

Quick-reference guide for installing and setting up **OpenVAS (GVM)** on a Linux system for pentesting labs.

---

## ⚡ System Update

```bash
sudo apt update -y
```
💡 **Tip:** Always start with a fresh, updated package list to avoid dependency issues.

---

## 📥 Install OpenVAS

```bash
sudo apt install openvas
```
💡 **Tip:** Installs scanner, manager, and web interface in one go.

---

## ⚙️ Initial Setup

```bash
sudo gvm-setup
```
✅ Creates `_gvm` user, initializes the database, and generates SSL certificates.

---

## 🔍 Verify Setup

```bash
sudo gvm-check-setup
```
💡 Ensures services, database, and feeds are correctly configured.

---

## 🌐 Synchronize Feeds

### SCAP Feed
```bash
sudo greenbone-feed-sync --type scap
```
🔹 Contains vulnerability definitions for accurate scanning.

### CERT Feed
```bash
sudo greenbone-feed-sync --type cert
```
🔹 Contains latest security advisories and threat intelligence.

---

## 🔄 Re-check Setup

```bash
sudo gvm-check-setup
```
✅ Confirm feeds are synced and services are healthy.

---

## 👤 Create Admin User

```bash
sudo runuser -u _gvm -- gvmd --create-user=bakawolf --new-password=Ilovebug@1
```
⚠️ Replace `bakawolf` and `Ilovebug@1` with your own username and strong password.

---

## ▶️ Start Services

```bash
sudo gvm-start
```
🌐 Access the web UI: **https://127.0.0.1:9392**

---

## ⏹ Stop Services

```bash
sudo gvm-stop
```
💡 Stop all services safely before shutdown or maintenance.

---

## 💡 Pro Hacker Tips

- Always run `gvm-check-setup` after updates.  
- Feed sync may take time; patience is key.  
- Run scans in isolated labs to avoid alerts.  
- Keep `_gvm` credentials secure; never expose publicly.  
- Use VM snapshots before major updates for rollback.  
- Monitor CPU & RAM usage; OpenVAS is resource-intensive.

---

