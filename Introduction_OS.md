# What is OS?
The software system that manages hardware resources for both users and their applications.
## Roles of OS:
- Act as a refree: It helps in managing the shared resources between the different applications/users. Example: CPU act as a shared 
  resource. We have only one CPU who is going to use it. In this case we need to decide which process will access the CPU at 
  any moment and any process should not be in the starvation condition (means every process should get the chance to access the CPU). Its the job of the OS to make everyone process happy.
- Provide abstraction (Illusionist): It helps in hiding the complex details of the hardware from the users. As we all know the hardware is really complex and when a computer operates, processes needs to make use of different parts of hardware like keyboard, IO devices etc. So OS makes a virtual image of this complex hardware which is being used by the processes. Its always easier to use virtual resources than the actual resource. As we all know our device doesnot provide lot of space in RAM. While designing any application we doesn't want to deal with these limitations, we assume if the data can not be stored
on RAM, it can be stored on the disk. If the developer has to worry about lot of hardware details then it becomes very difficult to write any application. Hence it is necessary to have some kind of abstraction so that developers have to use them instead of keeping track of every bit of hardware resource. Virtualization is done by OS which means cnverting physical resources to virtual resource.
- Act as a glue: Provide common services to facilitate sharing between different applications. In a computer there are many applications running at the same time. Its the job of OS to facilitate the sharing of resources between them.

## Computer overview to illustrate where data, programs, OS etc resides
In a computer the user data, OS things, application data, programs etc lies in the same memory. Its quite interesting to know that still the OS residing in the same memory are able to control the interference between various applications and processes.
This proves that OS behaves as a refree.

## Processors
Processors(Intel, X86) supports many instructions. Some of the instruction may be very complex. CPU belongs to the category of the processors. ARM is also a processor and belongs to RISK(Reduced Instruction Set Computer) category but they have simpler and smaller set of instructions. They are faster as compared to CISK (Complex Instruction Set Computing). CPU supports a set of instructions and know how to execute them. They use registers in the form of memory to execute these instructions.

## Registers
There are two kinds of registers:
- General purpose registers: It is mainly use to store temporary results, key variables etc. It depends on the developer where he/she wants to store its data.
- Special purpose registers: 
  - Program counter: Contains memory address of the next instruction to be fetched.
  - Stack pointer: Points to the top of the stack in the memory.
  - Control registers: Used to control advanced features of CPU like memory, virtual memory etc.
  - Program Status Word: Contains the condition code bits which are used to specify things like whether the CPU is in user    mode or privileged mode, what is the priority of CPU etc. 

## How processor/CPU works?
CPU is always executing instructions. But there are several phase of it. First the CPU fetches any instruction then it decodes it to get the actual meaning of what the instruction is suppose to do and then executes it.
There are two modes of CPU:
- User mode: Applications run in this mode. In user code, the application has no ability to drectly access the hardware or reference memory. Codes running in user mode must delegate to system APIs to access the memory or hardware.
- Kernel mode: System code, kernel of operating system run in this mode. When there is any executing set of codes, it has limited access to the kernel mode. In kernel mode we can access any memory address. The most trusted functions of the OS are executed in this part. Kernel mode act as a refree for user mode.

Trap: It causes synchronous switch between user mode and kernel mode. 

## Memory and I/O:
Memory is an important part of computer. Registers, RAM, Cache are the type of memory. Registers are the fastest but small and RAM is slow. Cache comes in between the registers and RAM. It is not as big as RAM. If there are no space in cache then they have to go to RAM to store data. This is the case of cache miss.
Registers > Cache > RAM > Magnetic Tape > Magnetic Disk
1 nsec : 2 nsec : 10 nsec : 10 msec : 100 sec







