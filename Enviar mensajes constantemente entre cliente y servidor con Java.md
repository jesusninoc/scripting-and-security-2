# Enviar mensajes constantemente entre cliente y servidor con Java
## Java, Network 
### URL: https://www.jesusninoc.com/2018/02/02/enviar-mensajes-constantemente-entre-cliente-y-servidor-con-java/
```Java
import java.io.*;
import java.net.*;

public class Server
{
    public static void main(String[] args)
    {
        int port=2050;
        while(true) {
            try {
                ServerSocket serverSocket = new ServerSocket(port);

                Socket clientSocket = serverSocket.accept();

                PrintWriter out = new PrintWriter(clientSocket.getOutputStream(), true);
                BufferedReader in = new BufferedReader(new InputStreamReader(clientSocket.getInputStream()));

                String inputLine = in.readLine();
                System.out.println("Receive: " + inputLine);
                String outputLine = inputLine.toUpperCase();
                System.out.println("Send: " + outputLine);
                out.println(outputLine);

                out.close();
                in.close();

                clientSocket.close();
                serverSocket.close();
            } catch (UnknownHostException e) {
                System.out.println(e);
            } catch (IOException e) {
                System.out.println(e);
            }
        }
    }
}

```
```Java
import java.io.*;
import java.net.*;

public class Client
{
    public static void main(String[] args)
    {
        int port=2050;
        while(true) {
            try {
                Socket clientSocket = new Socket("localhost", port);

                PrintWriter out = new PrintWriter(clientSocket.getOutputStream(), true);
                BufferedReader in = new BufferedReader(new InputStreamReader(clientSocket.getInputStream()));

                System.out.println("Send: Hi");
                out.println("Hi");
                System.out.println("Receive: " + in.readLine());

                out.close();
                in.close();
                clientSocket.close();
            } catch (UnknownHostException e) {
                System.out.println(e);
            } catch (IOException e) {
                System.out.println(e);
            }
        }
    }
}

```
