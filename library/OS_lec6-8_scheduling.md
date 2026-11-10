OS — lec 6, 7, 8 (CPU scheduling)

lec 6
- scheduler picks next process from the ready queue
- criteria: CPU utilisation, throughput, TAT, WT, response time
- CT = completion time
- TAT = CT - AT
- WT = TAT - BT   <-- sir: ALWAYS use this, esp for preemptive
- RT = (first time on CPU) - AT

FCFS
- non preemptive, by arrival order
- convoy effect: small jobs stuck behind one big job

lec 7
SJF
- shortest BURST first, but only among processes that have ARRIVED
- min avg WT if all arrive together
- prob: burst not known in advance -> predict w/ exponential avg
  τ(n+1) = α t(n) + (1-α) τ(n)    (α usually 1/2)

SRTF = preemptive SJF. check at every arrival

Priority
- in OUR course: smaller number = higher priority !!
- can be preemptive or non preemptive
- starvation -> aging (increase priority as it waits)

lec 8
RR
- time quantum q, then back of the ready queue
- q large -> becomes FCFS. q small -> too many context switches
- !! if a new process arrives at the same time a quantum expires: NEW process goes in the queue FIRST, then the preempted one. sir said write this assumption in the exam
- did 2 examples in class (in notebook, not typed)
