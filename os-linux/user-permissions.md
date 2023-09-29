# User Permission

There can be three types of user for linux.

#### 1. Super User Account
- have urestrictd permission( root user ) 
- for administrative task 
- 1 user per computer
#### 2. User Account
- regular user
- use user will have a dedicatd directory in home =>/home/tom
- multiple users per computer
#### 3. Service Account
- relevant for linux server distros
- each service(apache,mysql etc) will have its own user.
- best practice for security
- don't run services with root user
- multiple users per computer

#### N.B : Windows manage user centrally.there could be one central server for multiple pcs.Some users can be registerd on the central server they can work on those pcs and they can use the applications of tha sentral server.For linux pcs there is no such case,but there can be multiple user for asingle pc.

## Multiple user management of linux server 
### Groups and Permissions
1. permissions can be given directlyto a user
2. permission can be set to group wise.For example,there can be two groups for develper and admin each with different permision.When a user is a member of a group he/she will get the perimissions accordingly.

### User management in Practice
- #### Read user list ,only root user can write on this list
```
cat /etc/passwd
```


**codemen-11:x:1000:1000:codemen-11,,,:/home/codemen-11:/usr/bin/zsh**

***USERNAME:PASSWORD:UID:GROUPID:GECOS:HOMEDIR:SHELL***


- #### Adding new user 
```
sudo adduser username
```
- #### Changing user password 
 sudo passwd username
```
sudo passwd tom
```

- #### Switch User 
 su - username
```
su - tom
```
as root 
```
su -
```

- #### Exit from other user

```
exit
```

- #### Adding new group
 sudo groupadd groupname
```
sudo groupadd devops
```
by default ,system assigns the next available GID from the range of group IDs specified in login.defs file


- #### See list od groups 
```
cat /etc/group
```

- #### Different user and group 

| adduser, addgroup, deluser, delgroup      | useradd, groupadd, userdel, groupdel |
| ----------------------------------------- | ------------------------------------ |
| interactive                               | user need to provide infos           |
| more user friendly   | low level utiities        |
| should use it when executing manually   | should use it when executing automated ways(scripts)        |
| should use it when executing manually   | should use it when executing automated ways(scripts)        |


- #### Modify user account
usermod [OPTIONS] username 
```
sudo usermod -g devops tom
```

- #### Deleting group
 sudo delgroup groupname
```
sudo delgroup tom
```
***user can have one primary group and multiple secendory groups***

#### Adding user to secodary groups
sudo usermod -G groupname username
```
sudo usermod -G admin tom
```

Later when adding to additional groups
```
sudo usermod -aG newgroup tom
```

- #### check documentations
```
man ls
```

- #### See the groups of current user
```
groups
```

#### See the groups of a user
groups username
```
groups tom
```
#### Create and add user to a group 
sudo useradd -G groupname username
```
sudo useradd -G devops nicole
```

#### Remove user from a group 
sudo gpasswd -d username groupname
```
sudo gpasswd -d nicole devops
```