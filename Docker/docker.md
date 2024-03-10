If you have error "an unexpected error was encountered while executing a wsl command"

try in powershell with administrator: 

```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```