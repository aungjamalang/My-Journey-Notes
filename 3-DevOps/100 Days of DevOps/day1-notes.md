# Linux User Setup with Non-Interactive Shell

## 📋 Project Overview

**Objective:** Create a user account with non-interactive shell capabilities to accommodate backup agent tool specifications at xFusionCorp Industries.

**Target Server:** App Server 2  
**Username:** `kirsty`  
**Shell Type:** Non-interactive shell

---

## 🎯 Task Requirements

- [ ] Establish secure connection to App Server 2
- [ ] Create user `kirsty` with appropriate non-interactive shell
- [ ] Verify user creation and configuration
- [ ] Ensure compatibility across different Linux distributions

---

## 🔧 Implementation Steps

### Step 1: Secure Server Access

Connect to the target server using SSH protocol:

```bash
ssh <your-username>@<app-server-2-ip>
```

**Connection Parameters:**

- **Protocol:** SSH (Secure Shell)
- **Username:** System-specific (e.g., `tony`, `ubuntu`, `ec2-user`, `root`)
- **Target IP:** 172.16.x.x (App Server 2)

When prompted for connection confirmation:

```bash
Are you sure you want to continue connecting (yes/no[fingerprint])? yes
```

### Step 2: Determine Non-Interactive Shell Path

Identify the correct nologin binary location for your Linux distribution:

```bash
which nologin
```

### Step 3: User Creation (Distribution-Specific)

Execute the appropriate command based on your system's nologin path:

#### For Modern Linux Distributions

If `which nologin` returns `/sbin/nologin`:

```bash
sudo useradd -s /sbin/nologin kirsty
```

#### For Alternative Distributions

If `which nologin` returns `/usr/sbin/nologin`:

```bash
sudo useradd -s /usr/sbin/nologin kirsty
```

#### For Legacy Systems

For older Linux systems without nologin:

```bash
sudo useradd -s /bin/false kirsty
```

### Step 4: Verification

Confirm successful user creation:

```bash
getent passwd kirsty
```

**Expected Output:**

```
kirsty:x:1002:1002::/home/kirsty:/sbin/nologin
```

---

## ✅ Validation Checklist

|Task|Status|Notes|
|---|---|---|
|SSH connection established|✅|Secure access to App Server 2|
|Non-interactive shell identified|✅|Path verified via `which nologin`|
|User `kirsty` created|✅|Account configured with proper shell|
|Configuration verified|✅|Confirmed via `getent passwd`|

---

## 📊 Technical Details

**User Configuration:**

- **Username:** `kirsty`
- **UID:** Auto-assigned (e.g., 1002)
- **GID:** Auto-assigned (e.g., 1002)
- **Home Directory:** `/home/kirsty`
- **Shell:** `/sbin/nologin` (or distribution-specific path)

**Security Benefits:**

- Prevents interactive login sessions
- Suitable for service accounts and automated tools
- Maintains system security while allowing specific functionality

---

## 🔍 Troubleshooting Guide

### Common Issues

1. **Permission Denied**
    
    - Ensure you have sudo privileges
    - Verify you're logged in as an authorized user
2. **Command Not Found**
    
    - Check if the nologin binary exists on your system
    - Use `/bin/false` as fallback for legacy systems
3. **User Already Exists**
    
    - Use `userdel kirsty` to remove existing user if needed
    - Check existing users with `getent passwd | grep kirsty`

---

## 📝 Best Practices

- Always verify shell paths before user creation
- Use `getent passwd` for user verification instead of `/etc/passwd`
- Document distribution-specific configurations
- Test non-interactive shell functionality post-creation
- Maintain audit logs for user management activities

---

## 🏆 Completion Summary

The user `kirsty` has been successfully created on App Server 2 with a non-interactive shell configuration, meeting the backup agent tool requirements for xFusionCorp Industries. The implementation ensures compatibility across different Linux distributions while maintaining security best practices.

**Status:** ✅ **COMPLETED**  
**Environment:** App Server 2  
**Compliance:** Backup Agent Tool Specifications