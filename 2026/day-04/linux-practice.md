# Day 04 – Linux Practice: Processes and Services

## 1️⃣ Process Checks
### Command 1: List all running processes
```bash
1.ps aux
outpot:
jampot@jampot:~$ ps -aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.1 168740 12864 ?        Ss   20:30   0:03 /sbin/init maybe-ubiquity
root           2  0.0  0.0      0     0 ?        S    20:30   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        I<   20:30   0:00 [rcu_gp]
root           4  0.0  0.0      0     0 ?        I<   20:30   0:00 [rcu_par_gp]
root           6  0.0  0.0      0     0 ?        I<   20:30   0:00 [kworker/0:0H-kblockd]
root           8  0.0  0.0      0     0 ?        I<   20:30   0:00 [mm_percpu_wq]
root           9  0.0  0.0      0     0 ?        S    20:30   0:00 [ksoftirqd/0]
root          10  0.0  0.0      0     0 ?        I    20:30   0:04 [rcu_sched]
root          11  0.0  0.0      0     0 ?        S    20:30   0:00 [migration/0]
root          12  0.0  0.0      0     0 ?        S    20:30   0:00 [idle_inject/0]
root          13  0.0  0.0      0     0 ?        I    20:30   0:02 [kworker/0:1-events]
root          14  0.0  0.0      0     0 ?        S    20:30   0:00 [cpuhp/0]
root          15  0.0  0.0      0     0 ?        S    20:30   0:00 [cpuhp/1]
............................................................
2.Check a specific process (example: sshd)
pgrep -l sshd

Output:1089 sshd
4495 sshd
4585 sshd
5125 sshd
5214 sshd
7768 sshd
7896 sshd
................................................................
Command 3 (Optional): Interactive process viewer
top -n 1
Output:
jampot@jampot:~$ top -n 1

top - 22:42:35 up  2:12,  4 users,  load average: 0.00, 0.00, 0.00
Tasks: 226 total,   1 running, 225 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  1.6 sy,  0.0 ni, 98.4 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   7945.5 total,   6159.1 free,    255.3 used,   1531.0 buff/cache
MiB Swap:   4096.0 total,   4096.0 free,      0.0 used.   7413.7 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                      
   8097 jampot    20   0   11160   4040   3232 R   6.7   0.0   0:00.01 top                                                                                                          
      1 root      20   0  168740  12864   8348 S   0.0   0.2   0:03.62 systemd                                                                                                      
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kthreadd                                                                                                     
      3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp                                                                                                       
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par_gp                                                                                                   
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-kblockd   
.....................................................................................
2️⃣ Service Checks
Command 4: Inspect a service (example: ssh)
systemctl status ssh


Output:
~$ systemctl status ssh
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
     Active: active (running) since Wed 2026-01-28 20:28:08 UTC; 2h 15min ago
       Docs: man:sshd(8)
             man:sshd_config(5)
   Main PID: 1089 (sshd)
      Tasks: 1 (limit: 9419)
     Memory: 8.9M
     CGroup: /system.slice/ssh.service
             └─1089 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups
..........................................................................................
Command 5: List active services
systemctl list-units --type=service --state=active

output:

jampot@jampot:~$ systemctl list-units --type=service --state=active
  UNIT                                 LOAD   ACTIVE SUB     DESCRIPTION                                                                  
  accounts-daemon.service              loaded active running Accounts Service                                                             
  apparmor.service                     loaded active exited  Load AppArmor profiles                                                       
  apport.service                       loaded active exited  LSB: automatic crash report generation                                       
  atd.service                          loaded active running Deferred execution scheduler                                                 
  blk-availability.service             loaded active exited  Availability of block devices                                                
  cloud-config.service                 loaded active exited  Apply the settings specified in cloud-config                                 
  cloud-final.service                  loaded active exited  Execute cloud user/final scripts                                             
  cloud-init-local.service             loaded active exited  Initial cloud-init job (pre-networking)                                      
  cloud-init.service                   loaded active exited  Initial cloud-init job (metadata service crawler)                            
  console-setup.service                loaded active exited  Set console font and keymap
..............................................................................
3️⃣ Log Checks
Command 6: View logs for a service
journalctl -u ssh -n 50
Output:
jampot@jampot:~$ journalctl -u ssh -n 50
-- Logs begin at Sun 2025-04-13 04:58:24 UTC, end at Wed 2026-01-28 22:48:21 UTC. --
Apr 16 09:04:59 jampot sshd[2944670]: Accepted password for jampot from 192.168.0.42 port 40418 ssh2
Apr 16 09:04:59 jampot sshd[2944670]: pam_unix(sshd:session): session opened for user jampot by (uid=0)
-- Reboot --
Jan 28 20:28:00 jampot systemd[1]: Starting OpenBSD Secure Shell server...
Jan 28 20:28:08 jampot sshd[1089]: Server listening on 0.0.0.0 port 22.
Jan 28 20:28:08 jampot systemd[1]: Started OpenBSD Secure Shell server.
Jan 28 20:28:08 jampot sshd[1089]: Server listening on :: port 22.
Jan 28 20:39:56 jampot sshd[4495]: Accepted password for jampot from 192.168.0.8 port 61786 ssh2
Jan 28 20:39:56 jampot sshd[4495]: pam_unix(sshd:session): session opened for user jampot by (uid=0)
Jan 28 21:00:24 jampot sshd[5125]: Accepted password for jampot from 192.168.0.87 port 50132 ssh2
Jan 28 21:00:24 jampot sshd[5125]: pam_unix(sshd:session): session opened for user jampot by (uid=0)
Jan 28 22:35:31 jampot sshd[7768]: Accepted password for jampot from 192.168.1.11 port 49974 ssh2
Jan 28 22:35:31 jampot sshd[7768]: pam_unix(sshd:session): session opened for user jampot by (uid=0)
jampot@jampot:~$
.............................................................................
Command 7: Check last 50 lines of a log file
tail -n 50 /var/log/syslog

Output:
tail -n 50 /var/log/syslog
Jan 28 23:43:58 jampot multipathd[724]: sda: failed to get sgio uid: No such file or directory
Jan 28 23:44:03 jampot multipathd[724]: sda: add missing path
Jan 28 23:44:03 jampot multipathd[724]: sda: failed to get udev uid: Invalid argument
Jan 28 23:44:03 jampot multipathd[724]: sda: failed to get sysfs uid: Invalid argument
Jan 28 23:44:03 jampot multipathd[724]: sda: failed to get sgio uid: No such file or directory
Jan 28 23:44:08 jampot multipathd[724]: sda: add missing path
Jan 28 23:44:08 jampot multipathd[724]: sda: failed to get udev uid: Invalid argument
Jan 28 23:44:08 jampot multipathd[724]: sda: failed to get sysfs uid: Invalid argument
Jan 28 23:44:08 jampot multipathd[724]: sda: failed to get sgio uid: No such file or directory
Jan 28 23:44:13 jampot multipathd[724]: sda: add missing path
Jan 28 23:44:13 jampot multipathd[724]: sda: failed to get udev uid: Invalid argument
Jan 28 23:44:13 jampot multipathd[724]: sda: failed to get sysfs uid: Invalid argument
Jan 28 23:44:13 jampot multipathd[724]: sda: failed to get sgio uid: No such file or directory
.....................................................................

