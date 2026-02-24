# Day 09 – Linux User & Group Management Challenge

## Task
Today's goal is to **practice user and group management** by completing hands-on challenges.

Figure out how to:
- Create users and set passwords
- Create groups and assign users
- Set up shared directories with group permissions

---

## Answers

***Command used in this task***

- Task 1
  
```bash
#To add and verfy users

useradd -m tokyo
useradd -m berlin
useradd -m professor
cat /etc/passwd

#to set password

passwd tokyo
passwd berlin
passwd professor

```
- Task 2

```bash
#To add group

groupadd developers
groupadd admins
cat /etc/group
```
- Task 3

```bash
# To assign users to group

usermod -aG developers tokyo
usermod -aG developers berlin
usermod -aG admins berlin
usermod -aG admins professor

#Command to verify group users

groups tokyo
groups berlin
groups professor 

```
- Task 4

```bash
#to create directory

mkdir /opt/dev-project

#change group owner of directory

chgrp developers dev-project/

# Modify permission of user,group and other who wants to access this directory
chmod 775 /opt/dev-project

#Test by creating files as `tokyo` and `berlin`

su - tokyo
touch /opt/dev-project/tokyo.txt
exit
ls -l /opt/dev-project/

```
- Task 5

```bash

useradd -m nairobi
groupadd project-team
cat /etc/group
usermod -aG project-team nairobi
usermod -aG project-team tokyo  
mkdir /opt/team-workspace
ls -l /opt/
chgrp project-team /opt/team-workspace
ls -l /opt/
chmod 775 /opt/team-workspace/
ls -l /opt/team-workspace 

```
