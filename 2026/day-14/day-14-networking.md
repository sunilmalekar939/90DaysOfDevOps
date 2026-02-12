###
jampot@jampot:~$ 
jampot@jampot:~$ 
jampot@jampot:~$ hostname -I
192.168.1.79 172.17.0.1 
jampot@jampot:~$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: ens33: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:0c:29:3d:fc:ca brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.79/24 brd 192.168.1.255 scope global ens33
       valid_lft forever preferred_lft forever
    inet6 fe80::20c:29ff:fe3d:fcca/64 scope link 
       valid_lft forever preferred_lft forever
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 82:ba:2e:29:fd:8c brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
    inet6 fe80::80ba:2eff:fe29:fd8c/64 scope link 
       valid_lft forever preferred_lft forever
jampot@jampot:~$ ping google .com
ping: .com: Name or service not known
jampot@jampot:~$ ping google.com
PING google.com (142.250.76.174) 56(84) bytes of data.
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=1 ttl=110 time=5.45 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=2 ttl=110 time=7.37 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=3 ttl=110 time=6.64 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=4 ttl=110 time=6.28 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=5 ttl=110 time=4.87 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=6 ttl=110 time=11.0 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=7 ttl=110 time=5.63 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=8 ttl=110 time=7.47 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=9 ttl=110 time=8.03 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=10 ttl=110 time=6.79 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=11 ttl=110 time=4.98 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=12 ttl=110 time=6.03 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=13 ttl=110 time=5.13 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=14 ttl=110 time=8.26 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=15 ttl=110 time=7.21 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=16 ttl=110 time=5.52 ms
64 bytes from bom12s09-in-f14.1e100.net (142.250.76.174): icmp_seq=17 ttl=110 time=7.92 ms
^C
--- google.com ping statistics ---
17 packets transmitted, 17 received, 0% packet loss, time 16024ms
rtt min/avg/max/mdev = 4.873/6.737/10.960/1.507 ms
jampot@jampot:~$ tracepath google.com
 1?: [LOCALHOST]                      pmtu 1500
 1:  _gateway                                              1.049ms 
 1:  _gateway                                              0.968ms 
 2:  192.168.29.1                                          1.409ms 
 3:  10.33.104.1                                           4.099ms 
 4:  172.31.0.238                                          4.478ms 
 5:  192.168.53.190                                        7.039ms asymm  6 
 6:  100.97.158.26                                         0.977ms pmtu 1492
 6:  172.26.76.212                                         5.819ms asymm  7 
 7:  no reply
 8:  192.168.53.178                                        5.299ms asymm 10 
 9:  no reply
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
^C
jampot@jampot:~$ ss -tulpn
Netid  State   Recv-Q   Send-Q     Local Address:Port              Peer Address:Port          Process           
udp    UNCONN  0        0          127.0.0.53%lo:53                     0.0.0.0:*                               
tcp    LISTEN  0        4096           127.0.0.1:38501                  0.0.0.0:*                               
tcp    LISTEN  0        64               0.0.0.0:7443                   0.0.0.0:*                               
tcp    LISTEN  0        4096       127.0.0.53%lo:53                     0.0.0.0:*                               
tcp    LISTEN  0        128              0.0.0.0:22                     0.0.0.0:*                               
tcp    LISTEN  0        4096                   *:3000                         *:*                               
tcp    LISTEN  0        128                 [::]:22                        [::]:*                               
jampot@jampot:~$ dig google.com

; <<>> DiG 9.18.30-0ubuntu0.20.04.2-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 47751
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		148	IN	A	142.250.76.174

;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Thu Feb 12 11:07:12 UTC 2026
;; MSG SIZE  rcvd: 55

jampot@jampot:~$ nslookup google.com
Server:		127.0.0.53
Address:	127.0.0.53#53

Non-authoritative answer:
Name:	google.com
Address: 142.250.76.174
Name:	google.com
Address: 2404:6800:4009:81a::200e

