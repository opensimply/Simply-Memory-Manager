# Simply Memory Manager 2.2
***************************

Memory manager for Free Pascal and Lazarus. 


## Scope of use

The Simply Memory Manager (SMM) is a replacement for the native memory
manager for Free Pascal and Lazarus projects on Windows.

Simulation modeling of large and complex systems (and not only simulation)
requires multiple reuse of the maximum amount of available memory.

Free Pascal's memory manager uses certain Windows functions for memory
allocation and freeing, which cause fatal errors when large amount of memory 
is reusing multiple times. In addition, it runs in this case rather slow.

The SMM prevents such errors by using a different approach, and it is much
faster on avalanche-like memory allocation requests.
Run the "TestMemMgr" project to compare the performance.

The SMM has a "reserved memory" feature for the real "out of memory" case
that may prevent critical error.

In some cases, the SMM may be a bit slower than the native memory manager.
This is due to the fact that when using Lazarus IDE, some memory blocks
were already allocated, even when the SMM was the first unit in the "uses"
statement. Therefore, the SMM must also recognize and process requests to
free and reallocate memory blocks already allocated by the native memory
manager. This additional processing can reduce performance somewhat. The
slowdown might probably be noticeable in some cases in the GUI due to the
constant redrawing of graphical controls that use memory reallocation.


## How to use

Place the SimplySMM unit the first in the "uses" statement.

    uses
      SimplyMM,
        ....
 
## SMM and memory leaks tracing

Do not use the SMM when heap trace manager (HeapTrc) is active. 
In such cases, exclude the SimplySMM unit from the "uses" statement.  

    uses
     // SimplyMM,
       .... 
	
 
 
## Terms of Use 

The Simply Memory manager is free open source software under GNU General
Public License version 3, and is a part of the OpenSIMPLY project.

Home page: https://opensimply.org/smm/

Ask a question or report an issue: https://opensimply.org/feedback
