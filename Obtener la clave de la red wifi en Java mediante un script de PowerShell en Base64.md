# Obtener la clave de la red wifi en Java mediante un script de PowerShell en Base64
## Java, Network, PowerShell, Security 
### URL: https://www.jesusninoc.com/2018/01/12/obtener-la-clave-de-la-red-wifi-en-java-mediante-un-script-de-powershell-en-base64/
```Java
import java.io.IOException;
import java.util.concurrent.TimeUnit;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class ProcesoBase
{
	public static void main(String[] args) throws InterruptedException
	{		
		Runtime runtime = Runtime.getRuntime();
		try
		{
			Process process = runtime.exec("powershell.exe -encodedcommand KABuAGUAdABzAGgAIAB3AGwAYQBuACAAcwBoAG8AdwAgAGkAbgB0AGUAcgBmAGEAYwBlACAAfAAgAFMAZQBsAGUAYwB0AC0AUwB0AHIAaQBuAGcAIABTAFMASQBEACkAWwAwAF0AIAB8ACAAJQB7AFsAUwB0AHIAaQBuAGcAXQAkAFMAUwBJAEQAPQAkAF8AOwAkAFMAUwBJAEQAPQAkAFMAUwBJAEQALgByAGUAcABsAGEAYwBlACgAIgBTAFMASQBEACIALAAiACIAKQAuAHIAZQBwAGwAYQBjAGUAKAAiADoAIgAsACIAIgApAC4AdAByAGkAbQAoACkAOwAkAFMAUwBJAEQAOwBuAGUAdABzAGgAIAB3AGwAYQBuACAAcwBoAG8AdwAgAHAAcgBvAGYAaQBsAGUAIABuAGEAbQBlAD0AJABTAFMASQBEACAAawBlAHkAPQBjAGwAZQBhAHIAIAB8ACAAUwBlAGwAZQBjAHQALQBTAHQAcgBpAG4AZwAgACcAQwBvAG4AdABlAG4AaQBkAG8AIABkAGUAIABsAGEAIABjAGwAYQB2AGUAJwA7AH0A");
			
			process.getOutputStream().close();
			String line;
			BufferedReader stdout = new BufferedReader(new InputStreamReader(process.getInputStream()));
			while ((line = stdout.readLine()) != null){
				System.out.println(line);
			}

			TimeUnit.SECONDS.sleep(10);
		}
		catch(IOException ex){
			System.err.println("Error");
			System.exit(-1);
		}
	}
}

```
