## Read-Write Problem

#### Readers
```C
int readcnt; /* initialized with 0 */
sem_t mutex, w; /* initialized with 1 */
void reader(void) {
    while(1) {
        P(&mutex);
        readcnt++;
        if (readcnt == 1) P(&w);
        V(&mutex);

        /* do reading */

        P(&mutex);
        readcnt--;
        if (readcnt == 0) V(&w);
        V(&mutex);
    }
}
```
#### Writers
```C
void writer(void) {
    while(1) {
        P(&w);

        /* do writing */

        V(&w);
    }
}
```
