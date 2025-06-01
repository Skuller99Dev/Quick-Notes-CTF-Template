
- There is username and password on this you can upload shell on direcotry or find downloads files for initial access

```
 nmap --script=ftp-* -p 21 <% tp.frontmatter["IPVictima"] %>  (scan complete FTP Port)
```

-  check if anonymous allowed then use ftp anonymous@ip  (password also anonymous)
- there is some mod if ls dir not work then apply use passive (to go in active mod).
- mget * (# Download everything from current directory like zip, pdf, doc)
- send/put (# Send single file or upload shell command)
- after download files ==always use exiftool== –u -a <filename> (Meta description for users)
- FTP *version above 3.0 not exploitable*