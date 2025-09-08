# Static Route Setup Guide

## Why

Add a static route so traffic to an internal subnet always goes through the correct gateway on your VPN adapter.

---

## Steps

### 1. Open CMD or PowerShell as Administrator

Start -> Search `cmd` or `PowerShell` -> Right-click -> Run as administrator.

---

### 2. Find Interface Index and Gateway IP

Run the following commands:

```
route print
ipconfig /all
netsh interface ipv4 show interfaces
netsh interface ipv4 show config name="Your VPN Adapter Name"
```

Look for:

- **Interface index** (e.g., `26`)
- **Gateway IP** (e.g., `192.168.1.1`)

---

### 3. Add Persistent Route

For an entire subnet:

```
route -p add 192.168.50.0 mask 255.255.255.0 192.168.1.1 metric 1 if 26
```

For a single host:

```
route -p add 192.168.50.100 mask 255.255.255.255 192.168.1.1 metric 1 if 26
```

---

### 4. Verify Route

Check if the route exists:

```
route print 192.168.50
```

---

### 5. Test Connectivity

Run basic connectivity tests:

```
ping 192.168.50.100
tracert 192.168.50.100
```

---

### 6. Optional DNS Configuration

If internal domain resolution fails:

```
nslookup internal.example.com
notepad C:\Windows\System32\drivers\etc\hosts
ipconfig /flushdns
```

---

### 7. Remove Route (if needed)

```
route delete 192.168.50.0
```

---

## PowerShell Equivalent

To add the same route using PowerShell:

```
New-NetRoute -DestinationPrefix 192.168.50.0/24 -InterfaceIndex 26 -NextHop 192.168.1.1 -RouteMetric 1 -PolicyStore PersistentStore
```

# Example
# Static Route Setup - Step-by-Step Example

## Example: Static Route for `192.168.50.0/24` via VPN

### Step 1 - Open CMD as Admin  
(no command - open manually)

---

### Step 2 - Find Interface Index

```cmd
netsh interface ipv4 show interfaces
```

**Output (example):**
```
Idx     Met     MTU          State                Name
---  -------  ----------  ------------  ---------------------------
26       35        1500      connected    MyVPN
```

```cmd
netsh interface ipv4 show config name="MyVPN"
```

**Output (example):**
```
Configuration for interface "MyVPN"
    IP Address:                           10.8.0.10
    Default Gateway:                      10.8.0.1
```

---

### Step 3 - Add Static Route

```cmd
route -p add 192.168.50.0 mask 255.255.255.0 10.8.0.1 metric 1 if 26
```

**Output:**
```
OK!
```

---

### Step 4 - Verify Route

```cmd
route print 192.168.50
```

**Output (example):**
```
Network Destination        Netmask          Gateway       Interface  Metric
       192.168.50.0    255.255.255.0        10.8.0.1       10.8.0.10       1
```

---

### Step 5 - Test Connectivity

```cmd
ping 192.168.50.100
```

**Output (example):**
```
Reply from 192.168.50.100: bytes=32 time<10ms TTL=64
```

```cmd
tracert 192.168.50.100
```

**Output (example):**
```
Tracing route to 192.168.50.100
  1     1 ms     1 ms     1 ms  10.8.0.1
  2     2 ms     2 ms     2 ms  192.168.50.100
```

---

### Step 6 - Optional DNS

```cmd
notepad C:\Windows\System32\drivers\etc\hosts
```

**Add line:**
```
192.168.50.100    internal.example.com
```

```cmd
ipconfig /flushdns
nslookup internal.example.com
```

**Output (example):**
```
Server:  UnKnown
Address:  127.0.0.1

Name:    internal.example.com
Address: 192.168.50.100
```

---

### Step 7 - Remove Route

```cmd
route delete 192.168.50.0
```

**Output:**
```
OK!
```

---

### PowerShell Equivalent

```powershell
New-NetRoute -DestinationPrefix 192.168.50.0/24 -InterfaceIndex 26 -NextHop 10.8.0.1 -RouteMetric 1 -PolicyStore PersistentStore
```

**No output if successful.**
