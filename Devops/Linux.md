```table-of-contents
```
# Network commands
```
### Watching where the package is on the networkd card 
sudo tcpdump -i eth0 port 80
sudo tcpdump host 8.8.8.8
sudo tcpdump port 80
sudo tcpdump src 192.168.1.5 and dst port 443 # combine rules
### tcpdump sample result

### Package counter, checking for what rule has most DROP packages
sudo iptables -L -v -n

### Other network commands
ip a: show all the network interfaces
ip r: show the routing of the packages coming into the machine
### sample result of ip r
# 10.42.0.0/24 dev cni0 proto kernel scope link src 10.42.0.1
# network 10.42.0.0/24 is on the device cni0 that's created by kernel protocol, and the destination is on the same cni0 internal network and the package src address will be 10.42.0.1

ss -tulpn: Check listening ports
netstat -tulpn
ping
curl
wget
lsof: Check process that opens ports
```

### nft
```
sudo nft monitor trace
### sample result using the debug table
 == ack tcp window 688
trace id a4df8cd9 inet debug_table trace_chain unknown rule handle 3 (verdict continue)
trace id a4df8cd9 inet debug_table trace_chain verdict continue
trace id a4df8cd9 inet debug_table trace_chain policy accept
trace id a64a2a67 ip filter INPUT packet: iif "cni0" ether saddr b2:c6:ac:fd:76:57 ether daddr 42:41:c0:14:a2:3e ip saddr 10.42.0.32 ip daddr 172.18.121.110 ip dscp cs0 ip ecn not-ect ip ttl 64 ip id 60834 ip length 52 tcp sport 56556 tcp dport 6443 tcp flags == ack tcp window 688
trace id a64a2a67 ip filter INPUT rule  counter packets 2651 bytes 649379 jump KUBE-ROUTER-INPUT (verdict jump KUBE-ROUTER-INPUT)
trace id a64a2a67 ip filter KUBE-ROUTER-INPUT rule ip saddr 10.42.0.32  counter packets 13 bytes 1059 jump KUBE-POD-FW-USM7NRBIRGTUOWVB (verdict jump KUBE-POD-FW-USM7NRBIRGTUOWVB)
trace id a64a2a67 ip filter KUBE-POD-FW-USM7NRBIRGTUOWVB rule  counter packets 25 bytes 2564 jump KUBE-NWPLCY-COMMON (verdict jump KUBE-NWPLCY-COMMON)
trace id a64a2a67 ip filter KUBE-NWPLCY-COMMON rule  ct state related,established counter packets 1677 bytes 361512 accept (verdict accept)


# delete nft table ruleset
sudo nft delete table inet debug_table

# add the new nft table ruleset - for debugging
sudo nft add table inet debug_table
# 2. Tạo một chuỗi (chain) ở vị trí đầu tiên của lộ trình (Prerouting)
sudo nft add chain inet debug_table trace_chain { type filter hook prerouting priority -300 \; }
# 3. Đánh dấu các gói tin đi ra/vào liên quan đến cổng 80 (HTTP) và 443 (HTTPS)
sudo nft add rule inet debug_table trace_chain tcp dport { 80, 443 } meta nftrace set 1

```

# File 
```
cat 
less 
more
head
tail -f /var/log/syslog
wc -l file.txt # count lines, words, characters
```

# Search & filter
### awk
For handling the data tables, and columns
```
# awk to handle columes and math calculation
# print the colume 5th and 9th
ls -l | awk '{print $5, $9}'
# print the colume 1st and 2nd if the CPU at the colume 3 is greater than 0.1
ps aux | awk '$3 >= 0.1 {print $1, $2}'
# handle the table data if the separator is not white space, let's use -F:
# sample for reading all users in the passwd file
awk -F: '{print $1}' /etc/passwd
# calculation, sum the colume 5th to the end then print
ls -l | awk '{sum += $5} END {print sum}'
# tcpdump without dns resolution | print the ip with port | cut by . then get the fields 1-4 | sort | unique
sudo tcpdump -n -c 100 | awk '{print $3}' | cut -d. -f1-4 | sort | uniq

# in the column 9, search by .log then print the column 9
awk '$9 ~ /\.log$/ {print $9}'
```
### find
```
# find all files that has .log
find . -name "*.log" 

ps aux | grep nginx

# show all error findings in the logfile
grep -i error logfile.log 
```

### sed
sed is a stream editor for the line editing and transforming text

```
-n nothing --quite

-i inplace editing

# /p print all lines in the stream, first line contains 04:08:55 to the line contains 04:08:55
sed -n '/04:08:55/,/04:09:00/p' tcpdump.log

# print line 5
sed -n '5p' file.txt
# print line 5th to 10th
sed -n '5,10p' file txt

# print line contains `error`
sed -n '/error/p' log.txt

# search and replace 
sed 's/old_word/new_word/' file.txt
# replace all
sed 's/old_word/new_word/g' file.txt
# add -i for inplace editing and save to the file directly
sed -i 's/old_word/new_word/g' file.txt 

# delete
sed '2d' file.text
sed '/error/d' file.txt
```


# Process & service commands
```
ps aux --sort
ps aux --sort=-%mem | head
ps aux --sort=-%cpu | head
```


# Trace program call
1. Use the strace, gdb to trace the system calls (syscall) of the program. Only for debugging the third-party to know what're behind.

# Fine tuning for Docker
Kernel tuning
```
# /etc/sysctl.conf
# Expand the PID space
kernel.pid_max = 4194304

# Handle high-volume networking
net.core.somaxconn = 8192
net.ipv4.ip_local_port_range = 1024 65535
net.ipv4.tcp_tw_reuse = 1

# Increase file descriptor limits
fs.file-max = 2097152

# Support many memory mappings
vm.max_map_count = 262144
```

# Features
1. Namespace: is a feature for mapping container entities and host entities. A entities has a different "view" at container or host. 
   Namespaces: (cgroups (for DinD), user, uts - hostname/domain name, ipc, net (ip), pid, mnt)
2. Cgroups: Manage the limit of containers (cpu, ram, mounted devices, pid, net priority, block i/o)
3. ulimit: number of processes for a user

### Swap 
Swap space is just a "safety space" for the computer's memory, when the physical memory is run out, it uses storage swap space as temporary extra memory

K8S
- Without swap, it gets OOMKilled
- With swap in the modern K8S, the performance can be degraded, and it's harder to debug than normal crash

# Bugs
1. Zombie process: 
	Checking defunct process + kill parent.
	Use runAsNonRoot to force to use /sbin/tini to run the process /sbin/tini running at the PID 1 then it can reap the zombie process
	PID 1: /sbin/tini
	 └─ PID 2: node app.js
	     └─ PID 3: child process (spawn) 
	When pod is restarted > PID 2 is terminated > PID 3 (orphaned) -> re-parented to PID 1 -> PID 3 be terminated. 
	Use Prometheus to check accumulation of zombie processes