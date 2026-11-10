# OS End Sem 2024 (PYQ)

CS-301 Operating Systems · B.Tech 5th semester · Nov/Dec 2024
Time: 3 hours · Max marks: 100

## Part A: answer all (10 × 2 = 20)

1. Define turnaround time and waiting time.
2. What is the convoy effect?
3. What is starvation? How does aging solve it?
4. What is a race condition? Give an example.
5. State the necessary conditions for deadlock.
6. What is a TLB? Why is it needed?
7. What is Belady's anomaly?
8. What is thrashing?
9. Differentiate between SCAN and C-SCAN disk scheduling.
10. What is an inode?

## Part B: answer any five (5 × 16 = 80)

**11.** (a) Consider the following processes:

| Process | Arrival | Burst |
| --- | --- | --- |
| P1 | 0 | 6 |
| P2 | 1 | 3 |
| P3 | 2 | 8 |
| P4 | 4 | 2 |
| P5 | 5 | 4 |

Draw Gantt charts and find the average waiting time and average turnaround time for (i) FCFS (ii) SRTF (iii) Round Robin with time quantum 3. [12]

(b) Why can't SJF be implemented exactly? How can the next CPU burst be predicted? [4]

**12.** (a) What is a semaphore? Give a solution to the bounded buffer (producer–consumer) problem using semaphores. [10]

(b) What are the requirements of a solution to the critical section problem? [6]

**13.** (a) Consider the following snapshot of a system with resource types A, B, C. Available = (3, 1, 2).

| Process | Allocation (A B C) | Max (A B C) |
| --- | --- | --- |
| P0 | 1 1 0 | 5 3 2 |
| P1 | 2 0 1 | 3 2 3 |
| P2 | 2 1 2 | 6 1 4 |
| P3 | 1 2 1 | 2 3 2 |
| P4 | 0 1 2 | 4 3 3 |

(i) Find the Need matrix. (ii) Is the system in a safe state? If yes, give a safe sequence. (iii) If P1 requests (1, 0, 2), can it be granted immediately? [12]

(b) Differentiate between deadlock prevention and deadlock avoidance. [4]

**14.** (a) Explain paging hardware with a neat diagram. [6]

(b) A system has a 32-bit logical address and a page size of 4 KB. Each page table entry is 4 bytes. Find the number of pages and the size of the page table. [4]

(c) Memory access time is 100 ns and TLB access time is 20 ns. If the hit ratio is 80%, find the effective memory access time. [6]

**15.** (a) For the reference string 4 1 2 4 3 1 5 2 4 1 3 5 with 3 frames, find the number of page faults using FIFO, LRU, and Optimal page replacement. [12]

(b) What is thrashing? How does the working set model prevent it? [4]

**16.** (a) A disk has 200 cylinders (0–199). The head is at cylinder 50, moving towards 199. The request queue is 82, 170, 43, 140, 24, 16, 190. Find the total head movement for FCFS, SSTF, SCAN, and C-SCAN. [12]

(b) Explain seek time and rotational latency. [4]

**17.** (a) Explain contiguous, linked, and indexed file allocation, with their advantages and disadvantages. [10]

(b) Explain single-level, two-level, and tree-structured directories. [6]
