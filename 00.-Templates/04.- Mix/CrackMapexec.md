<%*
let protocol = await tp.system.prompt("Enter protocol")
-%>

- We test with Crackmapexec possible credentials against domain and in turn enumerate shared users and directories in the domain.

```
netexec <% protocol %> targets.txt -u users.txt -p passwords.txt
```

>[!Warning]
>
> Take into account the different protocols to be tested and also test in a local environment rather than in a domain.
> - Local
> ```
> netexec smb targets.txt -u users.txt -p passwords.txt --local-auth --continue-on-success
> ```
> - Domain
> ```
> netexec smb targets.txt -u users.txt -p passwords.txt -d <% tp.frontmatter["DOMAIN"] %> --continue-on-success
> ```
> - List all shares of all listed users
>``` 
>netexec smb targets.txt -u users.txt -p passwords.txt --shares  
> ```
> - displays all the users of the machine domain and their descriptions
> ```
>netexec smb targets.txt -u users.txt -p passwords.txt --users 
> ```
> - checks the users value 1 - value 1 of each of the files without testing the rest.
> ```
> netexec smb targets.txt -u users.txt -p passwords.txt --no-bruteforce --continue-on-success
> ```
