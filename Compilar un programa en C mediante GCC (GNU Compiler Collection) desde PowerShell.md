# Compilar un programa en C mediante GCC (GNU Compiler Collection) desde PowerShell
## Automation, Bash, C, PowerShell 
### URL: https://www.jesusninoc.com/2018/06/23/compilar-un-programa-en-c-mediante-gcc-gnu-compiler-collection-desde-powershell/
```PowerShell
$codigo = '#include <stdio.h>
int main()
{
        printf(\"Hola Mundo.\\n\");
        return 0;
}'

wsl echo $codigo > hola.c
bash -c "iconv hola.c -f UTF-16 -t UTF-8 > holas.c"
wsl gcc holas.c
wsl "./a.out"

```
```PowerShell
$codigo = '#include <stdio.h>
int main()
{
        printf("Hola Mundo PowerShell.\n");
        return 0;
}'

$codigo | Out-File hola.c
bash -c "iconv hola.c -f UTF-16 -t UTF-8 > holas.c"
wsl gcc holas.c
wsl "./a.out"

```
