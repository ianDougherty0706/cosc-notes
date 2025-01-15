# Day 3 - Linux Essesntials and Alternate Data Streams

## 1. Alternate Data Streams

Microsofts attempt at implimenting file system forks to maintain compatibility with other file systems
- Stores metadata
- Cant be scanned by anti-virus
- Does not change md5 hash
- Cannot be disabled

Writing ADS
- using "echo" followed by ">" along with the stream exe. "reminder.txt:secret.info"

Finding ADS
- using "dir" with the option "/R"

Reading ADS
- using "more" followed by "<" along with the stream exe. "reminder.txt:secret.info"
- using "Get-Item" followed with "-Stream *"

## 2. Linux Essentials

File Locations
- / - Root
- /bin - essential commands
- /home - user directories
- /etc - host configuration
- /var - contains all system logs by default

## 3. Linux Users

/etc/passwd
- Houses every users UID

/etc/group
- Houses every users GID

### Permissions

|Permission |  File         |   Directory   |
|----------:|:-------------:|:-------------:|
| read(r) 4 | Read contents | List Contents |
|write(w) 2 | Write Contents| Create/delete |
|execute(x) 1 |   Run       |  Move         |


### Sticky Bit
Removes ability to remove file unless you are the owner or root
- seen as a *t* at the end of the permissions block

### SUID and SGID
Makes an executable run with the permissions of the owner of the file

## 4. String Manipulation

### grep
- -r = recursive grep for a directory

### awk
- allows reformatting or selection of text which contains delimeters
- on the fly tool using piping

```bash
student@linux-opstation-kspt:~$ ls -l /etc 
drwxr-xr-x  7 root root       4096 Feb  4  2020 NetworkManager
drwxr-xr-x  2 root root       4096 Feb  4  2020 PackageKit
drwxr-xr-x  2 root root       4096 Feb  4  2020 UPower

student@linux-opstation-kspt:~$ ls -l /etc | awk -F " " '{print$3","$4","$9}' > files.csv 
student@linux-opstation-kspt:~$ cat files.csv
root,root,NetworkManager
root,root,PackageKit
root,root,UPower
```

### sed
- edits text instead of filtering or formatting it
- edits text as it is sent to standard output
- "stream editor"

```bash
student@linux-opstation-kspt:~$ cat /etc/passwd | grep root 
root:x:0:0:root:/root:/bin/bash

student@linux-opstation-kspt:~$ cat /etc/passwd | grep root | sed s/root/bacon/g 
bacon:x:0:0:bacon:/bacon:/bin/bash
```