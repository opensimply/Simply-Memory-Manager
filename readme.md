# Simply Memory Manager 2.0
***************************

This release is a significantly redesigned version with improved performance and some fixes.



## Scope of use

The Simply Memory Manager (SMM) is used for Free Pascal and Lazarus on Windows.

Simulation modeling of large and complex systems (and not only simulation)
requires multiple reuse of the maximum amount of available memory.

Free Pascal's native memory manager uses certain Windows functions for memory
allocation and freeing that cause fatal errors when large amount of memory is
reusing multiply.

The SMM prevents such errors. 



## Advantages and disadvantages

+ SMM prevents the "out of memory" error when cyclically allocating and
  freeing large amounts of memory.

+ It is a bit faster on avalanche-like memory allocation requests. Run "TestMemMgr" project included in the SMM package to compare the performance.

+ SMM demonstrates enough good performance both for single- and multi-thread tasks.
  
+ SMM has a "reserved memory" feature for the "out of memory" case.

- In some cases, SMM may be a bit slower than the native FPC memory manager. This is due to the fact that when using Lazarus, some memory blocks had been already allocated even when SMM was the first module in the "uses" statement. To prevent memory errors, the SMM must recognize
  and process the freeing and reallocating requests for memory blocks already allocated by FPC memory manager. Thus, the slowdown due to SMM might probably be most noticeable in some 
  cases in the GUI due to the constant redrawing of graphical controls that use memory movement.



## How to use

Place SMM the first after the "uses" statement.

    uses
      SimplyMM,
        ....
 

 
## SMM and memory leaks tracing

Do not use SMM when heap trace manager HeapTrc is active. 
In such cases, exclude SMM from the "uses" statement.

    uses
     // SimplyMM,
       .... 
	
 
 
## Links

Homepage: http://opensimply.org


