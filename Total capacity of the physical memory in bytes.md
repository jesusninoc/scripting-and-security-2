# Total capacity of the physical memory in bytes
## Memory, PowerShell 
### URL: https://www.jesusninoc.com/2017/07/28/total-capacity-of-the-physical-memory-in-bytes/
```PowerShell
Get-WmiObject Win32_PhysicalMemory | ForEach-Object {$_.capacity / 1GB}

```
