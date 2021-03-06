# Learn Linux file permissions (II)
## Bash, PowerShell 
### URL: https://www.jesusninoc.com/2018/03/11/learn-linux-file-permissions-ii/
```PowerShell
# Numerical permissions:
# Permission	rwx
# 7	read, write and execute	rwx
# 6	read and write	rw-
# 5	read and execute	r-x
# 4	read only	r--
# 3	write and execute	-wx
# 2	write only	-w-
# 1	execute only	--x
# 0	none	---

# The main parts of the chmod permissions:
# the left three characters rwx define permissions of the OWNER.
# the middle three characters rwx define permissions of the GROUP.
# the right three characters rwx define permissions of EVERYONE ELSE.

# Numerical permissions
enum Operaciones{
    x = 1
    w = 2
    wx = 3
    r = 4
    rx = 5
    rw = 6
    rwx = 7
}

# Random numerical permissions
$aleatoriou = (random(1..7)) ; $permisou = [Operaciones]$aleatoriou
$aleatoriog = (random(1..7)) ; $permisog = [Operaciones]$aleatoriog
$aleatorioo = (random(1..7)) ; $permisoo = [Operaciones]$aleatorioo

# Show numerical permissions and ugo=rwx
Write-Host ([String]$aleatoriou + "|" + [String]$aleatoriog + "|" + [String]$aleatorioo) "->" ("u="+[String]$permisou + ",g=" + [String]$permisog + ",o=" + [String]$permisoo)

```
