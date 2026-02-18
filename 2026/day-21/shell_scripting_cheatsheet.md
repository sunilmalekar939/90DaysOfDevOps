Shell Scripting Cheat Sheet

A practical reference guide for daily DevOps usage.

🔹 Quick Reference Table
Topic	Key Syntax	Example
Variable	VAR="value"	NAME="DevOps"
Argument	$1, $2	./script.sh arg1
If	if [ condition ]; then	if [ -f file ]; then
For Loop	for i in list; do	for i in 1 2 3; do
Function	name() { ... }	greet() { echo "Hi"; }
Grep	grep pattern file	grep -i "error" log.txt
Awk	awk '{print $1}' file	awk -F: '{print $1}' /etc/passwd
Sed	sed 's/old/new/g' file	sed -i 's/foo/bar/g' config.txt
1️⃣ Basics
Shebang

Defines interpreter for script.

#!/bin/bash

Running a Script
chmod +x script.sh
./script.sh
bash script.sh

Comments
# Single line comment

echo "Hello"  # Inline comment

Variables
NAME="Sunil"
echo $NAME
echo "$NAME"
echo '$NAME'


Double quotes expand variable, single quotes do not.

Reading User Input
read USERNAME
echo "Hello $USERNAME"

Command-Line Arguments
echo $0   # Script name
echo $1   # First argument
echo $#   # Number of arguments
echo $@   # All arguments
echo $?   # Last command exit code

2️⃣ Operators & Conditionals
String Comparisons
[ "$A" = "$B" ]
[ "$A" != "$B" ]
[ -z "$A" ]   # Empty
[ -n "$A" ]   # Not empty

Integer Comparisons
[ "$A" -eq 10 ]
[ "$A" -ne 5 ]
[ "$A" -lt 5 ]
[ "$A" -gt 5 ]
[ "$A" -le 5 ]
[ "$A" -ge 5 ]

File Tests
[ -f file ]   # Regular file
[ -d dir ]    # Directory
[ -e file ]   # Exists
[ -r file ]   # Readable
[ -w file ]   # Writable
[ -x file ]   # Executable
[ -s file ]   # Not empty

if / elif / else
if [ condition ]; then
    echo "True"
elif [ condition ]; then
    echo "Else if"
else
    echo "False"
fi

Logical Operators
cmd1 && cmd2
cmd1 || cmd2
! cmd

Case Statement
case $VAR in
    start) echo "Starting";;
    stop) echo "Stopping";;
    *) echo "Invalid";;
esac

3️⃣ Loops
For Loop (List)
for i in 1 2 3; do
    echo $i
done

For Loop (C Style)
for ((i=0; i<5; i++)); do
    echo $i
done

While Loop
while [ $COUNT -lt 5 ]; do
    echo $COUNT
    ((COUNT++))
done

Until Loop
until [ $COUNT -gt 5 ]; do
    echo $COUNT
    ((COUNT++))
done

Loop Control
break
continue

Loop Over Files
for file in *.log; do
    echo $file
done

Loop Over Command Output
cat file.txt | while read line; do
    echo $line
done

4️⃣ Functions
Define Function
greet() {
    echo "Hello"
}

Call Function
greet

Function Arguments
greet() {
    echo "Hello $1"
}
greet Sunil

Return Values
myfunc() {
    return 1
}

echo $?   # Exit code


Use echo to return strings.

Local Variables
myfunc() {
    local VAR="test"
}

5️⃣ Text Processing Commands
grep
grep "error" file
grep -i "error" file
grep -r "error" .
grep -c "error" file
grep -n "error" file
grep -v "info" file
grep -E "error|fail" file

awk
awk '{print $1}' file
awk -F: '{print $1}' /etc/passwd
awk 'NR==1' file
awk 'BEGIN {print "Start"} {print $1} END {print "End"}' file

sed
sed 's/old/new/g' file
sed -i 's/foo/bar/g' file
sed '2d' file

cut
cut -d',' -f1 file.csv

sort
sort file
sort -n file
sort -r file
sort -u file

uniq
uniq file
uniq -c file

tr
tr 'a-z' 'A-Z'
tr -d '\n'

wc
wc -l file
wc -w file
wc -c file

head / tail
head -n 10 file
tail -n 10 file
tail -f log.txt

6️⃣ Useful One-Liners
Delete Files Older Than 7 Days
find /path -type f -mtime +7 -delete

Count Lines in All .log Files
wc -l *.log

Replace String in Multiple Files
sed -i 's/old/new/g' *.txt

Check if Service is Running
systemctl is-active nginx

Disk Usage Alert
df -h | awk '$5 > 80 {print $0}'

Tail Log and Filter Errors
tail -f app.log | grep --line-buffered "ERROR"

7️⃣ Error Handling & Debugging
Exit Codes
echo $? 
exit 0
exit 1


0 = success, non-zero = failure.

Exit on Error
set -e

Unset Variable Error
set -u

Pipe Fail Detection
set -o pipefail

Debug Mode
set -x

Trap Cleanup
trap 'echo "Cleaning up"; rm -f temp.txt' EXIT
