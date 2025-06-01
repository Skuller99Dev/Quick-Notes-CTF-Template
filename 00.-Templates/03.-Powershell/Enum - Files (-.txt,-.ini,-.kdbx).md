<%*
let path = await tp.system.prompt("Enter directory path")
-%>

- Search for files in the directory  <% path %>

```
Get-ChildItem -Path <% path %> -Include *.txt,*.ini,*.kdbx -File -Recurse -ErrorAction SilentlyContinue
```

```
Get-ChildItem -Path <% path %> -Include *.txt,*.pdf,*.xls,*.xlsx,*.doc,*.docx -File -Recurse -ErrorAction SilentlyContinue
```

- Check history

```
(Get-PSReadlineOption).HistorySavePath
```

- we check at environment variables: 

```
Get-ChildItem -Path Env:
```

