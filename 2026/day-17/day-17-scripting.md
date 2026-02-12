###
Day 17 – Shell Scripting: Loops, Arguments & Error Handling
🔹 Task 1: For Loop
File: for_loop.sh
#!/bin/bash

for fruit in Apple Banana Mango Orange Grapes
do
    echo "Fruit: $fruit"
done

Output
Fruit: Apple
Fruit: Banana
Fruit: Mango
Fruit: Orange
Fruit: Grapes

File: count.sh
#!/bin/bash

for i in {1..10}
do
    echo $i
done

Output
1
2
3
4
5
6
7
8
9
10

🔹 Task 2: While Loop
File: countdown.sh
#!/bin/bash

read -p "Enter a number: " NUM

while [ $NUM -ge 0 ]
do
    echo $NUM
    NUM=$((NUM - 1))
done

echo "Done!"

Sample Output
Enter a number: 5
5
4
3
2
1
0
Done!

🔹 Task 3: Command-Line Arguments
File: greet.sh
#!/bin/bash

if [ -z "$1" ]; then
    echo "Usage: ./greet.sh <name>"
    exit 1
fi

echo "Hello, $1!"

Run
./greet.sh Sunil


Output:

Hello, Sunil!

File: args_demo.sh
#!/bin/bash

echo "Script name: $0"
echo "Total arguments: $#"
echo "All arguments: $@"

Run
./args_demo.sh DevOps Docker Kubernetes

Output
Script name: ./args_demo.sh
Total arguments: 3
All arguments: DevOps Docker Kubernetes

🔹 Task 4: Install Packages via Script
File: install_packages.sh
#!/bin/bash

# Check if running as root
if [ "$EUID" -ne 0 ]; then
    echo "Please run as root (sudo)."
    exit 1
fi

PACKAGES="nginx curl wget"

for pkg in $PACKAGES
do
    if dpkg -s $pkg &> /dev/null
    then
        echo "$pkg is already installed."
    else
        echo "Installing $pkg..."
        apt install -y $pkg
    fi
done

Run as root
sudo ./install_packages.sh

🔹 Task 5: Error Handling
File: safe_script.sh
#!/bin/bash

set -e   # Exit immediately if a command fails

mkdir /tmp/devops-test || echo "Directory already exists"

cd /tmp/devops-test || { echo "Failed to enter directory"; exit 1; }

touch testfile.txt || echo "Failed to create file"

echo "Script completed successfully."

Explanation

set -e → Exit script if any command fails

|| → Run right-side command if left fails

{ } → Group multiple commands

$EUID → Current user ID

exit 1 → Non-zero exit (error)

🔹 What I Learned

Loops automate repetitive tasks.

Command-line arguments make scripts dynamic.

Error handling prevents silent failures.

Root checks are important for system-level scripts.

Exit codes are critical in automation pipelines.

🔥 Real DevOps Use Cases

Automated server setup

Dependency installation

Health monitoring scripts

CI/CD pre-check scripts

Bulk configuration tasks

🔹 Important Concepts Summary
Concept	Meaning
$1	First argument
$#	Number of arguments
$@	All arguments
$0	Script name
set -e	Exit on error
EUID	Effective user ID
-z	Check empty string
-ne	Not equal
	
&>	Redirect output
🚀 Interview-Ready Understanding

If asked:

Why use set -e?

Answer:
It ensures the script stops immediately when a command fails, preventing inconsistent states in automation workflows.

Why check EUID?

Answer:
To ensure privileged operations (like installing packages) are executed only by root.

Difference between for and while?

Answer:
For loop is ideal for iterating over known items.
While loop is used when condition-based iteration is needed.
