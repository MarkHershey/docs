# Concurrency in Java

### CyclicBarrier

```
java.util.concurrent.CyclicBarrier
```

CyclicBarrier is used to make threads wait for each other. It is used when different threads process a part of computation and when all threads have completed the execution, the result needs to be combined in the parent thread. In other words, a CyclicBarrier is used when multiple thread carry out different sub tasks and the output of these sub tasks need to be combined to form the final output.

Ref:

- [GeeksforGeeks: CyclicBarrier in Java](https://www.geeksforgeeks.org/java-util-concurrent-cyclicbarrier-java/)


### CountDownLatch

```
java.util.concurrent.CountDownLatch
```

CountDownLatch is used to make sure that a particular task waits for some other threads (to count down) before it starts. In application, the main thread can wait for some setup threads to finish setup works before continuing.


Ref:

- [GeeksforGeeks: CountDownLatch in Java](https://www.geeksforgeeks.org/countdownlatch-in-java/)


### Phaser

```
java.util.concurrent.Phaser
```

Phaser's primary purpose is to enable synchronization of threads that represent one or more phases of activity.

Ref:

- [GeeksforGeeks: Phaser in Java](https://www.geeksforgeeks.org/java-util-concurrent-phaser-class-in-java-with-examples/)

