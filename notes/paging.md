# Paging and the TLB

How a logical address becomes a physical one, and the numericals around it: address translation, page table size, and effective access time. In Part B every year.

**Sources:** [OSTEP ch. 18: Introduction to Paging](https://pages.cs.wisc.edu/~remzi/OSTEP/vm-paging.pdf) · [OSTEP ch. 19: Translation Lookaside Buffers](https://pages.cs.wisc.edu/~remzi/OSTEP/vm-tlbs.pdf) · [Class notes, lectures 14–16](../library/paging_tlb_classnotes.md) · [2024 paper](../library/PYQ_2024_endsem.md) Q6, Q14 · [2023 paper](../library/PYQ_2023_partB.md) Q14
**My mistakes:** [Mistakes › Paging and the TLB](../mistakes.md#paging-and-the-tlb)

## Key ideas

* **Pages and frames:** logical memory is split into fixed-size pages, physical memory into frames of the same size. Any page can go in any frame, so there's no external fragmentation, only internal fragmentation in a process's last page.
* **The address:** a logical address is a page number p and an offset d. With pages of 2^n bytes, the offset is the low n bits, and the page number is the rest.
* **The page table:** one per process, mapping each page to a frame. The page-table base register (PTBR) points to it. Each entry also has bits like valid, protection, and dirty.
* **The TLB:** with only a page table, every access costs two memory accesses, one for the entry and one for the data. The TLB is a small, fast cache of recent translations. On a hit, the frame comes from the TLB. On a miss, it comes from the page table, and the entry goes into the TLB.
* **Effective access time:** with TLB lookup time t, memory access time m, and hit ratio h, our course uses EAT = h(t + m) + (1 − h)(t + 2m).
* **Big page tables:** 32-bit addresses with 4 KB pages need 2^20 entries; at 4 bytes each, that's 4 MB per process. Multi-level paging pages the page table itself, so its unused parts take no memory. An inverted page table has one entry per frame instead of one per page.

## How to work it out

**Page table size:** offset bits = log2(page size). Entries = 2^(address bits − offset bits). Size = entries × entry size.
Example: 32-bit addresses, 16 KB pages, 4-byte entries. 16 KB = 2^14, so 14 offset bits and 2^18 entries. 2^18 × 4 = 2^20 bytes = 1 MB.

**Address translation:** page = address ÷ page size, offset = the remainder. Physical address = frame × page size + offset.
Example: 1 KB pages, logical address 2500. Page 2, offset 2500 − 2048 = 452. If page 2 is in frame 5, the physical address is 5 × 1024 + 452 = 5572.

**EAT:** write out the hit path and the miss path, then weight them.
Example: t = 10 ns, m = 100 ns, h = 95%. Hit: 10 + 100 = 110 ns. Miss: 10 + 100 + 100 = 210 ns. EAT = 0.95 × 110 + 0.05 × 210 = 104.5 + 10.5 = 115 ns.

## Common traps

* **The TLB lookup counts on a miss too:** the miss path is t + 2m, not 2m. Some books treat the lookup as free on a miss; our class notes don't. If a question says to ignore TLB time, drop it.
* **Offset bits come from this question's page size.** 12 bits is only for 4 KB pages.
* **Page table size is entries × entry size,** not entries × page size.
* **KB here means 2^10 bytes.** Turn every size into a power of 2 before anything else.
* **An address past the last page is invalid.** It causes a trap, not a translation.

## How it's asked

* **Part B, every year:** paging explained with a diagram, plus numericals. 2024 Q14: page table size and EAT. 2023 Q14: two-level paging, and translating addresses with a given page table, where one address is past the last page.
* **Part A:** what a TLB is and why it's needed (2024 Q6).
