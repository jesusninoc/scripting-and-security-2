# Espera de hilos en Linux con C
## Bash, C 
### URL: https://www.jesusninoc.com/2018/06/21/espera-de-hilos-en-linux-con-c/
```C
#include <stdlib.h>
#include <pthread.h>
#include <stdio.h>

typedef struct {
        int hilo;
        int *ar;
        long n;
} vector_nuevo;

void *inicializa(void *arg)
{
        long i;

        for (i = 0; i < ((vector_nuevo *)arg)->n; i++)
        ((vector_nuevo *)arg)->ar[i] = 0;
        printf("Hilo %d ejecutando\n", ((vector_nuevo *)arg)->hilo);
}

int main(void)
{
        int ar[1000000];
        pthread_t th1, th2;
        vector_nuevo v_nuevo_1, v_nuevo_2;

        v_nuevo_1.hilo = 1;
        v_nuevo_1.ar = &ar[0];
        v_nuevo_1.n = 500000;
        (void) pthread_create(&th1, NULL, inicializa, &v_nuevo_1);
        v_nuevo_2.hilo = 2;
        v_nuevo_2.ar = &ar[500000];
        v_nuevo_2.n = 500000;
        (void) pthread_create(&th2, NULL, inicializa, &v_nuevo_2);
        (void) pthread_join(th1, NULL);
        (void) pthread_join(th2, NULL);
        return 0;
}

```
```Shell
gcc -pthread -o join join.c

```
