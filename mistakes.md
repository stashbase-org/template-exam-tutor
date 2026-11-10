# Mistakes

Every question I got wrong or partly right, by topic. Open ones come back in quizzes as new questions on the same point, until I get them right. Read this through before the exam.

## CPU scheduling

### Round robin: a new arrival joins the queue before the process just preempted

**Status:** To retry · missed Nov 4 and Nov 9

**Question:** (CPU scheduling, 6 marks) Round robin with quantum 2. P1 arrives at 0 with burst 4, P2 at 2 with burst 3, P3 at 3 with burst 2. Find the average waiting time.

**My answer:** 2.33. At time 2, I put P1 back in the queue ahead of P2.

**Right answer:** 3. At time 2, P2 arrives just as P1's quantum ends, and in our course the new arrival goes in first. Waiting times: P1 2, P2 4, P3 3.

```
| P1 | P2 | P1 | P3 | P2 |
0    2    4    6    8    9
```

**Covered in:** [CPU scheduling](notes/cpu-scheduling.md), class notes lecture 8

### SRTF: waiting time is TAT − burst, not start − arrival

**Status:** Fixed Nov 6 · missed Nov 4

**Question:** (CPU scheduling, 4 marks) SRTF. P1 arrives at 0 with burst 7, P2 at 1 with burst 4, P3 at 2 with burst 1. Find each process's waiting time.

**My answer:** 0 for all three, since each one started running as soon as it arrived.

**Right answer:** P1 5, P2 1, P3 0. P1 and P2 were both preempted, and waited again later. Chart: P1 0–1, P2 1–2, P3 2–3, P2 3–6, P1 6–12. WT = TAT − burst: P1 12 − 7 = 5, P2 5 − 4 = 1, P3 1 − 1 = 0.

**Covered in:** [CPU scheduling](notes/cpu-scheduling.md)

## Deadlocks

### Banker's algorithm: compare Need, not Max, with Available

**Status:** To retry · missed Nov 5

**Question:** (Deadlocks, 8 marks) Resources A, B, C, with Available (1, 1, 1). Allocation: P0 (1, 0, 1), P1 (2, 1, 1), P2 (1, 1, 0), P3 (0, 0, 2). Max: P0 (3, 2, 2), P1 (3, 2, 2), P2 (4, 2, 1), P3 (1, 1, 3). Is the system safe?

**My answer:** Unsafe, because no process's Max fits in Available.

**Right answer:** Safe. Need = Max − Allocation: P0 (2, 2, 1), P1 (1, 1, 1), P2 (3, 1, 1), P3 (1, 1, 1). P1's Need fits; when it finishes, Work becomes (3, 2, 2), and the rest follow. One safe sequence is P1, P2, P3, P0. Others count too.

**Covered in:** [Deadlocks](notes/deadlocks.md), Ananya's notes

## Paging and the TLB

### EAT: a TLB miss still pays for the TLB lookup

**Status:** To retry · missed Nov 6

**Question:** (Paging, 4 marks) Memory access takes 80 ns, a TLB lookup 10 ns, and the hit ratio is 90%. Find the effective access time.

**My answer:** 97 ns. I took the miss path as 80 + 80 = 160 ns.

**Right answer:** 98 ns. The TLB is checked first either way, so a miss costs 10 + 80 + 80 = 170 ns. EAT = 0.9 × 90 + 0.1 × 170 = 81 + 17 = 98 ns.

**Covered in:** [Paging and the TLB](notes/paging.md), class notes lectures 14–16

### Page table size: offset bits come from this page size, not 12 by habit

**Status:** To retry · missed Nov 9

**Question:** (Paging, 4 marks) A system has 32-bit logical addresses, 8 KB pages, and 4-byte page table entries. How big is a process's page table?

**My answer:** 4 MB. I used a 12-bit offset, like in the 2024 paper.

**Right answer:** 2 MB. 8 KB = 2^13 bytes, so the offset is 13 bits, leaving 19 bits for the page number. 2^19 entries × 4 bytes = 2^21 bytes = 2 MB.

**Covered in:** [Paging and the TLB](notes/paging.md)

## Page replacement

### Belady's anomaly happens with FIFO only

**Status:** Fixed Nov 7 · missed Nov 3

**Question:** (Page replacement, 2 marks) Which of FIFO, LRU, and Optimal can show Belady's anomaly?

**My answer:** FIFO and LRU.

**Right answer:** FIFO only. LRU and Optimal are stack algorithms: the pages they keep with n frames are always among those they'd keep with n + 1, so adding frames never adds faults.

**Covered in:** [Page replacement](notes/page-replacement.md)
