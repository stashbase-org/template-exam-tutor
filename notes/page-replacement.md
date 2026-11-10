# Page replacement

Which page to evict when a page fault finds no free frame, counting page faults by hand, and thrashing. There's a page replacement numerical in Part B every year.

**Sources:** [OSTEP ch. 22: Swapping: Policies](https://pages.cs.wisc.edu/~remzi/OSTEP/vm-beyondphys-policy.pdf) · [2024 paper](../library/PYQ_2024_endsem.md) Q7, Q8, Q15 · [2023 paper](../library/PYQ_2023_partB.md) Q15
**My mistakes:** [Mistakes › Page replacement](../mistakes.md#page-replacement)

## Key ideas

* **The goal:** the fewest page faults. Loading a page into an empty frame counts as a fault too.
* **FIFO:** evict the page that came in first. Simple, but it can throw out a page that's still in heavy use.
* **Optimal (OPT):** evict the page that won't be used for the longest time. No algorithm has fewer faults, but it needs to know the future, so it's a yardstick, not something an OS can run.
* **LRU:** evict the page that hasn't been used for the longest time. Usually close to Optimal. Exact LRU is costly, so real systems approximate it with a reference bit. The clock, or second-chance, algorithm skips a page whose bit is set, clearing the bit, and evicts the first page it finds with the bit clear.
* **Belady's anomaly:** with FIFO, more frames can mean more faults. LRU and Optimal never do this. They're stack algorithms: the pages kept with n frames are always among those kept with n + 1.
* **Thrashing:** when processes have too few frames, they fault constantly and spend more time paging than running. CPU use drops, and an OS that responds by adding processes makes it worse. The working-set model keeps each process's recently used pages in memory, and suspends a process when they don't all fit.

## How to work it out

Make a table: one column per reference, one row per frame. For each reference, write the frames' contents, and mark a fault. Then count.

* **FIFO:** replace the page that's been in memory longest.
* **LRU:** look back. Replace the page whose last use is furthest back.
* **Optimal:** look ahead. Replace the page whose next use is furthest away, or that's never used again.

Example, the string from 2023 Q15: 1 2 3 4 1 2 5 1 2 3 4 5, with 3 frames, FIFO.

| Reference | 1 | 2 | 3 | 4 | 1 | 2 | 5 | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Frame 1 | 1 | 1 | 1 | 4 | 4 | 4 | 5 | 5 | 5 | 5 | 5 | 5 |
| Frame 2 | | 2 | 2 | 2 | 1 | 1 | 1 | 1 | 1 | 3 | 3 | 3 |
| Frame 3 | | | 3 | 3 | 3 | 2 | 2 | 2 | 2 | 2 | 4 | 4 |
| Fault | F | F | F | F | F | F | F | | | F | F | |

9 faults. On the same string with 3 frames, LRU gives 10 and Optimal 7. With 4 frames, FIFO gives 10: more frames, more faults. That's Belady's anomaly, and it's the comment the question asks for.

## Common traps

* **Belady's anomaly is FIFO only.**
* **LRU looks back, Optimal looks ahead.** Mixing up the direction is the usual slip.
* **LRU doesn't always beat FIFO.** On the string above, it has more faults. Count; don't assume.
* **Ties in Optimal:** when several pages are never used again, evicting any of them is fine. Say which one you chose.

## How it's asked

* **Part B, every year:** a reference string, and the faults for FIFO, LRU, and Optimal with 3 frames, sometimes 4 too, 12 marks (2024 Q15, 2023 Q15). Then 4 marks of theory: thrashing and the working set (2024), second chance (2023).
* **Part A:** Belady's anomaly and thrashing (2024 Q7, Q8).
