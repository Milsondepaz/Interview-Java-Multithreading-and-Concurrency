# Java Multithreading and Concurrency Interview Questions

## 1- What is multithreading?
Multithreading is a process of executing multiple threads simultaneously. Multithreading is used to obtain the multitasking. It consumes less memory and gives the fast and efficient performance. Its main advantages are:

- Threads share the same address space.
- The thread is lightweight.
- The cost of communication between the processes is low.

## 2- What is the thread?
A thread is a lightweight subprocess. It is a separate path of execution because each thread runs in a different stack frame. A process may contain multiple threads. Threads share the process resources, but still, they execute independently.

## 3- Differentiate between process and thread?
There are the following differences between the process and thread.

- A Program in the execution is called the process whereas; A thread is a subset of the process
- Processes are independent whereas threads are the subset of process.
- Process have different address space in memory, while threads contain a shared address space.
- Context switching is faster between the threads as compared to processes.
- Inter-process communication is slower and expensive than inter-thread communication.
- Any change in Parent process doesn't affect the child process whereas changes in parent thread can affect the child thread.

![image](https://user-images.githubusercontent.com/16039211/143288611-cf66e175-2fcf-4a80-b809-5a622b784c6f.png)

## 4- What do you understand by inter-thread communication?
- The process of communication between synchronized threads is termed as inter-thread communication.
- Inter-thread communication is used to avoid thread polling in Java.
- The thread is paused running in its critical section, and another thread is allowed to enter (or lock) in the same critical section to be executed.
- It can be obtained by wait(), notify(), and notifyAll() methods.

## 5- What is the purpose of wait() method in Java?
The wait() method is provided by the Object class in Java. This method is used for inter-thread communication in Java. The java.lang.Object.wait() is used to pause the current thread, and wait until another thread does not call the ```notify()``` or ```notifyAll()``` method. Its syntax is given below.
```
public final void wait()
```

## 6- Why must wait() method be called from the synchronized block?
We must call the wait method otherwise it will throw ```java.lang.IllegalMonitorStateException``` exception. Moreover, we need ```wait()``` method for inter-thread communication with ```notify()``` and ```notifyAll()```. Therefore It must be present in the synchronized block for the proper and correct communication.

## 7- What are the advantages of multithreading?
Multithreading programming has the following advantages:

- Multithreading allows an application/program to be always reactive for input, even already running with some background tasks
- Multithreading allows the faster execution of tasks, as threads execute independently.
- Multithreading provides better utilization of cache memory as threads share the common memory resources.
- Multithreading reduces the number of the required server as one server can execute multiple threads at a time.

## 8- What are the states in the lifecycle of a Thread?
A thread can have one of the following states during its lifetime:

1- **New:-** In this state, a Thread class object is created using a new operator, but the thread is not alive. Thread doesn't start until we call the start() method.
2- **Runnable:** In this state, the thread is ready to run after calling the start() method. However, the thread is not yet selected by the thread scheduler.
3- **Running:** In this state, the thread scheduler picks the thread from the ready state, and the thread is running.
4- **Waiting/Blocked:** In this state, a thread is not running but still alive, or it is waiting for the other thread to finish.
5- **Dead/Terminated:** A thread is in terminated or dead state when the run() method exits.

![image](https://user-images.githubusercontent.com/16039211/143289684-3bdebad6-10a7-472f-b00a-005a27a8c36c.png)

## 6- What is the difference between preemptive scheduling and time slicing?
Under preemptive scheduling, the highest priority task executes until it enters the waiting or dead states or a higher priority task comes into existence. Under time slicing, a task executes for a predefined slice of time and then reenters the pool of ready tasks. The scheduler then determines which task should execute next, based on priority and other factors.

## 10- What is context switching?
In Context switching the state of the process (or thread) is stored so that it can be restored and execution can be resumed from the same point later. Context switching enables the multiple processes to share the same CPU.

## 11- Differentiate between the Thread class and Runnable interface for creating a Thread?
The Thread can be created by using two ways.

- By extending the Thread class
- By implementing the Runnable interface
However, the primary differences between both the ways are given below:

- By extending the Thread class, we cannot extend any other class, as Java does not allow multiple inheritances while implementing the Runnable interface; we can also extend other base class(if required).
- By extending the Thread class, each of thread creates the unique object and associates with it while implementing the Runnable interface; multiple threads share the same object
- Thread class provides various inbuilt methods such as getPriority(), isAlive and many more while the Runnable interface provides a single method, i.e., run().

## 12- What does join() method?
The join() method waits for a thread to die. In other words, it causes the currently running threads to stop executing until the thread it joins with completes its task. Join method is overloaded in Thread class in the following ways.

```public void join()throws InterruptedException```

```public void join(long milliseconds)throws InterruptedException```

## 13- Describe the purpose and working of sleep() method.
The sleep() method in java is used to block a thread for a particular time, which means it pause the execution of a thread for a specific time. There are two methods of doing so.

**Syntax:**

```public static void sleep(long milliseconds)throws InterruptedException```

```public static void sleep(long milliseconds, int nanos)throws InterruptedException```

**Working of sleep() method**

When we call the sleep() method, it pauses the execution of the current thread for the given time and gives priority to another thread(if available). Moreover, when the waiting time completed then again previous thread changes its state from waiting to runnable and comes in running state, and the whole process works so on till the execution doesn't complete.

## 14- What is the difference between wait() and sleep() method?
| wait()      | sleep() |
| ----------- | ----------- |
| 1) The wait() method is defined in Object class. | The sleep() method is defined in Thread class. |
| 2) The wait() method releases the lock. | The sleep() method doesn't release the lock. |
