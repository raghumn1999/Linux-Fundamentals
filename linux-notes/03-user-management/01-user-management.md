
# why user management is important?

* Accountability: In a team,we have multiple peoples,we can't use root user because if anything happen on
  server,it is not possible to identify and track user.
* secure: we can't give root user access to all people,because root user have all administrative privileges.
  so user management is required.


# User management

* Linux is a multi-user operating system, meaning multiple users can operate on a system simultaneously. 
  Proper user management ensures security, controlled access, and system integrity

* Key files involved in user management:
 
  /etc/passwd – Stores user account details.
  /etc/shadow – Stores encrypted user passwords.
  /etc/group – Stores group information.
  /etc/gshadow – Stores secure group details.

# Adding user

```
$ useradd -m <username>   --> creating the user with home directory

$ passwd <username>   --> changing the user password

$ cat /etc/passwd     --> to check user created,check the user entry in /etc/passwd

$ cat /etc/shadow    --> to check password created for user,check encrypted password entry in /etc/shadow

```

```
$ useradd -s /bin/bash username  --> to specify shell
```

# Modifying Users

Modify an existing user with usermod:

* Change the username:
  ```
  usermod -l new_username old_username
  ```

* Change the home directory:
   ```
   usermod -d /new/home/directory -m username
   ```
* Change the default shell:
   ```
   usermod -s /bin/zsh username
   ```

# Deleting user

```
$ userdel <username>  --> remove user but keep their home directory:

$ userdel -r <username>  --> remove user with home directory
```

* is it possible to get password of user,which is stored in /etc/shadow or user forget his password is it 
  possible to restore passsword?
Ans: No, not able to decrypt password and we have to reset password and share to user

* what is difference between useradd and adduser?
Ans:
     useradd will not prompt for any details and not create home directory by default.
     useradd is very usefull in script because of its non-prompt behaviour

   adduser will take all details and create home directory by default


# Enforcing Password Policies

* Password expiration: Set password expiry days
   ```
   chage -M 90 username --> every 90 days password will expire
   ```

* Lock a user account
   ```
   passwd -l <username>
   ```

* Unlock a user account
   ```
   passwd -u <username>
   ```

# Groups

* why groups are required?
* In any organization have more peoples,some are developers,some are QA,few are devops engineers etc.
  we can't create every user on system,we can create group for each team and add user into group.
  if any permission modification required,if we update group,every users in that group got modified
  permissions and while removing also,we can remove from group.

# Creation of group,adding user to group

```
groupadd <group name>  --> creating a group

cat /etc/group  --> check /etc/group to get to know group created or not

usermod -aG <group name> <username>  --> adding user to group

cat /etc/group  --> show the user details on group
```

# Viewing Group Memberships
```
groups username
```

# Changing Primary Group
```
usermod -g new_primary_group username
```

# Sudo Access and Privilege Escalation

# Adding a User to Sudo Group

* On Debian-based systems:
```
usermod -aG sudo username
```

* On RHEL-based systems:
```
usermod -aG wheel username
```

# Granting Specific Commands with Sudo
* Edit the sudoers file:
  ```
  visudo
  ```
* Then add:
  ```
  username ALL=(ALL) NOPASSWD: /path/to/command
  ```


# Remote login into linux server

* On linux server,sshd process is running
* On your machine,install ssh-client which will install ssh command on linux system
  if your using windows, use git bash
  if your using mac,use iterminal1
* Run below command to connect linux server remotely
  $ ssh username@ip_or_hostname  --> it will ask for password,enter password and login

* Most of time,organization disabled password based authentication
  To disable password based authentication
     * open /etc/ssh/ssh_config file,uncomment below line 
       PasswordAuthentication yes
     * set to PasswordAuthentication no
       PasswordAuthentication no
     * restart the ssh service

* if disable password based authentication,how we can login?
   * we can use pem file to login

