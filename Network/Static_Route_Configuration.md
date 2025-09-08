# Static Route Setup Guide

## Why
Add a static route so traffic to an internal subnet always goes through the correct gateway on your VPN adapter.

---

## Steps

1. **Open CMD or PowerShell as Admin**  
   Start -> Search `cmd` -> Right-click -> Run as administrator.

2. **Find Interface and Gateway**
```
route print
ipconfig /all
netsh interface ipv4 show interfaces
netsh interface ipv4 show config name="Your VPN Adapter Name"
```
Look for adapter index (e.g., `26`) and gateway (e.g., `192.168.1.1`).

3. **Add Persistent Route**
```
route -p add 192.168.50.0 mask 255.255.255.0 192.168.1.1 metric 1 if 26
```
For a single host:
```
route -p add 192.168.50.100 mask 255.255.255.255 192.168.1.1 metric 1 if 26
```

4. **Verify**
```
route print 192.168.50
```

5. **Test**
```
ping 192.168.50.100
tracert 192.168.50.100
```

6. **Optional DNS**
```
nslookup internal.example.com
notepad C:\Windows\System32\drivers\etc\hosts
ipconfig /flushdns
```

7. **Remove Route**
```
route delete 192.168.50.0
```

---

**PowerShell Equivalent:**
```
New-NetRoute -DestinationPrefix 192.168.50.0/24 -InterfaceIndex 26 -NextHop 192.168.1.1 -RouteMetric 1 -PolicyStore PersistentStore
```
