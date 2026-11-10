paging + TLB (lec 14-16)

paging
- logical mem -> pages, physical mem -> frames. SAME size
- no external fragmentation. internal frag only in the last page

logical addr = | p | d |
page size 2^n -> d = n bits, rest is p

- page table per process. PTBR points to it (PTLR = its length)
- each entry: frame no. + valid bit, protection bits, dirty bit

problem: every access = 2 memory accesses (PT + data)
-> TLB (associative memory, small + fast)

EAT = h(t + m) + (1-h)(t + 2m)
   <- sir's formula. TLB time is counted on a miss also
   (some books drop t on a miss. sir said use this one)

ex done in class: m = 100ns, t = 20ns, h = 80%
EAT = .8(120) + .2(220) = 96 + 44 = 140 ns

PT size: 32 bit addr, 4KB pages -> 2^20 entries x 4B = 4MB per process!! too big
-> multilevel paging. 2 level: | p1 | p2 | d |  (outer page table)
-> inverted PT: one entry per FRAME, not per page
