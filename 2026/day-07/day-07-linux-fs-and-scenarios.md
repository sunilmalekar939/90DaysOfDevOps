#
1️⃣ / (Root Directory)

The root directory is the starting point of the Linux file system.
All other directories are inside this directory.

Command used:

ls -l /


I would use this when I want to understand overall system structure.

2️⃣ /home

Contains home directories for normal users.

Command used:

ls -l /home


I would use this when checking user files or scripts.

3️⃣ /root

Home directory of the root (admin) user.

Command used:

ls -l /root


I would use this when working as root user.

4️⃣ /etc

Contains system configuration files.

Command used:

ls -l /etc
cat /etc/hostname


I would use this when troubleshooting configuration issues.

5️⃣ /var/log

Stores system and service log files.

Command used:

ls -l /var/log
du -sh /var/log/* 2>/dev/null | sort -h | tail -5


I would use this when debugging service failures.

6️⃣ /tmp

Temporary files stored here.

Command used:

ls -l /tmp


I would use this when testing or storing temporary data.

7️⃣ /bin

Contains essential command binaries like ls, cp, mv.

Command used:

ls -l /bin

8️⃣ /usr/bin

Contains user-level command binaries.

Command used:

ls -l /usr/bin

9️⃣ /opt

Used for optional or third-party applications.

Command used:

ls -l /opt

Part 2: Scenario-Based Practice
Scenario 1: Service Not Starting (myapp)

Step 1:

systemctl status myapp


Why: To check if service is running or failed.

Step 2:

journalctl -u myapp -n 50


Why: To check recent logs of the service.

Step 3:

systemctl is-enabled myapp


Why: To check if service starts on boot.

Step 4:

systemctl list-units --type=service


Why: To verify if service exists.

Scenario 2: High CPU Usage

Step 1:

top


Why: To monitor live CPU usage.

Step 2:

ps aux --sort=-%cpu | head -10


Why: To find top CPU-consuming processes.

Step 3:

kill <PID>


Why: To stop problematic process if needed.

Scenario 3: Finding Service Logs (docker)

Step 1:

systemctl status docker


Why: To check if docker service is active.

Step 2:

journalctl -u docker -n 50


Why: To check recent docker logs.

Step 3:

journalctl -u docker -f


Why: To follow logs in real time.

Scenario 4: File Permission Issue

Step 1:

ls -l /home/user/backup.sh


Why: To check current permissions.

Step 2:

chmod +x /home/user/backup.sh


Why: To add execute permission.

Step 3:

./backup.sh


Why: To verify script execution.

What I Learned

• Linux file system hierarchy is important for troubleshooting.
• Logs are mostly inside /var/log or journalctl for systemd services.
• Always check service status first before debugging.
• File permissions must include execute (x) to run scripts.

#############################
coammnd i run on cli for this practice
 1039  cd /home/jampot/
 1040  ls
 1041  ls -l
 1042  hist
 1043  history 
 1044  ls -l /
 1045  cd bin
 1046  sudo cd bin
 1047  sudo cd var 
 1048  sudo cd var/
 1049  cd /var/
 1050  ls
 1051  ls -l /home
 1052  cd
 1053  ls -l /home
 1054  ls -l /root/
 1055  ls -l /root
 1056  ls -l /root 
 1057  man chwn
 1058  ls -l /var/log | head -5
 1059  ls -l /var/log/
 1060  ls -l /var/log | head -10
 1061  ls -l /var/log | grep cpu
 1062  ls -l /var/log | grep root
 1063  ls -l /var/log | tail -10
 1064  du -sh /var/log/* 2>/dev/null | sort -h | tail -5
 1065  ls -la
 1066  du -sh /var/log/* 2>/dev/null | sort -h | tail -5
 1067  docker ps -a
 1068  docker run hello-world
 1069  docker ps -a
 1070  systemctl status docker
 1071  clear
 1072  docker --version
 1073  sudo docker run hello-world
 1074  sudo docker run -d -p 8080:80 --name mynginx nginx
 1075  sudo docker ps
 1076  curl localhost:8080
 1077  sudo docker stop mynginx
 1078  sudo docker ps -a
 1079  sudo docker start mynginx
 1080  sudo docker logs mynginx
 1081  sudo docker stats
 1082  sudo docker stop mynginx
 1083  sudo docker rm mynginx
 1084  sudo docker rmi nginx
 1085  ls
 1086  cd /usr/bin/
 1087  ls
 1088  cd 
 1089  cd /opt/
 1090  ls
 1091  ls -l /
 1092  ls -l
 1093  cd
 1094  systemctl status myapp
 1095  systemctl status services
 1096  sudo systemctl start docker
 1097  sudo systemctl enable docker
 1098  systemctl status docker
 1099  docker ps -A
 1100  sudo systemctl start docker
 1101  sudo systemctl enable docker
 1102  systemctl status docker
 1103  sudo snap install docker
 1104  docker ps -A
 1105  docker ps -a
 1106  sudo snap install docker
 1107  docker ps -a
 1108  sudo usermod -aG docker jampot
 1109  newgrp docker
 1110  docker ps -a
 1111  /var/run/docker.sock
 1112  ls -l /var/run/docker.sock
 1113  chmod 0777 /var/run/docker.sock 
 1114  sudo chown root:docker /var/run/docker.sock
 1115  sudo snap remove docker
 1116  sudo apt update
 1117  sudo apt install docker.io -y
 1118  sudo systemctl enable docker
 1119  sudo systemctl start docker
 1120  docker ps -a
 1121  docker ps - a
 1122  cat /etc/group | grep docker
 1123  sudo usermod -aG docker $USER
 1124  sudo usermod -aG docker $jampot
 1125  newgrp docker
 1126  clear
 1127  sudo docker run -d --name crash-test busybox sh -c "exit 1"
 1128  sudo docker ps
 1129  sudo docker ps - a
 1130  docker ps -a
 1131  docker rm sudo docker ps
 1132  docker logs crash-test
 1133  docker inspect crash-test
 1134  docker stop $(docker ps -q)
 1135  docker rm $(docker ps -aq)
 1136  docker system prune -a
 1137  clear
 1138  docker ps - a
 1139  hist
 1140  history 
 1141  1128 !
 1142  1129 !
 1143  1130 !
 1144  clear
 1145  ls
 1146  cat ystemctl\ status\ docker 
 1147  docker stop docker system prune -a
 1148  sudo apt remove docker.io -y
 1149  systemctl status docker
 1150  docker ps -a
 1151  docker ps - a
 1152  sudo docker ps -A
 1153  sudo docker ps -a
 1154  hist
 1155  history 
 1156  1149 !
 1157  ! 1149
 1158  clear
 1159  history 
 1160  history | grep docker
 1161  systemctl status docker
 1162  sudo systemctl stop docker
 1163  sudo systemctl stop docker.socket
 1164  sudo systemctl stop docker
 1165  sudo systemctl stop docker.socket
 1166  sudo systemctl unmask docker
 1167  sudo systemctl daemon-reload
 1168  sudo docker ps -A
 1169  sudo docker ps -a
 1170  sudo docker ps - a
 1171  sudo systemctl stop docker
 1172  sudo systemctl stop docker.socket
 1173  ps aux | grep dockerd
 1174  udo kill -9 519584
 1175  sudo pkill dockerd
 1176  sudo systemctl disable docker
 1177  sudo systemctl disable docker.socket
 1178  systemctl status docker
 1179  sudo systemctl status docker
 1180  which docker
 1181  hist
 1182  history
