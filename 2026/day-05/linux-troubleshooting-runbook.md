
###### As part of this activity, I set up a Docker container locally and used it to perform hands-on troubleshooting actions 
&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&


###### docker ps
CONTAINER ID   IMAGE                                           COMMAND             CREATED          STATUS                            PORTS     NAMES
471be90d71b0   techconnectengineering/gateway-9.0.0:173873   "./entrypoint.sh"   15 minutes ago   Restarting (127) 50 seconds ago          



------------------------

docker stats telephony-ics
ONTAINER ID   NAME            CPU %     MEM USAGE / LIMIT   MEM %     NET I/O   BLOCK I/O   PIDS
471be90d71b0   telephony-ics   0.00%     0B / 0B             0.00%     0B / 0B   0B / 0B     0



-----------------------
# docker inspect telephony-ics | grep -i pid
"Pid": 0,
"PidMode": "",
"PidsLimit": null,


........................            ...........................
# docker logs telephony-ics --tail 50
jampot@ice-support:~/sunil/375/opt/ice-agent$ docker logs telephony-ics --tail 50
--> ice-gw exit status: 127
Starting external ice-agent for gateway: {sip}
Agent log level:   {warning}
Server group code: {ARN}
./entrypoint.sh: line 66: /home/gateway/ice/agent/agent: No such file or directory
--> ice-gw pipeline pid: 13
./entrypoint.sh: line 82: ice/bin/ice-gw: No such file or directory
--> ice-gw exit status: 127
Starting external ice-agent for gateway: {sip}
Agent log level:   {warning}
Server group code: {ARN}
./entrypoint.sh: line 66: /home/gateway/ice/agent/agent: No such file or directory
--> ice-gw pipeline pid: 13
./entrypoint.sh: line 82: ice/bin/ice-gw: No such file or directory
--> ice-gw exit status: 127
Starting external ice-agent for gateway: {sip}
Agent log level:   {warning}
Server group code: {ARN}
./entrypoint.sh: line 66: /home/gateway/ice/agent/agent: No such file or directory
--> ice-gw pipeline pid: 13
./entrypoint.sh: line 82: ice/bin/ice-gw: No such file or directory
--> ice-gw exit status: 127
Starting external ice-agent for gateway: {sip}
Agent log level:   {warning}
Server group code: {ARN}
./entrypoint.sh: line 66: /home/gateway/ice/agent/agent: No such file or directory
--> ice-gw pipeline pid: 13
./entrypoint.sh: line 82: ice/bin/ice-gw: No such file or directory
--> ice-gw exit status: 127
Starting external ice-agent for gateway: {sip}
Agent log level:   {warning}
Server group code: {ARN}
./entrypoint.sh: line 66: /home/gateway/ice/agent/agent: No such file or directory
--> ice-gw pipeline pid: 13
./entrypoint.sh: line 82: ice/bin/ice-gw: No such file or directory
--> ice-gw exit status: 127
Starting external ice-agent for gateway: {sip}
Agent log level:   {warning}
Server group code: {ARN}
./entrypoint.sh: line 66: /home/gateway/ice/agent/agent: No such file or directory
--> ice-gw pipeline pid: 13
./entrypoint.sh: line 82: ice/bin/ice-gw: No such file or directory
--> ice-gw exit status: 127
Starting external ice-agent for gateway: {sip}
Agent log level:   {warning}
Server group code: {ARN}
./entrypoint.sh: line 66: /home/gateway/ice/agent/agent: No such file or directory
--> ice-gw pipeline pid: 13
./entrypoint.sh: line 82: ice/bin/ice-gw: No such file or directory
--> ice-gw exit status: 127




----------------------------------------
# docker exec -it telephony-ics ps aux
Error response from daemon: Container 471be90d71b037ce451802fec8e46d73a7f94e583d91195bf636191cc1f4628c is restarting, wait until the container is running
jampot@ice-support:~/sunil/375/opt/ice-agent$ 



---------------------------------------
# jampot@ice-support:~/sunil/375/opt/ice-agent$ df -h
docker system df
Filesystem                         Size  Used Avail Use% Mounted on
tmpfs                              387M  1.9M  386M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   39G  8.8G   28G  25% /
tmpfs                              1.9G     0  1.9G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
/dev/sda2                          2.0G  192M  1.6G  11% /boot
tmpfs                              387M   12K  387M   1% /run/user/1000
TYPE            TOTAL     ACTIVE    SIZE      RECLAIMABLE
Images          1         1         291.2MB   0B (0%)
Containers      1         1         0B        0B
Local Volumes   0         0         0B        0B
Build Cache     0         0         0B        0B
jampot@ice-support:~/sunil/375/opt/ice-agent$ 
-------------------------------------
hjh


