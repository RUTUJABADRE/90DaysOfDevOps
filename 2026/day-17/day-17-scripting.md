## Task 1: For Loop
```bash

#!/bin/bash
for fruits in apple banana orange graphs guava
do
        echo "$fruits"
done

```

```bash

#!/bin/bash
for i in {1..10}
do
        echo "$i"
done

```

output
![alt text](/images/task-1.png)

## Task 2: While loop

```bash

#!/bin/bash

read -p "Enter a number" num
while [ "$num" -ge 0 ]
do
        echo "$num"
        num=$((num - 1))
done
echo "DONE!"

```
output
![alt text](/images/task-2.png)


## Task 3: Command-Line Arguments

```bash
#!/bin/bash

if [ -z "$1" ]; then
        echo "Usage: ./greet.sh <name>"
else
        echo "Hello, $1!"
fi

```

```bash

echo "Script name: $0"
echo "Total number of arguments: $#"
echo "All arguments: $@"

```
output
![alt text](/images/task-3.png)

## Task 4: Install Packages via Script

```bash
#!/bin/bash

packages=( nginx curl wget )

for pkg in "${packages[@]}"
do
        if dpkg -s "$pkg" &> /dev/null; then
                echo "$pkg is already installed"
        else
                echo "$pkg is not installed ..Installing......"
                sudo apt update -y
                sudo apt install -y "$pkg"
                echo "$pkg installed successfully"

        fi
done

```
output
![alt text](/images/task-4.png)

## Task 5 : 

```bash
#!/bin/bash

set -e   # exit immediately if any command fails

mkdir -p /tmp/devops-test || echo "Failed to create directory"

cd /tmp/devops-test || echo "Failed to change directory"

touch test_file.txt || echo "Failed to create file"

echo "All steps completed successfully"

```

output
![alt text](/images/task-5.png)