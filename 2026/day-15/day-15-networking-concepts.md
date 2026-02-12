####

Task 1: DNS – How Names Become IPs
What happens when you type google.com in a browser?

Browser checks local DNS cache.

If not found, it queries the DNS resolver (ISP or configured DNS server).

DNS server contacts root → TLD → authoritative server.

The domain name is resolved to an IP address.

Browser connects to that IP using TCP (usually port 443).

DNS Record Types

A – Maps domain to IPv4 address

AAAA – Maps domain to IPv6 address

CNAME – Alias of one domain to another

MX – Mail server record

NS – Name server for the domain

Command
dig google.com

A Record Example Output
google.com.     300    IN    A    142.250.183.14


A Record IP: 142.250.183.14

TTL: 300 seconds

TTL = How long DNS response is cached.

🔹 Task 2: IP Addressing
What is IPv4?

An IPv4 address is a 32-bit numeric address written in dotted decimal format.

Example:

192.168.1.10


Structure:

4 octets

Each octet = 0–255

Total possible addresses ≈ 4.3 billion

Public vs Private IP
Type	Description	Example
Public	Accessible on internet	8.8.8.8
Private	Used inside internal networks	192.168.1.5
Private IP Ranges

10.0.0.0 – 10.255.255.255

172.16.0.0 – 172.31.255.255

192.168.0.0 – 192.168.255.255

Command
ip addr show


Example:

inet 192.168.1.20/24


This is a private IP (192.168.x.x range).

🔹 Task 3: CIDR & Subnetting
What does /24 mean?

It means:

First 24 bits are network bits

Remaining 8 bits are host bits

Subnet mask for /24:

255.255.255.0

Usable Hosts Formula
2^(host bits) - 2


Subtract 2 for:

Network address

Broadcast address

Host Calculation
CIDR	Host Bits	Total IPs	Usable Hosts
/24	8	256	254
/16	16	65,536	65,534
/28	4	16	14
Why Do We Subnet?

Better IP management

Security isolation

Reduce broadcast traffic

Organize networks logically

Subnetting improves performance and security.

🔹 Task 4: Ports – The Doors to Services
What is a Port?

A port is a logical communication endpoint used by applications to send/receive traffic.

IP = House address
Port = Door number

Common Ports
Port	Service
22	SSH
80	HTTP
443	HTTPS
53	DNS
3306	MySQL
6379	Redis
27017	MongoDB
Command
ss -tulpn


Example Output:

tcp LISTEN 0 128 0.0.0.0:22
tcp LISTEN 0 128 127.0.0.1:3306


Mapped Services:

Port 22 → SSH

Port 3306 → MySQL

🔹 Task 5: Putting It Together
Q1: You run
curl http://myapp.com:8080


Concepts involved:

DNS resolves myapp.com to IP

TCP connection to port 8080

HTTP protocol used

IP routing delivers packets

Layers involved:
Application → Transport → Internet → Link

Q2: App cannot reach database at 10.0.1.50:3306

First checks:

Is 10.0.1.50 reachable? (ping)

Is port 3306 open? (ss or nc)

Is MySQL service running?

Firewall blocking?

Same subnet/VPC?

🔹 What I Learned

DNS converts human-readable names into IP addresses.

CIDR determines network size and number of hosts.

Ports identify services running on a machine.

Subnetting improves network efficiency and security.

Troubleshooting requires checking DNS → IP → Port → Service.
