# Realizar una suma de dos números en lenguaje ensamblador con QtSpim
## Assembler 
### URL: https://www.jesusninoc.com/2017/09/26/realizar-una-suma-de-dos-numeros-en-lenguaje-ensamblador-con-qtspim/
```Assembly (x86)
## Program adds 1 and 12
.text                   # text section
.globl  main            # call main by SPIM

main:   
ori     $8,$0,0x1       # load 1 into register 8
ori     $9,$0,0x2       # load 2 into register 9
add     $10,$8,$9       # add registers 8 and 9, put result in register 10
jr $ra

```
