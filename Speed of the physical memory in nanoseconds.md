# Speed of the physical memory in nanoseconds
## Memory, PowerShell 
### URL: https://www.jesusninoc.com/2017/08/26/speed-of-the-physical-memory-in-nanoseconds/
```PowerShell
Get-WmiObject Win32_PhysicalMemory | Select-Object Speed

```
