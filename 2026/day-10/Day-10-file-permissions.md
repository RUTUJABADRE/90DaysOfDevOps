# Day 10 – File Permissions & File Operations Challenge

---

## Task-1

```bash
# create file
touch devops.txt

#create file with writing some content
cat > notes.txt

#create shell script using vim command
vim script.sh

# To verify changes
ls -l
```
![image alt](https://github.com/RUTUJABADRE/90DaysOfDevOps/blob/master/2026/day-10/task-1.png?raw=true)

## Task-2

```bash
#View file
cat notes.txt

#check file content in readonly mode
vim -R script.sh 

#to see first 5 line of file
head -n 5 /etc/passwd

#To see last five line of file
tail -n 5 /etc/passwd
```
![image alt](https://github.com/RUTUJABADRE/90DaysOfDevOps/blob/master/2026/day-10/task-2.png?raw=true)

## Task-3

```bash
#To check file permission 
ls -l notes.txt script.txt devops.txt

Owner → read, write
Group → read only
Others → read only
```
![image alt](https://github.com/RUTUJABADRE/90DaysOfDevOps/blob/master/2026/day-10/task-3.png?raw=true)

## Task-4

```bash
#Make script.sh executable
chmod +x script.sh 
./script.sh 

#Set devops.txt to read-only
chmod 444 devops.txt 

#Set notes.txt to 640
chmod 640 notes.txt 

#Create directory project/ with permissions 755
mkdir project
chmod 755 project/

#To verify Changes
ls -l
```
![image alt](https://github.com/RUTUJABADRE/90DaysOfDevOps/blob/master/2026/day-10/task-4.png?raw=true)

## Task-5

```bash
#Try writing to a read-only file 
$ echo "hello" >> devops.txt
sh: 1: cannot create devops.txt: Permission denied

#Try executing a file without execute permission
$ ./devops.txt
sh: 2: ./devops.txt: Permission denied
```
![image alt](https://github.com/RUTUJABADRE/90DaysOfDevOps/blob/master/2026/day-10/task-5.png?raw=true)
