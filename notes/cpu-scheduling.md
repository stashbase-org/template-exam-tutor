# CPU scheduling

How the OS picks which ready process runs next, and how to work out waiting and turnaround times by hand. There's a scheduling numerical in Part B every year.

**Sources:** [OSTEP ch. 7: CPU Scheduling](https://pages.cs.wisc.edu/~remzi/OSTEP/cpu-sched.pdf) · [Class notes, lectures 6–8](../library/OS_lec6-8_scheduling.md) · [2024 paper](../library/PYQ_2024_endsem.md) Q1–Q3, Q11 · [2023 paper](../library/PYQ_2023_partB.md) Q11
**My mistakes:** [Mistakes › CPU scheduling](../mistakes.md#cpu-scheduling)

## Key ideas

* **The times you're asked for:** completion time (CT) is when a process finishes. Turnaround time TAT = CT − arrival time. Waiting time WT = TAT − burst time. Response time = first time on the CPU − arrival time.
* **FCFS:** runs processes in arrival order, each to the end. Simple, but one long process ahead of short ones makes them all wait. That's the convoy effect.
* **SJF (non-preemptive):** of the processes that have arrived, runs the one with the shortest burst, to the end. It gives the lowest average waiting time when all processes arrive together.
* **SRTF (preemptive SJF):** at every arrival, if the new process's burst is shorter than what's left of the running one, it takes over. The lowest average waiting time of all. But the OS doesn't know burst lengths in advance, so it predicts the next one from past bursts: τ(n+1) = α·t(n) + (1 − α)·τ(n), usually with α = 1/2.
* **Priority:** the highest priority runs first, preemptive or not. In our course, a smaller number means a higher priority. Low-priority processes can starve; aging raises a process's priority the longer it waits.
* **Round robin (RR):** each process runs for at most one time quantum, then goes to the back of the ready queue. Good response time. Too large a quantum and it turns into FCFS; too small and the CPU spends its time switching.

## How to work it out

1. List each process with its arrival and burst time.
2. Draw the Gantt chart. At every event (an arrival, a finish, a quantum running out), pick who runs next by the algorithm's rule. If nothing has arrived, the CPU sits idle; leave a gap.
3. Read each completion time off the chart.
4. TAT = CT − arrival, WT = TAT − burst. Then average each.

Example, round robin with quantum 2: P1 arrives at 0 with burst 5, P2 at 1 with burst 3, P3 at 2 with burst 1.

* 0–2: P1 runs. P2 arrives at 1. At 2, P3 arrives just as P1's quantum ends: P3 joins the queue first, then P1. Queue: P2, P3, P1.
* 2–4: P2 runs, 1 left. Queue: P3, P1, P2.
* 4–5: P3 runs and finishes.
* 5–7: P1 runs, 1 left. 7–8: P2 finishes. 8–9: P1 finishes.

```
| P1 | P2 | P3 | P1 | P2 | P1 |
0    2    4    5    7    8    9
```

| Process | Arrival | Burst | CT | TAT | WT |
| --- | --- | --- | --- | --- | --- |
| P1 | 0 | 5 | 9 | 9 | 4 |
| P2 | 1 | 3 | 8 | 7 | 4 |
| P3 | 2 | 1 | 5 | 3 | 2 |

Average TAT = 19/3 ≈ 6.33. Average WT = 10/3 ≈ 3.33.

## Common traps

* **Waiting time in preemptive algorithms:** a process can wait more than once, so WT isn't "start time − arrival". Always use WT = TAT − burst.
* **Round robin ties:** when a new process arrives at the moment a quantum runs out, our class notes put the new one in the queue first, then the preempted one. Books differ, so write the assumption in your answer.
* **SJF only picks among processes that have arrived.** The shortest burst in the table may not be there yet.
* **Priority numbers:** smaller is higher in our course. Some books use the opposite; check the question.

## How it's asked

* **Part B, every year:** a table of four or five processes; Gantt charts and average WT and TAT for three algorithms, 12 marks, plus 4 marks of theory. 2024 Q11: FCFS, SRTF, and RR, then predicting bursts. 2023 Q11: SJF, preemptive priority, and RR, then preemptive vs. non-preemptive.
* **Part A:** TAT and WT, the convoy effect, starvation and aging (2024 Q1–Q3).
