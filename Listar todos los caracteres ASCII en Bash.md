# Listar todos los caracteres ASCII en Bash
## Bash 
### URL: https://www.jesusninoc.com/2017/10/05/listar-todos-los-caracteres-ascii-en-bash/
```Shell
for (( i=0; i <= 255; i++ )); do printf "\x$(printf %x $i)"; done

```
