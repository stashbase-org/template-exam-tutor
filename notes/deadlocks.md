# Deadlocks

When processes wait on each other forever, the four conditions behind it, and how an OS prevents, avoids, or detects it. Banker's algorithm is the numerical that comes up.

**Sources:** [OSTEP ch. 32: Concurrency Bugs](https://pages.cs.wisc.edu/~remzi/OSTEP/threads-bugs.pdf) · [Ananya's notes on Unit 3](../library/deadlock-notes-from-ananya.md) · [2024 paper](../library/PYQ_2024_endsem.md) Q5, Q13 · [2023 paper](../library/PYQ_2023_partB.md) Q13
**My mistakes:** [Mistakes › Deadlocks](../mistakes.md#deadlocks)

## Key ideas

* **Deadlock:** each process in a set waits for a resource that another process in the set holds, so none of them can go on.
* **Four conditions, all needed at once:** mutual exclusion, hold and wait, no preemption, circular wait. Break any one and deadlock can't happen.
* **Resource allocation graph:** a request edge goes from a process to a resource, an assignment edge from a resource to a process. If each resource has one instance, a cycle means deadlock. With several instances, a cycle means deadlock is possible, not certain.
* **Four ways to handle it:**
  * Prevention: make one condition impossible. The practical one is circular wait: number the resources, and always request them in increasing order.
  * Avoidance: grant a request only if the system stays in a safe state. That's Banker's algorithm.
  * Detection and recovery: let it happen, find it, then kill processes or take resources back.
  * Ignore it: what most desktop systems do, since it's rare.
* **Safe state:** there's an order, a safe sequence, in which every process can get what it still needs and finish. Unsafe doesn't mean deadlocked, only that deadlock can no longer be ruled out.

## How to work it out

Banker's algorithm, the safety check:

1. Need = Max − Allocation, for every process.
2. Start with Work = Available. Find a process that isn't done and whose Need ≤ Work, for every resource type.
3. Let it finish: Work = Work + its Allocation. Mark it done.
4. Repeat. If all of them finish, the system is safe, and the order is a safe sequence. If none fits, it's unsafe.

For a request: it must be within the process's Need and within Available. Pretend to grant it: Available − Request, Allocation + Request, Need − Request. Run the safety check, and grant it only if the result is safe.

Example: resources A and B, Available (2, 1).

| Process | Allocation | Max | Need |
| --- | --- | --- | --- |
| P0 | 1 0 | 3 2 | 2 2 |
| P1 | 1 1 | 2 2 | 1 1 |
| P2 | 0 1 | 3 1 | 3 0 |

Work (2, 1): P1 fits, so Work becomes (3, 2). P2 fits: (3, 3). P0 fits: (4, 3). Safe, with the sequence P1, P2, P0.

Now P0 requests (1, 1). It's within P0's Need and within Available. Pretend: Available becomes (1, 0), and P0's Need (1, 1). No process's Need fits in (1, 0), so the state would be unsafe. P0 waits, even though the resources are free right now.

## Common traps

* **Compare Need, not Max, with Available.**
* **When a process finishes, add back its Allocation,** not its Need or Max.
* **Any safe sequence counts.** There's often more than one.
* **A cycle means deadlock only when each resource has one instance.**
* **Unsafe isn't deadlocked.**

## How it's asked

* **Part B, every year:** a deadlock numerical, 12 marks or so, plus theory. 2024 Q13: Banker's algorithm with a request, then prevention vs. avoidance. 2023 Q13: drawing a resource allocation graph, then the detection algorithm.
* **Part A:** the four conditions (2024 Q5).
