# Day 07 – Linux File System Hierarchy & Scenario-Based Practice

**Core Directories (Must Know):**
- `/` (root) - The starting point of everything
- 
Purpose: I would use this when I want to navigate the entire file system.

- `/home` - User home directories
- 
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
- 
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
