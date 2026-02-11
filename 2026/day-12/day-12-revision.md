####
# Day 12 – Revision

## Processes & Services Review

Commands rerun today:

- ps aux
- systemctl status docker
- journalctl -u docker -n 20

Observations:
- Verified service status shows active (running)
- Logs help identify recent errors
- PID helps track processes

---

## File Skills Practice

Commands practiced:

- echo >> file
- chmod 640 revision.txt
- chown tokyo revision.txt
- ls -l
- mkdir testdir

Key Learning:
Permissions and ownership together control access.

---

## 5 Commands I’d Use First in an Incident

1. ps aux
2. top
3. systemctl status <service>
4. journalctl -xe
5. ls -l

These quickly show:
- CPU/memory usage
- Service health
- Permission issues

---

## User/Group Sanity Test

Created test user and verified using:

id testuser
ls -l file

Ownership and group verified successfully.

---

# Mini Self-Check

### 1️⃣ Which 3 commands save most time?

- systemctl status → instantly shows service health
- ps aux → shows running processes
- ls -l → shows permissions & ownership

---

### 2️⃣ How do you check if a service is healthy?

1. systemctl status <service>
2. journalctl -u <service> -n 20
3. ps aux | grep <service>

---

### 3️⃣ How to safely change ownership & permissions?

Example:

sudo chown user:group filename
chmod 640 filename

Always verify with:
ls -l filename

---

### 4️⃣ Focus for Next 3 Days

- Improve log analysis
- Understand networking basics
- Practice real-world troubleshooting scenarios

---

# Key Takeaways

- Permissions + ownership are critical in DevOps.
- Logs are your best friend during incidents.
- Small daily practice builds real confidence.

