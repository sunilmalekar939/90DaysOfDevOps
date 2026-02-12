####
🔹 Task 1: Your First Script
File: hello.sh
#!/bin/bash

echo "Hello, DevOps!"

Make it executable
chmod +x hello.sh

Run it
./hello.sh

Output
Hello, DevOps!

What happens if you remove the shebang?

If the shebang (#!/bin/bash) is removed:

The script may still run in interactive bash.

But if executed from another shell (like sh), it may fail.

The shebang tells the OS which interpreter to use.

👉 Best practice: Always include shebang.

🔹 Task 2: Variables
File: variables.sh
#!/bin/bash

NAME="Sunil"
ROLE="DevOps Engineer"

echo "Hello, I am $NAME and I am a $ROLE"

Run
chmod +x variables.sh
./variables.sh

Output
Hello, I am Sunil and I am a DevOps Engineer

Single vs Double Quotes

Example:

echo '$NAME'
echo "$NAME"


Output:

$NAME
Sunil


Difference:

Single quotes → No variable expansion

Double quotes → Variable expansion happens

🔹 Task 3: User Input with read
File: greet.sh
#!/bin/bash

read -p "Enter your name: " NAME
read -p "Enter your favourite tool: " TOOL

echo "Hello $NAME, your favourite tool is $TOOL"

Run
chmod +x greet.sh
./greet.sh

Sample Output
Enter your name: Sunil
Enter your favourite tool: Docker
Hello Sunil, your favourite tool is Docker

🔹 Task 4: If-Else Conditions
File: check_number.sh
#!/bin/bash

read -p "Enter a number: " NUM

if [ $NUM -gt 0 ]; then
    echo "Number is Positive"
elif [ $NUM -lt 0 ]; then
    echo "Number is Negative"
else
    echo "Number is Zero"
fi

File: file_check.sh
#!/bin/bash

read -p "Enter filename: " FILE

if [ -f "$FILE" ]; then
    echo "File exists."
else
    echo "File does not exist."
fi


-f checks if file exists and is regular file.

🔹 Task 5: Combine It All
File: server_check.sh
#!/bin/bash

SERVICE="sshd"

read -p "Do you want to check the status of $SERVICE? (y/n): " ANSWER

if [ "$ANSWER" == "y" ]; then
    systemctl is-active --quiet $SERVICE
    
    if [ $? -eq 0 ]; then
        echo "$SERVICE is running."
    else
        echo "$SERVICE is NOT running."
    fi
else
    echo "Skipped."
fi

What This Script Does

Stores service name in variable

Asks user for confirmation

Checks service status

Uses exit code ($?)

Prints readable result

🔹 What I Learned

Shebang defines which interpreter executes the script.

Variables store reusable values.

read allows interactive input.

If-else enables decision-making logic.

Exit codes ($?) are critical in automation.

Shell scripting is foundation of DevOps automation.

🔥 Real DevOps Use Cases

Automating deployments

Health check scripts

Log monitoring

Backup scripts

Service monitoring

🚀 Commands Used in This Lab
chmod +x filename.sh
./filename.sh
read
echo
if [ condition ]; then
systemctl is-active
$?
