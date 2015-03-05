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

## Producer-Consumer Problem

```C
sturct sp {
    sem_t mutex; /* initialized with 1 */
    sem_t slots; /* available spaces, initialized with n */
    sem_t items; /* initialized with 0 */
}
```
#### Producers
```C
void produce(*sp) {
    P(&sp->slots);
    P(&sp->mutex);
    /* insert one item */
    V(&sp->mutex);
    V(&sp->items);
}
```

#### Consumer
```C
void consumer(*sp) {
    P(&sp->items);
    P(&sp->mutex);
    /* remove one item */
    V(&sp->mutex);
    V(&sp->slots);
}
```
