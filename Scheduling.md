# Scheduling
- OS is resposible for scheudling
- There is a need for scheduling policy which decides the rules for 
  scheduling a process for xecuting next.
- Scheduling function is defined to execute this scheduling policy.
- It selects the process based on the policy and hence updates the process
  table for the current and selected process. 
- Then also "context switch is performed" which switch between the current p
  process and the selected process.
- Scheduling policy depends on user, requirement etc. OS can have multiple scheduling policy. 
- Scheduling policy must follow fairness so any process doesnot starve.
- Context switching is expensive. So while designing the scheduler we should keep in mind that context switch
  doesn't happen that often.
- In Xinu, integer value is used to assign the priority to any process. Priorities can change 
  any time. Initiled when process is created. 
- Scheduler always run the highest priority process.

## Round-robin:
At any time, the processor must be executing a highest priority eligible process. But there can be 
situation where there are processes of equal priority. In that case the scheduling algorithm just switched 
between the processes depending on the time alloted to them.

- Changes can only happen when there is an interrupt or there is a system call. It should always 
  happen in kernel mode. 
  
## Eligible process:
- Ready state or Current state.

## Efficient searching process in the process table during scheduling
- Ready list consist of ready processes.
- They are arranged in the order of their priority. Highest priority process is stored at the top.
- Selecting the highest priority process can be perfomed in O(1) time.

## Why it is sufficent to compare just the current process with the priority of the first processon 
ready list?
Because ready list is kept in an order of their priority

## What happens in case of tie between the priority of current process and highest priority
process in the ready list?
Round-robin

## Deferred rescheduling
There is a timer which calls the interrupt and the interrupt handler calles the scheduler.
There should be always a process running in the system. If the current process dies or kill itself 
then there is need of immediate execution of another process to take the place. 
- It suspends rescheduling.

## Currpid
- Global variable gives ID of process that is executing.
- proctab[currpid].prstate - next state of the current process
- proctab of currpis is selected and .prstate is used to access the prstate field of 
  current process.

Q) How do you reference curpid if running on multiple-core CPUs?
currpid is the global variable. Several current running processes exist if we have
several CPUs. We should have a global array containing the id of the currently running process
in each CPU.

- Scheduler switches context if the first process in the readylist is equal to or greater than 
  current process.
