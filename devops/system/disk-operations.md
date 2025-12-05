## Increase Disk Space

Check current disk space.

```CMD
df -k
```

```CMD
df -h
```

Output:

```
Filesystem           Size  Used Avail Use% Mounted on
devtmpfs             4.0M     0  4.0M   0% /dev
tmpfs                 32G     0   32G   0% /dev/shm
tmpfs                 13G  8.6M   13G   1% /run
/dev/mapper/cs-root  233G  4.1G  229G   2% /
/dev/vda1           1014M  324M  691M  32% /boot
tmpfs                6.3G     0  6.3G   0% /run/user/0
```
### Increase Disk Space

```CMD
fdisk /dev/vda

n (new partition)
enter (primary default)
enter (new partition number default)
enter (first sector default)
enter (last sector default)
t (partition type)
enter (new partition number default)
8e (linux lvm)
w (write and quit)

lsblk (now we should see new /dev/vda3)

sudo pvcreate /dev/vda3
sudo vgextend /dev/mapper/rhel /dev/vda3
sudo lvextend -l +100%FREE /dev/mapper/rhel-root
sudo xfs_growfs /
```
