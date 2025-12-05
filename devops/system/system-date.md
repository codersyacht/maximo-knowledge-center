## Change System Time

### Author: Jawahar

### Agenda

Set system time to UTC

### Prerequisite

**Setting System Time to UTC**

Login as root.

```CMD
timedatectl set-timezone UTC
```
```CMD
sudo reboot
```

Verify if the system time changed after restart to UTC

```CMD
date
```

Output:
```
Mon Jan  6 05:27:47 AM UTC 2025
```

### Learning

System time successfully changed to UTC.
