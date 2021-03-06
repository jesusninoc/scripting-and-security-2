# Seguridad informática con PowerShell
## PHP, PowerShell, Security 
### URL: https://www.jesusninoc.com/2016/02/28/seguridad-informatica-con-powershell/
```PowerShell
#Habilitar BitLocker
Enable-BitLocker -MountPoint "f:" -RecoveryPasswordProtector -UsedSpaceOnly -Verbose

#Deshabilitar BitLocker
Disable-BitLocker -MountPoint "f:"

```
```PowerShell
#Calcular hash para un archivo
Get-FileHash D:\power\fichero.txt -Algorithm MD5
Get-FileHash D:\power\fichero.txt -Algorithm SHA1
Get-FileHash D:\power\fichero.txt -Algorithm SHA256
Get-FileHash D:\power\fichero.txt -Algorithm SHA384
Get-FileHash D:\power\fichero.txt -Algorithm SHA512
Get-FileHash D:\power\fichero.txt -Algorithm RIPEMD160

```
```PowerShell
$credenciales=Get-Credential
1..254 | %{
    (Get-WmiObject Win32_AutochkSetting -ComputerName ('192.168.1.'+$_) -Credential $credenciales).SettingID
    (Get-WmiObject Win32_BaseBoard -ComputerName ('192.168.1.'+$_) -Credential $credenciales).Manufacturer
    (Get-WmiObject Win32_BIOS -ComputerName ('192.168.1.'+$_) -Credential $credenciales).Version
    (Get-WmiObject Win32_Bus -ComputerName ('192.168.1.'+$_) -Credential $credenciales).DeviceID
    Get-WmiObject Win32_Processor -ComputerName ('192.168.1.'+$_) -Credential $credenciales
    Get-WmiObject Win32_SystemEnclosure -ComputerName ('192.168.1.'+$_) -Credential $credenciales
    Get-WmiObject Win32_Battery -ComputerName ('192.168.1.'+$_) -Credential $credenciales
    Get-WmiObject Win32_Printer -ComputerName ('192.168.1.'+$_) -Credential $credenciales
}

```
```PowerShell
Get-PnpDevice | Where-Object { $_.class -EQ 'USBDevice' } | Select-Object FriendlyName

Get-ItemProperty -Path 'Registry::HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\USBSTOR\*\*\' | Where-Object { $_.FriendlyName } | Select-Object FriendlyName
Get-ItemProperty -Path 'Registry::HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\USB\*\*\' | Where-Object { $_.FriendlyName } | Select-Object FriendlyName
Get-ItemProperty -Path 'Registry::HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Enum\USB\*\*\' | Where-Object { $_.FriendlyName } | Select-Object FriendlyName
Get-ItemProperty -Path 'Registry::HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Enum\USBSTOR\*\*\' | Where-Object { $_.FriendlyName } | Select-Object FriendlyName

```
```PowerShell
[System.Security.Principal.WindowsIdentity]::GetCurrent()

```
```PowerShell
#Es necesario abrir PowerShell como administrador

#Crear un usuario local con contraseña en Windows 10 con PowerShell 5.1
$pass=ConvertTo-SecureString "11234aaa@@€dsf" -asplaintext -force
New-LocalUser usuario -Password $pass

#Crear un grupo local en Windows 10 con PowerShell 5.1
New-LocalGroup grupo

#Añadir usuarios a un grupo local en Windows 10 con PowerShell 5.1
Add-LocalGroupMember -Member usuario -Group administradores

```
```PowerShell
#Programas instalados
Get-Package

```
```PowerShell
#Mostrar los procesos que se están ejecutando en relación con los servicios (solo llamadas WMI y más información)
(Get-WmiObject -Class Win32_Service | Where-Object State -EQ 'Running') | %{
Write-Host $_.Name,$_.ProcessId,$_.State,(Get-WmiObject -Class win32_process | Where-Object ProcessId -EQ  $_.ProcessId | select name, Path, ExecutablePath, CommandLine)
}

```
```PowerShell
#Mostrar los servicios que se están ejecutando en relación con los procesos y los hilos
(Get-WmiObject -Class Win32_Service | Where-Object State -EQ ‘Running’) | %{
Write-Host $_.Name,$_.ProcessId,$_.State,(Get-Process -Id $_.ProcessId).Name,(Get-WmiObject -Class Win32_Thread | Where-Object ProcessHandle -EQ $_.ProcessId)
}

```
```PowerShell
Get-HotFix | Select-Object HotFixID
Get-Package | Select-Object Name | Where-Object Name -match "Actualización" | Format-Custom

```
```PowerShell
Get-Process

```
```PowerShell
Get-Process | Select-Object Name,Path
Get-WmiObject -Class win32_process | Select-Object Name,ExecutablePath

```
```PowerShell
#Mostrar los procesos que ejecuta un usuario
Get-WmiObject win32_process |% {Write-Host $_.processname $_.getowner().user}

```
```PowerShell
#Relación entre puertos UDP, procesos y lista de puertos de la IANA (junto con una breve descripción de cada puerto)

#Descargar y guardar el listado de puertos
Invoke-WebRequest 'https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.csv' -OutFile e:\service-names-port-numbers.csv

#Relación entre puertos abiertos UDP y lista de puertos
$portscsv=Import-Csv e:\service-names-port-numbers.csv
$listado=$portscsv | Select-Object 'Service Name','Port Number','Transport Protocol','Description' | Where-Object 'Transport Protocol' -EQ udp
Get-NetUDPEndpoint | %{Write-Host (Get-Process -id $_.OwningProcess).Name, $_.Localaddress, ($listado | Select-Object 'Service Name','Port Number','Description' | Where-Object 'Port Number' -EQ $_.Localport)}

```
```PowerShell
#Relación entre puertos TCP, procesos y lista de puertos de la IANA (junto con una breve descripción de cada puerto)

#Descargar y guardar el listado de puertos
Invoke-WebRequest 'https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.csv' -OutFile e:\service-names-port-numbers.csv

#Relación entre puertos abiertos TCP y lista de puertos la IANA
$portscsv=Import-Csv e:\service-names-port-numbers.csv
$listado=$portscsv | Select-Object 'Service Name','Port Number','Transport Protocol','Description' | Where-Object 'Transport Protocol' -EQ tcp
Get-NetTCPConnection | %{Write-Host $_.Localaddress, ($listado | Select-Object 'Service Name','Port Number','Description' | Where-Object 'Port Number' -EQ $_.RemotePort), $_.Remoteaddress} | Format-Custom

```
```PowerShell
#Mostrar información avanzada de los procesos (Path, ExecutablePath, CommandLine) que se están ejecutando en relación con los servicios y los puertos abiertos UDP
(Get-WmiObject -Class Win32_Service | Where-Object State -EQ 'Running') | %{
#Write-Host $_.Name,$_.ProcessId,$_.State,(Get-Process -Id $_.ProcessId | Select-Object name, Path, ExecutablePath, CommandLine)
Write-Host $_.Name,$_.ProcessId,$_.State,(Get-WmiObject -Class win32_process | Where-Object ProcessId -EQ  $_.ProcessId | select name, Path, ExecutablePath, CommandLine)
Write-Host $_.Name,$_.ProcessId,$_.State,(Get-Process -Id $_.ProcessId).Name,(Get-NetUDPEndpoint | where OwningProcess -EQ $_.ProcessId | select LocalPort,RemoteAddress,RemotePort,OwningProcess)
Write-Host "##################################################"
}

```
```PowerShell
#Mostrar información avanzada de los procesos (Path, ExecutablePath, CommandLine) que se están ejecutando en relación con los servicios y los puertos abiertos TCP
(Get-WmiObject -Class Win32_Service | Where-Object State -EQ 'Running') | %{
#Write-Host $_.Name,$_.ProcessId,$_.State,(Get-Process -Id $_.ProcessId | Select-Object name, Path, ExecutablePath, CommandLine)
Write-Host $_.Name,$_.ProcessId,$_.State,(Get-WmiObject -Class win32_process | Where-Object ProcessId -EQ  $_.ProcessId | select name, Path, ExecutablePath, CommandLine)
Write-Host $_.Name,$_.ProcessId,$_.State,(Get-Process -Id $_.ProcessId).Name,(Get-NetTCPConnection | where OwningProcess -EQ $_.ProcessId | select LocalPort,RemoteAddress,RemotePort,OwningProcess)
Write-Host "##################################################"
}

```
```PowerShell
#Examinar el equipo en busca de virus
Start-MpScan

```
```PowerShell
#Ver las últimas definiciones del antivirus
(Get-MpThreatCatalog).ThreatName

```
```PowerShell
Add-WBBackupTarget
Add-WBBareMetalRecovery
Add-WBFileSpec
Add-WBSystemState
Add-WBVirtualMachine
Add-WBVolume
Get-WBBackupSet
Get-WBBackupTarget
Get-WBBackupVolumeBrowsePath
Get-WBBareMetalRecovery
Get-WBDisk
Get-WBFileSpec
Get-WBJob
Get-WBPerformanceConfiguration
Get-WBPolicy
Get-WBSchedule
Get-WBSummary
Get-WBSystemState
Get-WBVirtualMachine
Get-WBVolume
Get-WBVssBackupOption
New-WBBackupTarget
New-WBFileSpec
New-WBPolicy
Remove-WBBackupSet
Remove-WBBackupTarget
Remove-WBBareMetalRecovery
Remove-WBCatalog
Remove-WBFileSpec
Remove-WBPolicy
Remove-WBSystemState
Remove-WBVirtualMachine
Remove-WBVolume
Restore-WBCatalog
Resume-WBBackup
Resume-WBVolumeRecovery
Set-WBPerformanceConfiguration
Set-WBPolicy
Set-WBSchedule
Set-WBVssBackupOption
Start-WBApplicationRecovery
Start-WBBackup
Start-WBFileRecovery
Start-WBHyperVRecovery
Start-WBSystemStateRecovery
Start-WBVolumeRecovery
Stop-WBJob

```
```PowerShell
#Detectar los puertos abiertos que tienen las direcciones IP de un rango utilizando Nmap mediante un escaneo rápido
1..254 | %{nmap -F ('192.168.1.'+$_)}

#Detectar los servicios que están activos en las direcciones IP de un rango utilizando Nmap
1..254 | %{nmap -sV ('192.168.1.'+$_)}

#Detectar los puertos abiertos que tienen las direcciones IP de un rango utilizando Nmap
1..254 | %{nmap ('192.168.1.'+$_)}

#Detectar el sistema operativo que tienen las direcciones IP de un rango utilizando Nmap
1..254 | %{nmap -O ('192.168.1.'+$_)}

```
```PowerShell
#Información sobre conexiones
#https://www.jesusninoc.com/2015/11/13/cmdlets-for-tcpip-model-layers/
Get-NetAdapterHardwareInfo
Get-NetAdapter -Physical
Get-NetNeighbor
Get-NetAdapterStatistics
Get-NetAdapter | Select-Object Name,MacAddress
Get-NetAdapter | Select-Object Name,MacAddress
Get-WmiObject -Class Win32_NetworkAdapterConfiguration | Select-Object Description,MACAddress
Get-NetAdapter | Select-Object Name,MacAddress
Get-WmiObject -Class Win32_NetworkAdapterConfiguration | Select-Object Description,MACAddress
((Get-NetAdapterBinding).DisplayName) -match 'Protocolo de Internet'
(Get-NetIPInterface) | Select-Object InterfaceAlias,AddressFamily
Get-NetIPv4Protocol
Get-NetIPv6Protocol
Get-NetRoute
Get-NetNat
Get-NetNatExternalAddress
Get-NetNatGlobal
Get-NetNatSession
Get-NetNatStaticMapping
Get-NetNatTransitionConfiguration
Get-NetNatTransitionMonitoring
Get-NetFirewallAddressFilter
Get-NetFirewallApplicationFilter
Get-NetFirewallInterfaceFilter
Get-NetFirewallInterfaceTypeFilter
Get-NetFirewallPortFilter
Get-NetFirewallProfile
Get-NetFirewallRule
Get-NetFirewallSecurityFilter
Get-NetFirewallServiceFilter
Get-NetFirewallSetting
Get-NetTCPSetting
Get-NetTCPConnection
Get-NetTCPConnection | Select-Object LocalPort,Remoteport
Get-NetUDPSetting
Get-NetUDPEndpoint
(Get-NetUDPEndpoint).LocalPort
Get-DnsClient
Get-DnsClientCache
Get-DnsClientGlobalSetting
Get-DnsClientNrptGlobal
Get-DnsClientNrptPolicy
Get-DnsClientNrptRule
Get-DnsClientServerAddress

```
```PowerShell
#Mostrar el registro de eventos del día anterior
Get-EventLog -LogName System -EntryType Error, Warning -After (Get-Date).AddDays(-1)

```
```PowerShell
#Cifrar utilizando una clave secreta
$cadena='abcdefghijk'
$clave='clavesecreta123'

#La clave para cifrar tiene que ser correcta en tipo System.Byte
#ConvertFrom-SecureString : No se puede enlazar el parámetro 'Key'. No se puede convertir el valor "Some secret key" al tipo "System.Byte". Error: "La cadena de entrada no tiene el formato correcto."

$clavebyte=[Byte[]]($clave.PadRight(24).Substring(0,24).ToCharArray())

$cadenacifrada=$cadena | ConvertTo-SecureString -AsPlainText -Force | ConvertFrom-SecureString -Key $clavebyte
$cadenacifrada

```
```PowerShell
#Descifrar utilizando una clave secreta

$clave='clavesecreta123'

#La clave para cifrar tiene que ser correcta en tipo System.Byte
$clavebyte=[Byte[]]($clave.PadRight(24).Substring(0,24).ToCharArray())

$cadenadescifrando = $cadenacifrada | ConvertTo-SecureString -Key $clavebyte

$credencial = New-Object -TypeName System.Management.Automation.PSCredential('clave123', $cadenadescifrando)
$cadenadescrifrada = $credencial.GetNetworkCredential().Password
$cadenadescrifrada

```
```PowerShell
#Gets the items in one or more specified locations
Get-ChildItem

#Recursively searches for files with a “.txt” extension in the C:\temp directory. The contents of any files matching this criteria are then searched for the term “password”
Get-ChildItem c:\temp -Filter *.txt -Recurse | Select-String password

#Searching file “TeamViewer”
Get-ChildItem c:\ -rec -ea SilentlyContinue | ForEach-Object {
Select-String "TeamViewer" -input (Get-ItemProperty -Path $_.PsPath) -AllMatches
}

#Searching IP adresses in text files
Write-Host "IP addresses:`n"
Get-ChildItem C:\Users\ -rec -ea SilentlyContinue | ForEach-Object {
Select-String "\b\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\b" -input (Get-ItemProperty -Path $_.PsPath) -AllMatches | ForEach-Object {($_.matches)|Select-Object Value}
}

