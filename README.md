# Managing-Users-in-Kali-Linux-as-a-Network-Security-dude-
A complete Linux User &amp; Group Management cheat sheet covering user creation, deletion, permissions, home directories, sudo privileges, group administration, shell management, and security best practices. Perfect for sysadmins, security interns, and anyone mastering Linux fundamentals.

Alright bro, here’s a **clean, polished, Notion-ready, no-nonsense Linux User & Group Management Cheat Sheet**.
Short, crisp, copy-paste friendly, and covers EVERYTHING you learned — plus the new ones.

---

#  **Linux User & Group Management — Ultimate Cheat Sheet**

---

##  **Create User**

```
sudo adduser lemur
sudo useradd lemur
```

### Create user + home directory

```
sudo useradd graylemur -m
```

---

##  **View All Users**

```
cat /etc/passwd
cut -d: -f1 /etc/passwd
awk -F: '$3 >= 1000 {print $1}' /etc/passwd
```

---

##  **Change Password**

```
sudo passwd lemur
```

---

##  **Home Directory Stuff**

### Show all home directories

```
ls /home
```

### View inside another user’s directory (safe way)

```
sudo ls -la /home/darklemur
```

### Allow others to enter a user’s home

```
sudo chmod 755 /home/lemur
```

### Lock down the home directory (default security)

```
sudo chmod 700 /home/lemur
```

### Create a home directory for an existing user

```
sudo mkhomedir_helper username
```

---

##  **Shell Management**

### Change user shell to bash

```
sudo usermod --shell /bin/bash darklemur
```

### Change username

```
sudo usermod -l newname oldname
```

---

##  **Delete User**

### Delete user only

```
sudo deluser lemur
```

### Delete user + home directory

```
sudo deluser --remove-home lemur
```

---

##  **Switch Between Users**

### Log in as another user

```
sudo su - lemur
```

### Log out from switched user

```
exit
```

---

##  **Sudo / Root Privileges**

### Give sudo power (recommended)

```
sudo usermod -aG sudo lemur
```

### Remove sudo power

```
sudo deluser lemur sudo
```

### visudo (manual privilege control)

```
sudo visudo
```

Example full sudo:

```
lemur ALL=(ALL:ALL) ALL
```

### Give specific command access (no password)

Inside visudo:

```
lemur ALL=(ALL:ALL) NOPASSWD: /sbin/useradd
```

---

##  **Group Management**

### Show all groups

```
cat /etc/group
getent group
```

### Create a new group

```
sudo groupadd powerhouse
```

### Delete a group

```
sudo groupdel powerhouse
```

### Add user to group

```
sudo usermod -aG powerhouse darklemur
```

### Remove user from group

```
sudo gpasswd -d darklemur powerhouse
```

### Give full sudo power to a group

Inside visudo:

```
%powerhouse ALL=NOPASSWD:ALL
```

---

##  **Password & Account Aging**

Change password aging settings:

```
sudo chage -i username
```

Common options:

* **Minimum age:** 0
* **Maximum age:** 99999
* **Warning days:** default
* **Inactive days:** default

Check aging info:

```
sudo chage -l username
```

---

# **YOU NOW KNOW:**

* User creation
* Deletion
* Shell assignment
* Home directory control
* Permissions
* Sudo privileges
* Specific command delegation
* Full group management
* Password aging
* Switching users

Bro, this is **real sysadmin muscle**. You can manage a small company with this.

If you want, I can also make a **File Permissions Cheat Sheet (chmod, chown, umask)** next.
