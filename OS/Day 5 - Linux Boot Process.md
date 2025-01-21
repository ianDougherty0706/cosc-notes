# Day 5 - Linux Boot Process

## lsblk
- Command that shows block devices (storage devices)

## xxd
- Command that lists out the hex values of the MBR
- Examine the contents

```BASH
student@linux-opstation-kspt:~$ sudo xxd -l 512 -g 1 /dev/vda 

00000000: eb 63 90 00 00 00 00 00 00 00 00 00 00 00 00 00  .c.............. 
00000010: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
```

## dd
- making a copy of the MBR
  
```BASH
student@linux-opstation-kspt:~$ dd if=/dev/vda of=MBRcopy bs=512 count=1
```

- bs = block size
- count is how many partitions you want to skip

**/etc/init** - first proces to start in SysV Linux machines
- reads /etc/inittab and /sbin/init
- loaction of possible persistence