#Searching BitLocker recovery keys
#Searching content “Clave de recuperación de Cifrado de unidad BitLocker”
Get-ChildItem C:\Users\juan -rec -ea SilentlyContinue | ForEach-Object {
Select-String "Clave de recuperación de Cifrado de unidad BitLocker" -input (Get-ItemProperty -Path $_.PsPath) -AllMatches
}

#Large file, but contains spill over from RAM, usually lots of good information can be pulled, but should be a last resort due to size 
Get-ChildItem $env:SystemDrive\pagefile.sys

#Prefetch files
Get-ChildItem $env:SystemRoot\Prefetch

#Portion of accessed file list within prefetch file for PowerShell.exe
Get-Content $env:SystemRoot\Prefetch\POWERSHELL_ISE.EXE-85BC6AB4.pf

#File contains the registry settings
Get-ChildItem $env:windir\System32\config -Force

#File contains the registry settings for their individual account
Get-ChildItem $env:USERPROFILE\NTUSER.DAT

#This file contains the mappings of IP addresses to host names
Get-ChildItem $env:windir\System32\drivers\etc\hosts
Get-Content $env:windir\System32\drivers\etc\hosts

```
```PowerShell
#Shellbags
#Más información https://digital-forensics.sans.org/blog/2011/07/05/shellbags
Get-ChildItem HKCU:\Software\Microsoft\Windows\Shell
Get-ChildItem HKCU:\Software\Microsoft\Windows\

