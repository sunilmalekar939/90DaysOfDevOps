##
Files Created

devops.txt

notes.txt

script.sh

project/ (directory)

Permission Changes

Before:

-rw-r--r-- script.sh


After:

-rwxr-xr-x script.sh


devops.txt:

Removed write permission (read-only)


notes.txt:

Changed to 640 → rw-r-----


project directory:

755 → rwxr-xr-x

Commands Used
touch devops.txt
echo "text" > notes.txt
vim script.sh
cat notes.txt
head -n 5 /etc/passwd
tail -n 5 /etc/passwd
chmod +x script.sh
chmod a-w devops.txt
chmod 640 notes.txt
mkdir project
chmod 755 project

What I Learned

How Linux file permissions work (r=4, w=2, x=1)

How to modify permissions using chmod

Difference between file and directory permissions

Why execute permission is required for scripts

How permission errors appear in real scenarios
