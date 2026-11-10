# Deadlocks (Unit 3)

Ananya's notes, shared before the midsem.

## 4 conditions (ALL needed at once)

1. Mutual exclusion
2. Hold and wait
3. No preemption
4. Circular wait

## Resource allocation graph (RAG)

- request edge P -> R, assignment edge R -> P
- single instance per resource: cycle = deadlock
- multiple instances: cycle = deadlock POSSIBLE, not sure

## Methods

- prevention / avoidance / detection + recovery / ignore it (ostrich algorithm)

Prevention = break one condition

- hold and wait: request everything at the start (bad utilisation)
- no preemption: take resources away from a waiting process
- circular wait: number all resources, request only in increasing order <- most practical

## Banker's algorithm (avoidance)

Need = Max - Allocation

Safety algorithm:

1. Work = Available, Finish[i] = false for all
2. find i with Finish[i] = false and Need_i <= Work
3. Work = Work + Allocation_i, Finish[i] = true, go to 2
4. all Finish true -> SAFE

Resource request algorithm (Pi asks for Request_i):

1. Request_i <= Need_i? else error
2. Request_i <= Available? else Pi waits
3. pretend to allocate: Available -= Req, Allocation_i += Req, Need_i -= Req
4. run safety. safe -> grant. unsafe -> roll back, Pi waits

## Detection

- like the safety algorithm, but with current Request instead of Need
- single instance: wait-for graph, look for a cycle

Recovery: kill processes (all, or one at a time), or preempt resources (rollback, watch for starvation)
