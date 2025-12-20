


```
 OpenJDK 공식 소스 (요약, 핵심만)
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