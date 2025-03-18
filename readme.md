# Memory manager for Free Pascal and Lazarus
Simply Memory Manager is a replacement for the native memory manager for Free Pascal and Lazarus projects on Windows.
***
**Download Simply Memory Manager 2.2 at [opensimply.org/smm](https://opensimply.org/smm/)** 
---
In some cases, it is necessary to repeatedly get and free a large amount of memory. For example, it can be editing graphic files, copying a large number of files and, of course, simulation large and complex systems. In the latter case, multiple reuse of the maximum amount of available memory is required.
Free Pascal's native memory manager uses certain memory allocation and deallocation functions for 32-bit Windows applications that cause fatal errors when reusing large amounts of memory repeatedly, and it runs in this case rather slowly. SMM prevents such errors by using a different approach, and it is much faster on avalanche-like memory allocation requests. 
