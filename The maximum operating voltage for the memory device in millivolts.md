# The maximum operating voltage for the memory device in millivolts
## Memory, PowerShell 
### URL: https://www.jesusninoc.com/2017/08/18/the-maximum-operating-voltage-for-the-memory-device-in-millivolts/
```PowerShell
Get-WmiObject Win32_PhysicalMemory | Select-Object MaxVoltage

```
