#spoofing #trick
### Fake information for the laptop provided by comp
1. Change the hostname
2. Change the username
3. Change the Mac TTL to the default window TTL
4. Fake user agent, information in the browser, then check by using https://ipleak.net/
5. Fake the MAC address then use 
   ```
	networksetup -setairportpower en0 off
	networksetup -setairportpower en0 on
	ip link set dev en0 address bc:09:1b:7c:26:d5
	>> then connect
   ```



