#Image for the connectes my aws node from  my laocal machine
<img width="1718" height="1664" alt="image" src="https://github.com/user-attachments/assets/f3271238-8eef-43a3-8492-f7ffa4668b7d" />
####
image for the 
instal ngnix and eable to browse from my machin on http:
<img width="1280" height="481" alt="Screenshot 2026-02-11 at 3 49 30 PM" src="https://github.com/user-attachments/assets/c5be9312-5231-486b-a573-c5ffe5db26be" />

####
Logs file pulled from the AWs sever 
Last login: Wed Feb 11 15:08:24 on ttys001
sunilmalekar@Ankitas-MacBook-Air ~ % scp -i aws-server-key.pem ubuntu@174.129.132.173:~/nginx-logs.txt .
Warning: Identity file aws-server-key.pem not accessible: No such file or directory.
ubuntu@174.129.132.173: Permission denied (publickey).
scp: Connection closed
sunilmalekar@Ankitas-MacBook-Air ~ % ls -l   
total 0
drwx------@   4 sunilmalekar  staff   128 Jan 24 11:44 Applications
drwx------+   7 sunilmalekar  staff   224 Jan 30 22:32 Desktop
drwx------+   7 sunilmalekar  staff   224 Jan  4 01:45 Documents
drwx------+ 125 sunilmalekar  staff  4000 Feb 11 15:33 Downloads
drwx------@  88 sunilmalekar  staff  2816 Apr 26  2025 Library
drwx------    5 sunilmalekar  staff   160 Apr  6  2025 Movies
drwx------+   4 sunilmalekar  staff   128 Apr  6  2025 Music
drwx------+   6 sunilmalekar  staff   192 Jun 23  2025 Pictures
drwxr-xr-x+   4 sunilmalekar  staff   128 Apr  6  2025 Public
sunilmalekar@Ankitas-MacBook-Air ~ % cd Downloads 
sunilmalekar@Ankitas-MacBook-Air Downloads % scp -i aws-server-key.pem ubuntu@174.129.132.173:~/nginx-logs.txt .
nginx-logs.txt                                                                   100% 1062     1.7KB/s   00:00    
sunilmalekar@Ankitas-MacBook-Air Downloads %

##########################################################
# SSH Connection
chmod 400 my-key.pem
ssh -i my-key.pem ubuntu@<public-ip>

# Update system
sudo apt update && sudo apt upgrade -y

# Install Docker
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker

# Install Nginx
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx

# Check status
sudo systemctl status nginx

# View logs
sudo cat /var/log/nginx/access.log
sudo cp /var/log/nginx/access.log ~/nginx-logs.txt

# Download logs
scp -i my-key.pem ubuntu@<public-ip>:~/nginx-logs.txt .


