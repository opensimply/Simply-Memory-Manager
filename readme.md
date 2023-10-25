# Memory manager for Free Pascal and Lazarus
**Download Simply Memory Manager 2.2 at [opensimply.org/smm](https://opensimply.org/smm/)** 
***
Simply Memory Manager (SMM) is a replacement for the native memory manager for Free Pascal and Lazarus projects on Windows.
Free Pascal's native memory manager uses certain Windows functions for memory allocation and freeing that cause fatal errors when large amounts of memory are repeatedly reused.
In addition, it runs in this case rather slowly. SMM prevents such errors by using a different approach, and it is much faster on avalanche-like memory allocation requests.
