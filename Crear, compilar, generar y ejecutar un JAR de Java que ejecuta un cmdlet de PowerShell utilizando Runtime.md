# Crear, compilar, generar y ejecutar un JAR de Java que ejecuta un cmdlet de PowerShell utilizando Runtime
## Java 
### URL: https://www.jesusninoc.com/2018/02/09/crear-compilar-generar-y-ejecutar-un-jar-de-java-que-ejecuta-un-cmdlet-de-powershell-utilizando-runtime/
```Java
import java.io.*;

public class CrearJava
{
    public static void main(String[] args)
    {
        FileWriter fichero = null;
        PrintWriter pw = null;
        try
        {
            fichero = new FileWriter("EjecutarPowerShell.java");
            pw = new PrintWriter(fichero);
            pw.println("import java.io.IOException;");
            pw.println("import java.io.BufferedReader;");
            pw.println("import java.io.IOException;");
            pw.println("import java.io.InputStreamReader;");
            pw.println("public class EjecutarPowerShell");
            pw.println("{");
            pw.println("	public static void main(String[] args) throws InterruptedException");
            pw.println("	{		");
            pw.println("		Runtime runtime = Runtime.getRuntime();");
            pw.println("		try");
            pw.println("		{");
            pw.println("			Process process = runtime.exec(\"powershell.exe  $PSVersionTable.PSVersion\");");
            pw.println("			");
            pw.println("			process.getOutputStream().close();");
            pw.println("			String line;");
            pw.println("			BufferedReader stdout = new BufferedReader(new InputStreamReader(process.getInputStream()));");
            pw.println("			while ((line = stdout.readLine()) != null){");
            pw.println("				System.out.println(line);");
            pw.println("			}");
            pw.println("		}");
            pw.println("		catch(IOException ex){");
            pw.println("			System.exit(-1);");
            pw.println("		}");
            pw.println("	}");
            pw.println("}");
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
           try {
           if (null != fichero)
              fichero.close();
           } catch (Exception e2) {
              e2.printStackTrace();
           }
        }
	
	//Compilar y crear un fichero JAR que ejecutar el fichero creado EjecutarPowerShell.java
	Runtime runtime = Runtime.getRuntime();
		try
		{
			Process process = runtime.exec("javac EjecutarPowerShell.java");
			
			process.getOutputStream().close();
			String line;
			BufferedReader stdout = new BufferedReader(new InputStreamReader(process.getInputStream()));
			while ((line = stdout.readLine()) != null){
				System.out.println(line);
			}

			Process process2 = runtime.exec("jar cf EjecutarPowerShell EjecutarPowerShell.class");
			
			process2.getOutputStream().close();
			String line2;
			BufferedReader stdout2 = new BufferedReader(new InputStreamReader(process2.getInputStream()));
			while ((line2 = stdout2.readLine()) != null){
				System.out.println(line2);
			}

			Process process3 = runtime.exec("java EjecutarPowerShell");
			
			process3.getOutputStream().close();
			String line3;
			BufferedReader stdout3 = new BufferedReader(new InputStreamReader(process3.getInputStream()));
			while ((line3 = stdout3.readLine()) != null){
				System.out.println(line3);
			}  
		}
		catch(IOException ex){
			System.err.println("Error");
			System.exit(-1);
		}
	}
}

```
