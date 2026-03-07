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
```
```CMD
n (new partition)
```
```CMD
enter (primary default)
```
```CMD
enter (new partition number default)
```
```CMD
enter (first sector default)
```
```CMD
enter (last sector default)
```
```CMD
t (partition type)
```
```CMD
enter (new partition number default)
```
```CMD
8e (linux lvm)
```
```CMD
w (write and quit)
```
```CMD
lsblk (now we should see new /dev/vda3)
```
```CMD
sudo pvcreate /dev/vda3
```
```CMD
sudo vgextend /dev/mapper/rhel /dev/vda3
```
```CMD
sudo lvextend -l +100%FREE /dev/mapper/rhel-root
```
```CMD
sudo xfs_growfs /
```