#Registros HIVE
Get-ChildItem HKLM:\SAM
Get-ChildItem HKLM:\SECURITY
Get-ChildItem HKLM:\SOFTWARE
Get-ChildItem HKLM:\HARDWARE

#Información sobre programas ejecutados (Prefetch)
Get-ChildItem C:\Windows\Prefetch

#Información sobre navegadores
Get-ChildItem C:\Users\user\AppData\Local\Microsoft\Windows\History
Get-ChildItem C:\Users\user\AppData\Local\Mozilla\Firefox\Profiles

#Ficheros temporales
Get-ChildItem C:\Windows\Temp

#Ficheros temporales de los usuarios
Get-ChildItem C:\Users\user\AppData\Local\Temp

#Información sobre el hardware
Get-ChildItem C:\Windows\Inf

#Información sobre USB
Get-ChildItem HKLM:\SYSTEM\ControlSet001\Enum\USB
Get-ChildItem HKLM:\SYSTEM\ControlSet001\Enum\USBSTOR
Get-ChildItem HKLM:\SYSTEM\CurrentControlSet\Enum\USB
Get-ChildItem HKLM:\SYSTEM\CurrentControlSet\Enum\USBSTOR
Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\Windows Portable Devices\Devices'
Get-ChildItem 'HKLM:\SYSTEM\ControlSet001\Control\DeviceClasses'

