# Crear y compilar una DLL con Microsoft Visual C#
## C# 
### URL: https://www.jesusninoc.com/2018/04/16/crear-y-compilar-una-dll-con-microsoft-visual-c/
```C#
namespace Hola
{ 
	public class Hola
	{
		public static void Main()
		{
			System.Console.WriteLine("Hola");
		}
	}
}

```
```PowerShell
csc /target:library hola.cs

```
