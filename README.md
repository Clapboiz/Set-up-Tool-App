# SET-UP-TOOL-APP

To lock the PowerShell execution policy and return to the default state, you can use the "Set-ExecutionPolicy Restricted" command. This will block the execution policy that allows execution of script files that are digitally signed and from trusted software vendors.

Run in powershell with admin role ("Run as Administrator"):
```markdown
Set-ExecutionPolicy Bypass
```

The following steps help you block the PowerShell execution policy:

Open PowerShell with administrative rights by right-clicking on the PowerShell icon and selecting "Run as Administrator".

Run the command "Set-ExecutionPolicy Restricted" to lock the execution policy.

```
Set-ExecutionPolicy Restricted
```

Enter "Y" to confirm the change of the enforcement policy.

### HOW TO DELETE 1 FOLDER IN WINDOWS WITH ADMIN ROLE
```
Start-Process PowerShell -Verb RunAs -ArgumentList "Remove-Item -Path 'D:\folder\folder' -Force -Recurse"
```

# REFERENCES
[1] https://www.sharepointdiary.com/2020/02/how-to-delete-a-folder-in-powershell.html#:~:text=To%20delete%20a%20folder%20in%20PowerShell%2C%20you%20can%20use%20the,delete%20using%20the%20%2DPath%20parameter.&text=This%20will%20delete%20the%20folder,contents%2C%20including%20subfolders%20and%20files.
