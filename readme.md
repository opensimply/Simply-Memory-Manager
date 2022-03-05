# Simply Memory Manager 2.2
***************************

Memory manager for Free Pascal and Lazarus. 


## Scope of use

The Simply Memory Manager (SMM) is a replacement for the native memory
manager for Free Pascal and Lazarus projects on Windows.

Simulation modeling of large and complex systems (and not only simulation)
requires multiple reuse of the maximum amount of available memory.

Free Pascal's native memory manager uses certain Windows functions for memory
allocation and freeing, which cause fatal errors when large amount of memory is
reusing multiply. In addition, the memory manager runs in this case is rather slow.

The SMM prevents such errors, and it is a much faster on avalanche-like memory
allocation requests. Run the "TestMemMgr" project to compare the performance.

The SMM has a "reserved memory" feature for the "out of memory" case that may
prevent critical error of your project .

In some cases, the SMM may be a bit slower than the native memory manager.
This is due to the fact that when using Lazarus IDE, some memory blocks
had been already allocated even when the SMM was the first module in the
"uses" statement. To prevent such memory errors, the SMM must recognize
and process the freeing and reallocating requests for memory blocks
already allocated by Free Pascal's memory manager.

Thus, the slowdown due to the SMM might probably be most noticeable in some
cases in the GUI due to the constant redrawing of graphical controls that
use memory movement (reallocation).


## How to use

Place SimplySMM unit the first after the "uses" statement.

    uses
      SimplyMM,
        ....
 
## SMM and memory leaks tracing

Do not use SMM when HeapTrc heap trace manager is active. 
In such cases, exclude the SimplySMM unit from the "uses" statement.  

    uses
     // SimplyMM,
       .... 
	
 
 
## Terms of Use 

The Simply Memory manager is free open source software under GNU General
Public License version 3, and is a part of the OpenSIMPLY project.

Home page: https://opensimply.org/smm/

Ask a question or report an issue: https://opensimply.org/feedback
