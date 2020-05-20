# echo

output strings

**outputs "hello world" to console:**

```bash
echo "hello world"
```
```bash
hello world
```

# pwd

**print working directory:**

```bash
pwd
```

```bash
/root
```

# cd

change folder

**change folder to /wfs/:**

```bash
cd /wfs/
```

# cp

copy files and folders

**create backup of setup.ini:**

```bash
cp setup.ini setup.ini.bck
```
# touch

create a file

**create file with name new.sh:**

```bash
touch new.sh
```

# chmod

change file attributes

**make new.sh executable:**

```bash
chmod +x new.sh
```

# mkdir

create a folder

**create folder with name newdir:**

```bash
mkdir newdir
```

# rmdir

delete a folder

**delete folder with name newdir:**

```bash
rmdir newdir
```

# rm

delete a file

**delete file with name new.sh:**

```bash
rm new.sh
```

# ls

show directory content

**long list current directory:**

```bash
ls -l
```
```bash
total 96
drwxr-xr-x  3 root root     60 Mai 20 13:49 apparmor
drwxr-xr-x  2 root root     40 Mai 20 13:49 asset.events
-rw-r--r--  1 root root   2765 Mai 20 13:50 asset.ini
drwxr-xr-x  2 root root    100 Mai 20 13:50 ca-certs
drwxr-xr-x  2 root root     60 Mai 20 13:49 chrony
...
-rw-------  1 root root    106 Mai 20 13:50 systemkey
-rw-r--r--  1 root root     49 Mai 20 13:50 systemmd5
-rw-------  1 root root     32 Mai 20 13:49 tckey
-rw-------  1 root root    214 Mai 20 13:49 updateconf.ini
drwxr-xr-x 14 user users   440 Mai 20 13:50 user
drwxr-xr-x  2 root root     40 Mai 20 13:49 zoneinfo

```

# su 

**change to root:**

```bash
su
```

# vi

texteditor

**open setup.ini in vi:**

```bash
vi setup.ini
```
```bash
<system>
        <remotemanager>
                <server0>
                        ip=<igelrmserver.int.acme.org>
                </server0>
        </remotemanager>
        <icg>
                <server0>
                        host=<icg.acme.org>
                        uuid=<d8d43ff7a4274b8f96fb6ec96c4948>
....
        <drivers>
                currentdriver=<intel>
                currentconnectors=<lvds1,Seiko Epson Corporation,,1366,768,1366,768,0,0,,;>
        </drivers>
</x>


```

# kill

kill a running task by process id

**kill process with PID 48:**

```bash
kill 48
```

# killall

kill a running task by name

**kill process with name pnlogin:**

```bash
killall pnlogin 2>/dev/null
``` 
# ps

**show running tasks:**

```bash
ps -aef
```
```bash
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 13:49 ?        00:00:03 /sbin/init 3
root         2     0  0 13:49 ?        00:00:00 [kthreadd]
root         3     2  0 13:49 ?        00:00:00 [rcu_gp]
root         4     2  0 13:49 ?        00:00:00 [rcu_par_gp]
root         6     2  0 13:49 ?        00:00:00 [kworker/0:0H-kb]
root         8     2  0 13:49 ?        00:00:00 [mm_percpu_wq]
root         9     2  0 13:49 ?        00:00:00 [ksoftirqd/0]
root        10     2  0 13:49 ?        00:00:00 [rcu_sched]
root        11     2  0 13:49 ?        00:00:00 [rcu_bh]
...
```

# cat

display a file

**show contents of group.ini:**

```bash
cat group.ini
```
```bash
<services>
        <cisco_vxme_client>
                enabled=<true>
        </cisco_vxme_client>
        <ica_client>
                enabled=<true>
...
```

# more

display a file page by page

**show contents of group.ini, hit space to continue to next page:**

```bash
more group.ini
```
```bash
<services>
        <cisco_vxme_client>
                enabled=<true>
        </cisco_vxme_client>
        <ica_client>
                enabled=<true>
...
```
# mount

mount a partition

**mount license folder readable:**

```bash
mount -o remount,rw /license
```

# user_shutdown

**shutdown the system:**

```bash
user_shutdown
```

# user_reboot

**reboot the system:**

```bash
user_reboot
```

# grep

search for regular expression

**search for configured UMS server name:**

```bash
more /wfs/setup.ini | grep "ip="
```
```bash
                        ip=<igelrmserver.int.acme.org>
```

# top

task monitor

```bash
top
```
```bash
top - 14:15:59 up 26 min,  2 users,  load average: 0,05, 0,01, 0,01
Tasks: 236 total,   1 running, 168 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0,1 us,  0,1 sy,  0,0 ni, 99,8 id,  0,0 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem :  1891000 total,   351040 free,   481452 used,  1058508 buff/cache
KiB Swap:  1134592 total,  1134592 free,        0 used.  1183616 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
18620 root      20   0   79776   4276   3520 R   0,3  0,2   0:00.02 top
    1 root      20   0  205624   9980   5812 S   0,0  0,5   0:03.88 systemd
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd
    3 root       0 -20       0      0      0 I   0,0  0,0   0:00.00 rcu_gp
    4 root       0 -20       0      0      0 I   0,0  0,0   0:00.00 rcu_par
...
```

# sleep

wait

**wait for 5 seconds:**

```bash
sleep 5
```

# watch

repeat periodic a command

**probe tcp port 8443 on igelrmserver every 2 seconds:**

```bash
watch probeport igelrmserver 8443
```
```bash
Every 2,0s: probeport igelrmserver 8443                                                                                                                       ITCA44CC8C90000: Wed May 20 14:24:08 2020

Connection successful
```

# which

locate command

**locate command nmcli:**

```bash
which nmcli
```
```bash
/usr/bin/nmcli
```

# uname

**show linux details:**

```bash
uname
```
```bash
Linux
```

# date

date tool

**show date:**

```bash
date
```
```bash
Mi 19. Mai 19:26:59 CEST 2020
```

# systemctl

service handler

**restart network:**

```bash
systemctl restart network-manager
```