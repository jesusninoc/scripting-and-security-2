# The configured clock speed of the memory device
## Memory, PowerShell 
### URL: https://www.jesusninoc.com/2017/08/22/the-configured-clock-speed-of-the-memory-device/
```PowerShell
Get-WmiObject Win32_PhysicalMemory | Select-Object ConfiguredClockSpeed

```