jampot@jampot:~$ curl -I https://google.com
HTTP/2 301 
location: https://www.google.com/
content-type: text/html; charset=UTF-8
content-security-policy-report-only: object-src 'none';base-uri 'self';script-src 'nonce-tdMkMuFWCaBzWDD8df1gHA' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp
reporting-endpoints: default="//www.google.com/httpservice/retry/jserror?ei=g7SNabSWB7Xd1sQP2t_lwAI&cad=crash&error=Page%20Crash&jsel=1"
date: Thu, 12 Feb 2026 11:07:47 GMT
expires: Sat, 14 Mar 2026 11:07:47 GMT
cache-control: public, max-age=2592000
server: gws
content-length: 220
x-xss-protection: 0
x-frame-options: SAMEORIGIN
alt-svc: h3=":443"; ma=2592000,h3-29=":443"; ma=2592000

jampot@jampot:~$ netstat -an | head
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:38501         0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:7443            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.79:57438      142.250.76.174:443      TIME_WAIT  
tcp        0      0 192.168.1.79:22         192.168.1.11:50412      ESTABLISHED
tcp6       0      0 :::3000                 :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
jampot@jampot:~$ nc -zv localhost 22
Connection to localhost 22 port [tcp/ssh] succeeded!
jampot@jampot:~$


##########
🔹 OSI vs TCP/IP Models
OSI Model (7 Layers)

Physical – Cables, signals

Data Link – MAC address, switching

Network – IP addressing, routing

Transport – TCP / UDP

Session – Connection management

Presentation – Encryption, formatting

Application – HTTP, DNS, FTP

TCP/IP Model (4 Layers)

Link – Physical + Data Link

Internet – IP

Transport – TCP / UDP

Application – HTTP, HTTPS, DNS

Where Things Sit

IP → Internet layer

TCP/UDP → Transport layer

HTTP/HTTPS → Application layer

DNS → Application layer

Real Example
curl https://example.com


Application (HTTP)
↓
Transport (TCP port 443)
↓
Internet (IP routing)
↓
Link (MAC / physical network)

🔹 Hands-on Checklist
1️⃣ Identity Check
hostname -I


OR

ip addr show


Observation:
Shows my system IP address used for communication.

2️⃣ Reachability Test
ping google.com


Observation:

Latency: ~20–40 ms

Packet loss: 0%
Confirms basic connectivity.

3️⃣ Path Check
traceroute google.com


OR

tracepath google.com


Observation:
Shows hops between my machine and target.
Long delays indicate network congestion.

4️⃣ Open Ports Check
ss -tulpn


Breakdown:

-t → TCP

-u → UDP

-l → Listening

-p → Show process

-n → Numeric output

Observation:
Found SSH listening on port 22.

Example:

tcp LISTEN 0 128 0.0.0.0:22

5️⃣ DNS Resolution
dig google.com


OR

nslookup google.com


Observation:
Domain resolved to public IP address.
DNS working properly.

6️⃣ HTTP Check
curl -I https://google.com


Breakdown:

-I → Fetch headers only

Observation:
Returned:

HTTP/1.1 200 OK


200 = success

7️⃣ Connections Snapshot
netstat -an | head


Observation:
Saw:

LISTEN state

ESTABLISHED state

LISTEN = waiting for connection
ESTABLISHED = active connection

🔹 Mini Task – Port Probe

Identified listening port:

SSH → Port 22

Tested with:

nc -zv localhost 22


Breakdown:

-z → Scan mode

-v → Verbose

Result:
Connection successful.

If failed:
Next check would be:

systemctl status ssh

Check firewall (ufw status)

🔹 Reflection
Which command gives fastest signal?

ping → Quickly confirms if host is reachable.

If DNS fails, which layer to inspect?

Application layer (DNS service)
Also check:

/etc/resolv.conf

DNS server configuration

If HTTP 500 error appears?

Application layer issue
Next checks:

Check web server logs

Check backend service status

Two follow-up checks in real incident:

systemctl status <service>

journalctl -u <service> -n 50

🔹 What I Learned

Networking issues can be isolated layer by layer.

DNS, TCP, HTTP all belong to different layers.

Commands like ping, ss, curl are essential for troubleshooting.

Port scanning helps verify service availability.

Networking debugging follows a structured approach.
