# Ejecutar un código sobre un contenedor Docker con PHP y la extensión pthreads
## PHP 
### URL: https://www.jesusninoc.com/2018/04/03/ejecutar-un-codigo-sobre-un-contenedor-docker-con-php-y-la-extension-pthreads/
```PHP
<?php
$thread = new class extends Thread {
    public function run() {
        echo "Hello World\n";
    }
};

$thread->start() && $thread->join();
?>

```
```Shell
docker run -it -v $(pwd):/app jdecool/php-pthreads -f ejemplo.php

```
