Window MAC address
BC-09-1B-7C-26-D5
hostname CTC-LAPT-110
username pyco\phi.nguyendinh

Check leak information: https://ipleak.net/

```

networksetup -setairportpower en0 off
networksetup -setairportpower en0 on
ip link set dev en0 address bc:09:1b:7c:26:d5
>> Connect
```


Bug checking:
journalctl
curl verbose
ps aux | grep to check the command, configuration file when running service.

