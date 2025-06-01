```
$userpassword=ConvertTo-SecureString -AsPlainText -Force -String password123!
New-ADUser -Name Shoganai -Enabled $true -AccountPassword $userpassword

```