# Abstraction of process
- Unit of computation
- Processor is only known to OS
- Not known to hardware
- All the computation is done inside a process
- No OS actually executes the computation. All computation is done inside a process.
- There should be atleast one process running all the time. OS cannot stop a running process until it context switch to 
  other processes.
- A process can have multiple threads running inside it so it might be reffered as heavy-weight process. 
- There are separate componenets for each process like data and bss segments.
- Each process has its own address space. 
- In light process there could be single thread. It can share its data and bss segment with other threads but it should keep its 
  stack segment private.
- So there should be separate stack for each threads. But multiple threads could share the same data and bss segments.
- Threads could not share the stacks.
- Onle the bss and data sections could be shared between the multiple threads inside a process.

## Maintaining processes
- Its the job of the OS to keep track of the processes because processes are unknown to the hardware.
- For maintaining the processes, OS maintains a process table.
- As it is unknown to hardware, process table is not the part of hardware but needs to be stored in OS address space.

## Information kept in process table:
- Process identifier (Integer)
- Owner of the process (If OS involves multiple users)
- Scheduling priority
- Location of data and code
- Process status like waiting, curr, nulll, ready etc.

Q) Where do we store current program counter and current register values of currently running program?
Stack

In XINU there is only a single owner, one global context, one global address.

### prstate: Current status of process (running, waiting, current etc)
### prprio: Priotity of the process (integer)
### prstkptr: Saved value of the process stack pointer when the process is not executing
### prstkbase: Address of the base of the process's stack
### prstlen : Maximum size that process stack can grow
### prname: Indentifier for the process (humand use this to refer to the process)
