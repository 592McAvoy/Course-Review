# Process

## 1. Thread & Process

### 1.1 thread

- thread是一个**运行单元**的抽象

- 包含the *minimal state* that is necessary to stop an active and resume it at some point later

  - The state depends on the processor，on x86, it is the processor registers

  ![](img/10.png)

- Address spaces 和 threads 是相互独立的概念：
  - One can switch from one thread to another thread in the same address space
  - or one can switch from one thread to another thread in another address space

### 1.2 process

- process是一个在执行的程序（资源分配单元）

  - $1$ * address space + $1^+$ * thread

  - 包含 program counter, stack, data section

- process的state在它运行过程中不断改变

  - **new**:  The process is being created

  - **running**:  Instructions are being executed

  - **waiting**:  The process is waiting for some event to occur

  - **ready**:  The process is waiting to be assigned to a processor

  - **terminated**:  The process has finished execution

    ![](img/11.png)

- **Process Control Block (PCB)**与对应process相关联，包含process的信息

  - Process state

  - Program counter

  - CPU registers

  - CPU scheduling information

  - Memory-management information

  - Accounting information

  - I/O status information

    ![](img/12.png)

## 2. Context Switch

### 2.1 switch

从一个process切换到另一个process

- save the state of the old process
- load the saved state for the new process Context of a process represented in the PCB

![](img/13.png)

- 更改%esp（换栈）标志着switch
- 调用swtch时把%eip存到了栈上（ret addr），所以后面一系列pushl中没有eip

### 2.2 Process Scheduling Queues

- **Job queue** – set of all processes in the system
  - **Ready queue** – set of all processes residing in main memory, ready and waiting to execute
  - **Device queues** – set of processes waiting for an I/O device

- **Scheduler**
  - **Long-term scheduler**  (or job scheduler) – selects which processes should be brought into the ready queue
    - controls the *degree of multiprogramming*
  - **Short-term scheduler**  (or CPU scheduler) – selects which process should be executed next and allocates CPU

![](img/14.png)

## 3. Fork

- parent process调用fork来创建一个child process
  - 使用**process identifier** (**pid**)来区分不同process
  - child：fork返回0，parent：fork返回child pid
- Execution
  - Parent and children execute **concurrently**
  - Parent waits until children terminate
    - 如果Parent要exiting，就要先级联的把child给terminate掉
- Address space
  - Child **duplicate** of parent’s
  - Child has a program loaded into it

![](img/15.png)