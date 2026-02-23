# Day 08 – Cloud Server Setup: Docker, Nginx & Web Deployment

## Task
Today's goal is to **deploy a real web server on the cloud** and learn practical server management.

You will:
- Launch a cloud instance (AWS EC2 or Utho)
- Connect via SSH
- Install Nginx
- Configure security groups for web access (port 80 by default for nginx)
- Extract and save logs to a file
- Verify your webpage is accessible from the internet
---

## Answers

**Command Used**

```bash
1. ssh connect command
cd /Download - to go inside folder where .pem key file exists
2. Give read permission to pem file
chmod 400 <mykey.pem>
3. SSH command to connect to EC2 instance
ssh -i <mykey.pem> ubuntu@public-ip
4. command to download nginx
sudo apt install nginx
5. to check service is running or not
systemctl status nginx
```
***Command to download log file locally***

```bash
1. Locate log file on server then copy it to user directory
   - cd /var/log/nginx
   - ls -l
   - cp /var/log/nginx/access.log /home/ubuntu/nginx-access.log
2. copy locally from server
   - exit from server
   - scp -i your-key.pem ubuntu@<your-instance-ip>:~/nginx-access.log .

```
