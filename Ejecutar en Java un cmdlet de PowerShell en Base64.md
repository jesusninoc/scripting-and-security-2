# Ejecutar en Java un cmdlet de PowerShell en Base64
## Java, PowerShell 
### URL: https://www.jesusninoc.com/2018/02/10/ejecutar-en-java-un-cmdlet-de-powershell-en-base64/
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
			Process process = runtime.exec("powershell.exe -encodedcommand RwBlAHQALQBQAHIAbwBjAGUAcwBzAA==");
			
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
