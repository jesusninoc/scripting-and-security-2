# Serializar y deserializar contenido en un fichero en Java
## Java 
### URL: https://www.jesusninoc.com/2018/01/05/serializar-y-deserializar-contenido-en-un-fichero-en-java/
```Java
import java.io.*;
import java.util.Date;

public class Serializar {
    public static void main(String[] args) {
        try {
            FileOutputStream fos = new FileOutputStream("fichero.txt");
            ObjectOutputStream sos = new ObjectOutputStream(fos);
            sos.writeObject("Fecha actual");
            sos.writeObject(new Date());
            sos.close();
        }
        catch (FileNotFoundException ex) {
            ex.printStackTrace();
        }
        catch (IOException ex) {
            ex.printStackTrace();
        }
    }
}

```
```Java
import java.io.*;
import java.util.Date;

public class Deserializar {
    public static void main(String[] args) {
        try {
            FileInputStream fis = new FileInputStream("fichero.txt");
            ObjectInputStream sis = new ObjectInputStream(fis);
            System.out.println((String)sis.readObject());
            System.out.println((Date)sis.readObject());
            sis.close();
        }
        catch (FileNotFoundException ex) {
            ex.printStackTrace();
        }
        catch (IOException ex) {
            ex.printStackTrace();
        }
        catch(ClassNotFoundException ex) {
            ex.printStackTrace();
        }
    }
}

```
