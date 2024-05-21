# AN UNEXPECTED ERROR WAS ENCOUNTERED WHILE EXECUTING A WSL COMMAND
If you have error "an unexpected error was encountered while executing a wsl command"

try in powershell with administrator: 

```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

# PORTS ARE NOT AVAILABLE

If you have error "Ports are not available: listen tcp 0.0.0.0/port: bind: An attempt was made to access a socket in a way forbidden by its access permissions"

try in `cmd with administrator`:

```
net stop winnat
net start winnat
```

### REFERENCE

```
https://learn.microsoft.com/en-us/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package
```
