# Realizar desplazamientos de bits en PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/05/28/realizar-desplazamientos-de-bits-en-powershell/
```PowerShell
#Desplazamiento izquierdo
#Número sin desplazamiento
21 -shl 0
#Ver número en binario sin desplazamiento
[Convert]::ToString(21, 2)
#Número con desplazamiento a la izquierda de un bit
21 -shl 1
#Ver número en binario con desplazamiento a la izquierda de un bit
[Convert]::ToString(21 -shl 1, 2)

#Desplazamiento derecho
#Número sin desplazamiento
21 -shr 0
#Ver número en binario sin desplazamiento
[Convert]::ToString(21, 2)
#Número con desplazamiento a la derecha de un bit
21 -shr 1
#Ver número en binario con desplazamiento a la derecha de un bit
[Convert]::ToString(21 -shr 1, 2)

```
