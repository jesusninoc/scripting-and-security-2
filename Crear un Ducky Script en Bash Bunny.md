# Crear un Ducky Script en Bash Bunny
## Bunny scripts, Ducky scripts 
### URL: https://www.jesusninoc.com/2017/04/21/crear-un-ducky-script-en-bash-bunny/
```PowerShell
DELAY 3000
GUI r
DELAY 200
STRING notepad
ENTER
DELAY 2000
STRING Hola
ENTER

```
```PowerShell
LED G
ATTACKMODE HID STORAGE

# Set your language here
LANGUAGE='es'
DUCKY_LANG='es'

LED R G
# Check for switch position to make it easier for us. (can be replaced in the future with bunny helpers)
check_switch() {
	switch1=`cat /sys/class/gpio_sw/PA8/data`
	switch2=`cat /sys/class/gpio_sw/PL4/data`
	switch3=`cat /sys/class/gpio_sw/PL3/data`
	echo "--- switch1 = $switch1, switch2 = $switch2, switch3 = $switch3"
	if [ "x$switch1" = "x0" ] && [ "x$switch2" = "x1" ] && [ "x$switch3" = "x1" ]; then
		SWITCH_POSITION="switch1"
	elif [ "x$switch1" = "x1" ] && [ "x$switch2" = "x0" ] && [ "x$switch3" = "x1" ]; then
		SWITCH_POSITION="switch2"
	elif [ "x$switch1" = "x1" ] && [ "x$switch2" = "x1" ] && [ "x$switch3" = "x0" ]; then
		SWITCH_POSITION="switch3"
	else
		SWITCH_POSITION="invalid"
	fi
}

check_switch

if [ -f "/root/udisk/payloads/${SWITCH_POSITION}/ducky_script.txt" ]; then
        QUACK ${SWITCH_POSITION}/ducky_script.txt
        LED G
else
    LED R
    echo "Unable to load ducky_script.txt" >> /root/debuglog.txt
        exit 1
fi

```
