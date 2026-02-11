#
Users & Groups Created

Users:

tokyo

berlin

professor

nairobi

Groups:

developers

admins

project-team

Group Assignments

tokyo → developers, project-team

berlin → developers, admins

professor → admins

nairobi → project-team

Directories Created

/opt/dev-project (Group: developers, Permission: 775)

/opt/team-workspace (Group: project-team, Permission: 775)

Commands Used
sudo useradd -m username
sudo passwd username
sudo groupadd groupname
sudo usermod -aG group username
sudo mkdir -p /opt/directory
sudo chgrp groupname directory
sudo chmod 775 directory
groups username
ls -ld directory

What I Learned

How to create and manage Linux users and groups.

How group permissions control shared directory access.

Importance of correct permissions (775).

How to verify user group membership.

Real-world usage of shared team directories.
