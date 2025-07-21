# Secure-Linux-Web-Server-Setup-with-Monitoring-and-Basic-Firewall


This project demonstrates how to set up a **secure web server on Linux** with **monitoring tools**, **automated backups**, and a **basic firewall** for real-world deployment.

---

## 🚀 Project Objectives

- Provision a secure Linux server (locally or cloud)
- Harden the OS against unauthorized access
- Deploy a web server (Apache/Nginx)
- Enable system monitoring & alerting
- Automate backups using cron and bash
- Configure basic firewall using UFW

---

## 🛠️ Technologies Used

- **Ubuntu 20.04+**
- **Apache / Nginx**
- **SSH Key Authentication**
- **UFW (Uncomplicated Firewall)**
- **Fail2Ban**
- **Monitoring tools:** htop, iftop, netstat
- **Bash scripting**
- **Cron jobs**

---

## 📦 Step-by-Step Implementation

### 1. 🔧 Provision a Linux Server

- Used **VMware Workstation** (or VirtualBox / AWS EC2)
- Installed **Ubuntu OS**

---

### 2. 🔒 Basic OS Hardening

- Created a **non-root user**
- Setup **SSH key-based authentication**
- Disabled root login over SSH
- Configured **UFW** to allow only ports:
  - `22` for SSH
  - `80` for HTTP
  - `443` for HTTPS

---

### 3. 🌐 Install and Configure Web Server

- Installed **Apache** (or Nginx)
- Deployed a **simple HTML site** at `/var/www/html`
- Configured **virtual host** if needed

---

### 4. 📈 Monitoring Tools Setup

- Installed: `htop`, `iftop`, `nmon`, `netstat`
- Installed and configured **Fail2Ban** to block brute-force SSH attempts
- Monitored:
  - CPU and memory usage
  - Network traffic
  - Log files in `/var/log/`

---

### 5. 🔄 Automation using Bash + Cron

- Wrote a bash script to:
  - Backup `/var/www/html`
  - Compress with timestamp using `tar`
  - Store in backup directory

```bash
#!/bin/bash
backup_path="/home/username/backups"
mkdir -p $backup_path
tar -czvf $backup_path/html_backup_$(date +%F_%T).tar.gz /var/www/html
