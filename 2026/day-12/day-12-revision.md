
- **Processes & services:** rerun 2 commands from Day 04/05 (e.g., `ps`, `systemctl status`, `journalctl -u <service>`); jot what you observed today. 

```bash
ps aux
systemctl status ssh
journalctl -u ssh
```

- **File skills:** practice 3 quick ops from Days 06–11 (e.g., `echo >>`, `chmod`, `chown`, `ls -l`, `cp`, `mkdir`). 

```bash
echo "hello linux" >> test.txt #appends text to a file.
chmod 644 test.txt #changes file permissions.
ls -l  #shows detailed file information including permissions.
mkdir practice_folder #creates directories.
cp test.txt practice_folder/. #copies files to another location.
```

- **Cheat sheet refresh:** skim your Day 03 commands—highlight 5 you’d reach for first in an incident. 

```bash
top #identify high CPU usage processes
ps aux #list running processes
df -h #check disk space
free -m #check memory usage
systemctl status <service> #verify service health

```

## Mini Self-Check (write short answers in `day-12-revision.md`)
1) Which 3 commands save you the most time right now, and why?  

ps aux – quickly shows all running processes.
systemctl status – checks if a service is running or failing.
df -h – helps identify disk space issues quickly.

2) How do you check if a service is healthy? List the exact 2–3 commands you’d run first
systemctl status nginx
ps aux | grep nginx
journalctl -u nginx

3) How do you safely change ownership and permissions without breaking access? Give one example command.
sudo chown user1:user1 file.txt
chmod 644 file.txt