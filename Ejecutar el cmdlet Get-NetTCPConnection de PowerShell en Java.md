# Ejecutar el cmdlet Get-NetTCPConnection de PowerShell en Java
## Java, Network, PowerShell 
### URL: https://www.jesusninoc.com/2018/02/08/ejecutar-el-cmdlet-get-nettcpconnection-de-powershell-en-java/
```Java
import java.io.IOException;
import java.util.concurrent.TimeUnit;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class ProcesoPowerShell
{
	public static void main(String[] args) throws InterruptedException
	{		
		Runtime runtime = Runtime.getRuntime();
		try
		{
			Process process = runtime.exec("powershell.exe  Get-NetTCPConnection");
			
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