#Información acerca de las acciones de instalación durante la instalación
Get-Content C:\Windows\setupact.log

#Información sobre los errores de instalación durante la instalación
Get-Content C:\Windows\setuperr.log

```
```PowerShell
$Proceso=Get-Process -Name notepad
$NombreF='d:\dump\'+(($Proceso).name)+'.dmp'
$Fichero = New-Object IO.FileStream($NombreF,[IO.FileMode]::Create)
(([PSObject].Assembly.GetType('System.Management.Automation.WindowsErrorReporting')).GetNestedType('NativeMethods', 'NonPublic')).GetMethod('MiniDumpWriteDump',[Reflection.BindingFlags] 'NonPublic, Static').Invoke($null, @($Proceso.Handle,$Proceso.Id,$Fichero.SafeFileHandle,[UInt32] 2,[IntPtr]::Zero,[IntPtr]::Zero,[IntPtr]::Zero))
$Fichero.Close()

```
```PowerShell
#Probar contraseñas de forma aleatoria que tengan 8 letras
while(1)
{
$postParams = @{user='juan';pass=(((65..90) + (97..122) | Get-Random -Count 8 | % {[char]$_}) -join "")}
$postParams
Start-Sleep -Seconds 5
$web=Invoke-WebRequest -Uri 'https://localhost/examplepost.php' -Method Post -Body $postParams
$web.content
}

```
