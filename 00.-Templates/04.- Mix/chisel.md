
- We launch chisel server on the victim machine.

```
./chisel.exe server --port 8080 --reverse
```

- We launch chisel client on kali

```
chisel client <% tp.frontmatter["VictimIP"] %> R:socks > /dev/null 2>&1 &
```

