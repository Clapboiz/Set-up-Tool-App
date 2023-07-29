# Set-up-Tool-App

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

