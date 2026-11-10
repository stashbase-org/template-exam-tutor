# Operating Systems

Study notes for my Operating Systems end-semester exam, one page per topic. Built from my class notes, Ananya's notes on deadlocks, chapters of OSTEP, and the 2023 and 2024 papers.

## What to work on

* **Paging calculations keep slipping.** Two open mistakes, both small steps: the TLB lookup on a miss, and offset bits for 8 KB pages. Paging is in Part B every year. See [Paging and the TLB](paging.md).
* **Round robin ties, missed twice.** When a new process arrives just as a quantum ends, it goes in the queue first. See [CPU scheduling](cpu-scheduling.md).
* **Synchronization hasn't been quizzed yet.** Both past papers have a semaphore question in Part B. See [Process synchronization](synchronization.md).
* **Unit 5 isn't in my materials.** File systems and disk scheduling are two of the seven Part B questions each year, and 4 marks in Part A. [OSTEP ch. 37: Hard Disk Drives](https://pages.cs.wisc.edu/~remzi/OSTEP/file-disks.pdf) covers disk scheduling.

## Topics

| Topic | In one line | How I'm doing | Last quizzed |
| --- | --- | --- | --- |
| [CPU scheduling](cpu-scheduling.md) | FCFS, SJF, SRTF, priority, round robin; Gantt charts and waiting times by hand | Getting there | Nov 9 |
| [Process synchronization](synchronization.md) | Race conditions, the critical section, locks, semaphores, producer–consumer | Not quizzed yet | – |
| [Deadlocks](deadlocks.md) | The four conditions, allocation graphs, prevention, Banker's algorithm | Getting there | Nov 5 |
| [Paging and the TLB](paging.md) | Pages and frames, address translation, page table size, effective access time | Shaky | Nov 9 |
| [Page replacement](page-replacement.md) | FIFO, LRU, Optimal, Belady's anomaly, thrashing | Solid | Nov 7 |

## Materials

| Material | What it is | Topics |
| --- | --- | --- |
| [OS_lec6-8_scheduling](../library/OS_lec6-8_scheduling.md) | Class notes, lectures 6–8 | CPU scheduling |
| [paging_tlb_classnotes](../library/paging_tlb_classnotes.md) | Class notes, lectures 14–16 | Paging |
| [deadlock-notes-from-ananya](../library/deadlock-notes-from-ananya.md) | A friend's notes on Unit 3 | Deadlocks |
| [doubts](../library/doubts.md) | My list of questions to clear up | All |
| [PYQ_2024_endsem](../library/PYQ_2024_endsem.md) | The 2024 end-semester paper, in full | All, plus Unit 5 |
| [PYQ_2023_partB](../library/PYQ_2023_partB.md) | The 2023 end-semester paper, Part B only | All, plus Unit 5 |
| [OSTEP ch. 7: CPU Scheduling](https://pages.cs.wisc.edu/~remzi/OSTEP/cpu-sched.pdf) | Textbook chapter, online | CPU scheduling |
| [OSTEP ch. 18: Introduction to Paging](https://pages.cs.wisc.edu/~remzi/OSTEP/vm-paging.pdf) | Textbook chapter, online | Paging |
| [OSTEP ch. 19: Translation Lookaside Buffers](https://pages.cs.wisc.edu/~remzi/OSTEP/vm-tlbs.pdf) | Textbook chapter, online | Paging |
| [OSTEP ch. 22: Swapping: Policies](https://pages.cs.wisc.edu/~remzi/OSTEP/vm-beyondphys-policy.pdf) | Textbook chapter, online | Page replacement |
| [OSTEP ch. 28: Locks](https://pages.cs.wisc.edu/~remzi/OSTEP/threads-locks.pdf) | Textbook chapter, online | Synchronization |
| [OSTEP ch. 31: Semaphores](https://pages.cs.wisc.edu/~remzi/OSTEP/threads-sema.pdf) | Textbook chapter, online | Synchronization |
| [OSTEP ch. 32: Concurrency Bugs](https://pages.cs.wisc.edu/~remzi/OSTEP/threads-bugs.pdf) | Textbook chapter, online | Deadlocks |
