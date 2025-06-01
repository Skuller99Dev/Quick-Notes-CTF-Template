<%*
let prefix = await tp.system.prompt("Enter the file prefix")
let path = await tp.system.prompt("Enter the directory path")
-%>

- We launch Sharphound and then import it into bloodhound.

```
powershell -ep bypass
Import-Module .\SharpHound.ps1
Invoke-BloodHound -CollectionMethod All -OutputDirectory <% path %>\ -OutputPrefix "<% prefix %>"
```