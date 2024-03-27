# Concurrency-with-pthreadThe provided C program creates two threads using the pthread library, each executing a separate function concurrently. However, it immediately exits the main function without waiting for the threads to finish their execution. Here's what you would observe:

The program starts and creates two threads: one executing print_i and the other executing print_j.
Both threads start executing their respective functions.
Since there's no synchronization or waiting mechanism in place, the main function calls exit(0) immediately after creating the threads.
As a result, the program terminates abruptly, possibly before both threads get a chance to print their messages.
The actual output on the screen might vary depending on the scheduling of threads by the operating system. You might see one or both of the messages "I am in i" and "I am in j" printed on the screen, or you might not see any output at all before the program terminates.

To ensure that both threads have completed their execution before the program exits, you should use pthread_join to wait for them to finish. Here's an updated version of the program with pthread_join:
