General Linux system Organization:
- User Processes - GUI, servers, Shell
- Linux Kernel - system calls, process Management, Memory management, Device drivers
- Hardware: CPU, Main Memory (RAM), Disks,...

_The kernel_: a software residing in memory that acts as the primary interface between the hardware and any running program.

_Processes_ (user processes): These are the running programs that the kernel manages. These make up the _**user space**_

The kernel runs in kernel mode while the user processes run in user mode.The Kernel mode has unrestricted access to the processor and main memory.

The *User space* refers to the parts of main memory that the user processes can access.

A _state_ is a particular arrangement of bits. e.g you can have 4 bits represented in 3 different states: 0110, 0001, 1011. 

The term _Image_ (e.g ISO image) refer to a particular physical arrangement of bits.

The kernel is in charge of managing tasks in 4 general system areas:
- Process: It determines which process are allowed to use the CPU
- Memory: The kernel needs to keep track of all memory. Ensuring proper distribution between processes.
- Device drivers: The kernel acts as an interface between hardware and processes. The kernel operates the hardware.
- System calls and support: Processes use **system calls*** to communicate with the kernel.

Context Switching: The act of one process giving up control of the CPU to another process. A time-slice is the piece of time given to each process (usually enough for significant computation).

The Kernel is responsible for context switching.
The Kernel runs between process time slices during a context switch.

The concept of a Memory Management unit (MMU) is still a bit unclear. (chapter 8)

A device is accessible only in kernel mode, avoiding improper access by user processes.
Different devices even if they perform the same task can have different programming interface, hence the need for the device drivers as part of the kernel, presenting a uniform interface to user processes simplifying the software developer's job.

System calls: Several kinds of kernel features are available to user processes. e.g system calls perform tasks that a user process alone cannot do well or at all. e.g, the acts of opening, reading, and writing files all involve **_syscalls_** (interaction between a process and the kernel).

Two system calls, fork() and exec() give a good understanding of how processes start.
fork(): when a process calls this, the kernel creates a nearly identical copy of the process
exec(): when a process calls exec(program), the kernel loads and starts program, replacing the current process.

What exactly are Pseudodevices? (something about the Kernel supporting user processes with features other than traditional syscalls)


Users exists primarily to support permissions and boundaries. Every user-space process has a user owner, and processes are said to run as the _owner_. A user may terminate or modify the behavior of its own processes(within certain limits), but it cannot interfere with other users' processes. Note the the _root_ is also a user (the most important user), and a Linux system normally has a number of users in addition to the ones that correspond to the real humans who use the system.

The root is the "superuser"
_As powerful as the root user is, it still runs in the operating system's user mode, not kernel mode._
Groups are sets of users. They can callow a user to share file access to other members of a group.

----
This is the end of Chapter 1