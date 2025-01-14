You must turn on hyper V first and if you have this bug `Docker Desktop is unable to detect a Hypervisor`, follow this command:

```
bcdedit /set hypervisorlaunchtype auto
```

If you have this bug, you follow my step to fix.

```
Docker Desktop - Ubuntu-18.04
WSL integration with distro 'Ubuntu-18.04' unexpectedly stopped. Do you want to restart it?

running wsl distro proxy in Ubuntu-18.04 distro: running proxy: exit status 
```

```
C:\WINDOWS\system32>wsl -l -v
  NAME              STATE           VERSION
* Ubuntu-18.04      Stopped         1
  docker-desktop    Running         2

C:\WINDOWS\system32>wsl --set-version Ubuntu-18.04 2
For information on key differences with WSL 2 please visit https://aka.ms/wsl2
Conversion in progress, this may take a few minutes.
The operation completed successfully.

C:\WINDOWS\system32>
C:\WINDOWS\system32>wsl -l -v
  NAME              STATE           VERSION
* Ubuntu-18.04      Stopped         2
  docker-desktop    Running         2

C:\WINDOWS\system32>wsl --start Ubuntu-18.04
Invalid command line argument: --start
Please use 'wsl.exe --help' to get a list of supported arguments.

C:\WINDOWS\system32>wsl -d Ubuntu-18.04

clap@LAPTOP-EGMVE44L:/mnt/c/WINDOWS/system32$
clap@LAPTOP-EGMVE44L:/mnt/c/WINDOWS/system32$ exit
logout

C:\WINDOWS\system32>wsl -l -v
  NAME              STATE           VERSION
* Ubuntu-18.04      Running         2
  docker-desktop    Running         2

```
