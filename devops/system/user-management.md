## User Setup

### Author: Jawahar

### Agenda

- Create a new user called _admin_.
- Set the user password.
- Provide root access.

### Prerequisite

**Recommendation:** <br>
Standardize the system time to UTC or EST. <br>

[System Time](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/system/system-date.md)

**Note :** The instruction is for creating user _admin_. Replace _admin_ with the intended user name.

### User Setup

Note: All the following steps are to create a user _admin_. To create a user with different name, replace admin with the intended user name.

**1. Create user admin.**

```CMD
useradd admin
```

Set password as "LabMachine4@Training"

```CMD
passwd admin
```


**2. Provide root access to admin user.**

Type **visudo** and edit the file by adding the following line under "_Allow root to run any commands anywhere_".

```script
admin    ALL=(ALL)   ALL
```
```
## Allow root to run any commands anywhere 
root     ALL=(ALL)   ALL
admin    ALL=(ALL)   ALL
```

Uncomment the following:

```
## Same thing without a password
%wheel  ALL=(ALL)       NOPASSWD: ALL
```

exit visudo.

**3. Add the user to wheel group.**

The wheel group is a special user group used to control access to the su or sudo command, which allows a user to masquerade as another user (usually the super user).

```CMD
sudo usermod -aG wheel admin
```
Exit and login back as admin user.


**4. Check a user in a group.**

```script
groups <user>
```

**5. Check all users in a group.**

```script
getent group <group>
```

**Delete user from a group.**

Perform this step only if you want to delete the user.

```script
gpasswd -d <user> <group>
```

### Result

User is created with full root access
