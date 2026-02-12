#####
🔹 1️⃣ Create Virtual Disk
dd if=/dev/zero of=/tmp/disk1.img bs=1M count=1024

Command Breakdown:

dd → Low-level data copy tool

if= → Input file

/dev/zero → Special device that provides empty (zero) data

of= → Output file

/tmp/disk1.img → File acting as virtual disk

bs=1M → Block size (1 Megabyte per block)

count=1024 → Number of blocks (1024 × 1MB = 1GB)

👉 Creates a 1GB virtual disk file.

losetup -fP /tmp/disk1.img

Breakdown:

losetup → Attach file as loop device

-f → Find free loop device

-P → Scan for partitions

👉 Attaches disk file as /dev/loop0

losetup -a


-a → Show all active loop devices

🔹 2️⃣ Check Current Storage
lsblk


lsblk → List block devices (disks, partitions)

pvs


Shows Physical Volumes

vgs


Shows Volume Groups

lvs


Shows Logical Volumes

df -h


df → Disk free space

-h → Human readable (MB/GB)

🔹 3️⃣ Create Physical Volume
pvcreate /dev/loop0


pvcreate → Converts disk into LVM Physical Volume

/dev/loop0 → Target disk

👉 First LVM layer

🔹 4️⃣ Create Volume Group
vgcreate devops-vg /dev/loop0


vgcreate → Create Volume Group

devops-vg → Name of Volume Group

/dev/loop0 → Physical Volume used

👉 VG = Storage Pool

🔹 5️⃣ Create Logical Volume
lvcreate -L 500M -n app-data devops-vg

Breakdown:

lvcreate → Create Logical Volume

-L 500M → Size = 500 MB

-n app-data → Name of Logical Volume

devops-vg → Volume Group used

👉 LV = Usable partition

🔹 6️⃣ Format Logical Volume
mkfs.ext4 /dev/devops-vg/app-data


mkfs → Make filesystem

.ext4 → Filesystem type

/dev/devops-vg/app-data → Logical Volume path

👉 Prepares volume for mounting.

🔹 7️⃣ Create Mount Directory
mkdir -p /mnt/app-data


mkdir → Create directory

-p → Create parent directories if needed

/mnt/app-data → Mount point

🔹 8️⃣ Mount Volume
mount /dev/devops-vg/app-data /mnt/app-data


mount → Attach filesystem

First path → Source device

Second path → Mount location

🔹 9️⃣ Extend Logical Volume
lvextend -L +200M /dev/devops-vg/app-data


lvextend → Increase LV size

-L +200M → Add 200MB

+ → Increase (without + it sets exact size)

resize2fs /dev/devops-vg/app-data


resize2fs → Resize ext2/3/4 filesystem

Required after lvextend

👉 Without resize2fs, filesystem won’t use new space.

🧠 LVM Architecture (Interview Important)

Disk
↓
Physical Volume (PV)
↓
Volume Group (VG)
↓
Logical Volume (LV)
↓
Filesystem
↓
Mount Point

❌ Mistakes I Made During Lab

❌ Ran LVM commands without sudo
→ LVM requires root privileges

❌ Created LV inside ubuntu-vg but tried formatting /dev/devops-vg/app-data
→ Wrong VG name

❌ Tried creating directory in /mnt without sudo
→ Permission denied

❌ Tried mounting without sudo
→ Only root can mount filesystems

🎯 Interview Questions You Should Answer
Q1: Why use LVM instead of normal partitions?

Because LVM allows dynamic resizing without downtime.

Q2: What happens if you forget resize2fs?

Filesystem will not use the extended space.

Q3: Can you shrink LVM?

Yes, but risky and requires unmounting.

Q4: Difference between PV and VG?

PV = physical disk
VG = storage pool of one or more PVs

🔥 Real DevOps Production Example

If database disk is full:

lvextend -L +20G /dev/prod-vg/db-data
resize2fs /dev/prod-vg/db-data


No downtime needed.
