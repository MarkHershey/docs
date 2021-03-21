# Inter-Process Communication

Each process in the system has its own isolated memory space, if a program has multiple processes running concurrently and there are some data need to be shared/accessed by all the processes, some form of inter-process communication (IPC) has to be done. There are two main problems to be considered for IPC:

- How to pass data between processes
- How to prevent race condition, conflicts between processes while reading/writing shared data. In other words, how to synchronize different processes to work together smoothly.

To addressing the first problem, there are various methods to achieve IPC:

- [Network Socket](https://en.wikipedia.org/wiki/Network_socket)
- [Unix Domain Socket ](https://en.wikipedia.org/wiki/Unix_domain_socket)
    - bidirectional
- [Message Queue](https://en.wikipedia.org/wiki/Message_queue)
- [Named Pipe](https://en.wikipedia.org/wiki/Named_pipe) 
    - unidirectional
- [Shared Memory](https://en.wikipedia.org/wiki/Shared_memory)
- [Message Passing](https://en.wikipedia.org/wiki/Message_passing)
