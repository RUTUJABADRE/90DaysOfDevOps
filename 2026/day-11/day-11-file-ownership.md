## Task 2: Basic chown Operations
```bash
touch devops-file.txt
ls -l devops-file.txt 
chown tokyo devops-file.txt 
chown berlin devops-file.txt
ls -l devops-file.txt
```

## Task 3: Basic chgrp Operations
```bash
touch team-notes.txt

ls -l team-notes.txt
-rw-r--r-- 1 root root 0 Mar  1 08:24 team-notes.txt

groupadd  heist-team

chgrp heist-team team-notes.txt

ls -l team-notes.txt
-rw-r--r-- 1 root heist-team 0 Mar  1 08:24 team-notes.txt
```

## Task 4: Combined Owner & Group Change 
```bash
touch project-config.yaml
chown professor:heist-team project-config.yaml 
ls -l project-config.yaml 
mkdir app-logs/
chown berlin:heist-team app-logs/
ls -la app-logs 
```
## Task-5: Recursive Ownership 
```bash
 mkdir -p heist-project/vault
 mkdir -p heist-project/plans
 touch heist-project/vault/gold.txt
 touch heist-project/plans/strategy.conf
 groupadd planners
 chown -R professor:planners heist-project/
 ls -lR heist-project/
```

## Task 6: Practice Challenge
```bash
groupadd vault-team
groupadd tech-team
mkdir bank-heist/ 
touch bank-heist/access-codes.txt
touch bank-heist/blueprints.pdf
touch bank-heist/escape-plan.txt
ls -lr bank-heist/
chown tokyo:vault-team access-codes.txt 
chown berlin:tech-team blueprints.pdf   
chown nairobi:vault-team escape-plan.txt
```
## What I Learned

1. Every file in Linux has an owner and a group that control access permissions.
2. The `chown` command is used to change owner and group, while `chgrp` changes only the group.
3. The `-R` flag allows recursive ownership changes for directories and their contents.
4. Always verify ownership changes using `ls -l`.