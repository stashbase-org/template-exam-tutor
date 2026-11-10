# Process synchronization

What goes wrong when processes share data, and how locks and semaphores prevent it. A semaphore question is in Part B every year.

**Sources:** [OSTEP ch. 28: Locks](https://pages.cs.wisc.edu/~remzi/OSTEP/threads-locks.pdf) · [OSTEP ch. 31: Semaphores](https://pages.cs.wisc.edu/~remzi/OSTEP/threads-sema.pdf) · [2024 paper](../library/PYQ_2024_endsem.md) Q4, Q12 · [2023 paper](../library/PYQ_2023_partB.md) Q12

## Key ideas

* **Race condition:** the result depends on the order the processes happen to run in. Two processes each doing count++ load, add, and store; if both load before either stores, one update is lost.
* **Critical section:** the code that touches shared data. A solution needs three things:
  * Mutual exclusion: at most one process inside at a time.
  * Progress: if no one's inside, one of the processes waiting to enter gets in, and the choice isn't put off forever.
  * Bounded waiting: once a process asks to enter, there's a limit on how many times others get in first.
* **Locks:** acquire before the critical section, release after. They're built on atomic hardware instructions like test-and-set or compare-and-swap. A spinlock keeps the CPU busy while it waits; other locks put the waiting process to sleep.
* **Semaphore:** an integer changed only by two atomic operations. wait (P) decrements it, and blocks the process if the value is now negative. signal (V) increments it, and wakes one waiting process if there is one. A binary semaphore (0 or 1) works as a lock; a counting semaphore tracks how many of something are free.
* **Producer–consumer with a buffer of N slots:** three semaphores. mutex = 1 guards the buffer, empty = N counts free slots, full = 0 counts filled ones.

```
Producer                 Consumer
wait(empty)              wait(full)
wait(mutex)              wait(mutex)
  add item to buffer       take item from buffer
signal(mutex)            signal(mutex)
signal(full)             signal(empty)
```

* **The other classic problems,** readers–writers and dining philosophers, aren't in these materials yet. Dining philosophers came up in 2023.

## Common traps

* **wait(empty) comes before wait(mutex).** Swap them, and a producer can take the mutex, then block on a full buffer. The consumer can never get the mutex to empty it: deadlock.
* **Progress vs. bounded waiting:** progress is about someone getting in; bounded waiting is about a particular process getting in eventually.
* **A signal is never lost.** With no one waiting, it raises the count, and the next wait goes straight through.

## How it's asked

* **Part B, every year:** semaphores applied to a classic problem, 10 marks, plus theory. 2024 Q12: producer–consumer, and the three requirements of the critical section. 2023 Q12: dining philosophers, and binary vs. counting semaphores.
* **Part A:** a race condition, with an example (2024 Q4).
