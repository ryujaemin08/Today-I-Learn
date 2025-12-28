


```java
// OpenJDK 공식 소스 (요약, 핵심만)
public RunnableScheduledFuture<?> take() throws InterruptedException {
    for (;;) {
        RunnableScheduledFuture<?> first = queue[0];
        if (first == null)
            available.await();
        else {
            long delay = first.getDelay(NANOSECONDS);
            if (delay <= 0)
                return finishPoll(first);
            if (leader != null)
                available.await();
            else {
                Thread thisThread = Thread.currentThread();
                leader = thisThread;
                try {
                    available.awaitNanos(delay);
                } finally {
                    if (leader == thisThread)
                        leader = null;
                }
            }
        }
    }
}

```





[ ]

[ ]Condition.awaitNano() 시 어떻게 나노초만큼 기다릴 수 있게 타이머가 작동하는지


Condition.awaitNano() 시 지정한 나노초 만큼 자신의 쓰래드를 대기 시킨다.
Condition.await() 시 자신의 쓰레드를 대기시킨다.



Condition.signal() 시 지정한 대기중이였던 쓰레드를 실행 가능한 상태로 전환함 (깨운다.)