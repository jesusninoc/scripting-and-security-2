# Hacer clic en una posición de la pantalla con Java
## Automation, Java 
### URL: https://www.jesusninoc.com/2017/12/20/hacer-clic-en-una-posicion-de-la-pantalla-con-java/
```Java
import java.awt.Robot;
import java.awt.event.InputEvent;

public class Robots
{
	public static void main(String[] args) throws Exception
	{
		Robot r = new Robot();
		r.mouseMove(10,10);
		r.mousePress(InputEvent.BUTTON1_MASK);
	}
}

```
