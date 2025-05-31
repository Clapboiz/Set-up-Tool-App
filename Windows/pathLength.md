# ERROR: CAN'T EDIT ENVIRONMENT VARIABLE OVER 2047 CHARACTERS
## SOLUTION 1
Following step by step:

![image](https://github.com/Clapboiz/Set-up-Tool-App/assets/112185647/da390ca2-c6c4-40fa-b342-9e0e65a9511a)

![image](https://github.com/Clapboiz/Set-up-Tool-App/assets/112185647/ac11a8ae-2433-4365-9f4a-8a6a16f6bc90)

![image](https://github.com/Clapboiz/Set-up-Tool-App/assets/112185647/8c1a43a1-e315-45cd-b09b-ddef1b7ada82)

you create a new path, any name you want. I encourage you create name the same as me.

`Path1`, `Path2`, `Pathx` (x is a number). 

After you convert all your paths to path 1,2,3,... (each path <2047 characters), please edit `Path` -> `%Path1%;%Path2%;%Pathx%`

Open powershell with administration to make this change permanent

```
$Path2 = $env:Path2
$Path3 = $env:Path3
$env:PATH += ";$Path2;$Path3"
[System.Environment]::SetEnvironmentVariable("PATH", $env:Path, [System.EnvironmentVariableTarget]::Machine)
```

Then type this command in cmd (Optional)

```
set Path=%Path2%;%Path3%
```

## SOLUTION 2
You type `Windows + R` and type `regedit`, then you access the path `Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Environment` and add your path.

![image](https://github.com/Clapboiz/Set-up-Tool-App/assets/112185647/afa545ef-80ce-4caa-a09f-83b695709bb8)

## REFRESH ENV
You added the path to the registry, but the environment variable hasn't been refreshed yet

When you manually add a path to the registry at:

```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Environment
```

Windows does not apply the change immediately. To make it take effect, you have two options:

```
OPTION 1: Restart your computer
```

```
OPTION 2: You can do this from PowerShell (run as Administrator):
$env:Path = [System.Environment]::GetEnvironmentVariable("Path", "Machine")
```

Then test it again with your command

# REFERENCES
[1]. https://answers.microsoft.com/en-us/windows/forum/all/cant-edit-environment-variable-over-2047/ac713701-b1b4-4f6f-b2c7-5bb9282addb9

[2]. https://superuser.com/questions/1385854/how-do-i-bypass-restrictions-on-the-length-of-the-path-variable

[3]. https://stackoverflow.com/questions/19287379/how-do-i-add-to-the-windows-path-variable-using-setx-having-weird-problems

[4]. https://www.delftstack.com/howto/powershell/set-the-path-environment-variable-in-powershell/

[5]. https://stackoverflow.com/questions/714877/setting-windows-powershell-environment-variables
