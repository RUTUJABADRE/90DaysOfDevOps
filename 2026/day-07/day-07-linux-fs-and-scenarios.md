# Day 07 – Linux File System Hierarchy & Scenario-Based Practice

**Core Directories (Must Know):**

---

- `/` (root) - The starting point of everything
  
  Purpose: I would use this when I want to navigate the entire file system.

- `/home` - User home directories
  
  Purpose: I will use this to store personal files and data
  
  Default location:
  ```bash
  /home/rutuja
  ```
- `/root` - Root user's home directory

  Purpose : We check the /root directory when troubleshooting system issues, managing root user configurations, verifying administrative scripts, checking SSH keys.
  
  Admins often keep scripts or logs in /root
  
  ```bash
  sudo ls -l /root
  output:
         backup.sh
         install.log
         deploy.sh
  ```
  
- `/etc` - Configuration files
 
Purpose : /etc directory contains system-wide configuration files. It is used to configure services like SSH, network settings, user accounts, and system applications

1. If SSH is not working, you check:
   ```bash
   sudo vi /etc/ssh/sshd_config
   ```
2. If DNS issue:
   ```bash
   cat /etc/resolv.conf
   ```
3. If user login issue:
   ```bash
   cat /etc/passwd
   ```
4. User related files
   
   ```bash
   /etc/passwd
   /etc/shadow
   /etc/group
   ```
- `/var/log` - Log files (very important for DevOps!)
  
  Purpose : It is used for troubleshooting errors, monitoring system activity, and checking service and security logs.
  
  ```bash
  sudo tail -f /var/log/syslog
  ```
- `/tmp` - Temporary files
  
  Purpose : It is used to store temporary files created by users and applications.

  ```bash
  ls /tmp
  ```
---

**Scenario 1: Service Not Starting** 
```
A web application service called 'myapp' failed to start after a server reboot.
What commands would you run to diagnose the issue?
Write at least 4 commands in order.
```

## Answer

```bash
# Scenario 1: Service Not Starting

Step 1:
Command:
systemctl status myapp

Why:
To check if service is running, stopped, or failed.

Step 2:
Command:
journalctl -u myapp -n 50

Why:
To check logs and see error messages.

Step 3:
Command:
systemctl restart myapp

Why:
To try restarting the service.

```
---

**Scenario 2: High CPU Usage** 
```
Your manager reports that the application server is slow.
You SSH into the server. What commands would you run to identify
which process is using high CPU?
```

## Answer

```bash
Step 1:
Command:
top

Why:
Shows live CPU usage.

Step 2:
Command:
ps aux --sort=-%cpu | head -10

Why:
Shows highest CPU consuming processes.

Step 3:
Command:
kill -9 PID

Why:
Stop problematic process.
```
---
**Scenario 3: Finding Service Logs** 
```
A developer asks: "Where are the logs for the 'docker' service?"
The service is managed by systemd.
What commands would you use?
```
## Answer

```bash
# Scenario 3: Finding Service Logs

Step 1:
systemctl status docker

Why:
Check if docker is running.

Step 2:
journalctl -u docker -n 50

Why:
View docker logs.

Step 3:
journalctl -u docker -f

Why:
View logs in real time.
```
---
**Scenario 4: File Permissions Issue** 
```
A script at /home/user/backup.sh is not executing.
When you run it: ./backup.sh
You get: "Permission denied"

What commands would you use to fix this?
```
## Answer

```bash
# Scenario 4: File Permission Issue

Step 1:
ls -l /home/user/backup.sh

Why:
Check permissions.

Step 2:
chmod +x /home/user/backup.sh

Why:
Add execute permission.

Step 3:
./backup.sh

Why:
Run the script.
```
