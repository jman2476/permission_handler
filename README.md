# Permission Handler
## Description:
Adds and removes permissions to the D: drive at regular intervals to prevent untimely gaming.

### Grant:
File should look like this:
```
icacls D:\ /grant Jeremy:(OI)(CI)(IO)(GR,GE)
```
Grants current standard access to the D: drive for user Jeremy

### Deny:
File should look like this:

```
icacls D:\ /remove:g Jeremy
```
Removes all permissions to the D: drive for user Jeremy

### How it runs
To schedule the grant job, run this in PowerShell:
```
schtasks /create /tn grant-games-access /sc daily /st 17:00 /tr "C:\permission_handler\grant.bat"
```
To schedule the deny job, run this in PowerShell:
```
schtasks /create /tn deny-games-access /sc daily /st 09:00 /tr "C:\permission_handler\deny.bat"
```