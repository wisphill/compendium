### Netfilter
Netfilter is a network framework inside the Linux kernel. It allows preventing, modifying, watching packages going through the system.

Netfilter provides 5 hooks:
1. PREROUTING: The packages comes to the network card before routing
2. POSTROUTING: The packages leaves the network card
3. INPUT: The packages are sent to the current machine
4. OUTPUT: The packages are created by current machine and prepared to send out
5. FORWARD: The packages are going through to switch to the different network

Netfilter can be used by modules
1. conntrack: watching the TCP state to build the stateful firewall, stateful connection
2. NAT: Change the ip source/dest to route packages, hide the internal network, access internet
3. Package filtering: preventing, firewall
4. Package mangling: Change the package headers

### Iptables, nftables
They are in the user spaces to interact with the netfilter rules, allows user to define the rules for the netfilter to process

Nftables is a upgrade version of iptables, has more advantages, make the kernel more lighter to process.