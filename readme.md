# Simply Memory Manager 1.66
****************************

## Scope of use

The Simply Memory Manager (SMM) is used for Free Pascal and Lazarus on Windows.

Since Free Pascal native memory manager uses Windows functions for memory
allocation and freeing, that may cause fatal errors when large amount of
memory is reusing multiply, the SMM is a good solution for such cases.

+ SMM prevents the "out of memory" error when cyclically allocating and
  freeing large amounts of memory.

+ It is a bit faster on avalanche-like memory allocation requests.

+ SMM has a "reserved memory" feature for the "out of memory" case.

- SMM runs slower than the native FPC memory manager. This is due to the fact
  that when using Lazarus, some memory blocks had been already allocated even
  when SMM was the first module in the "uses" statement. To prevent memory
  errors, the SMM must recognize and process the freeing and reallocating
  requests for memory blocks already allocated by FPC memory manager.
  Memory slowdowns because of SMM are mostly noticeable in the GUI due to the
  constant redrawing of graphical controls that use memory movement.

- Warning! Do not use the SMM when heap tracing. SMM does not support it.


### Why use the SMM in this case?

Despite all of the above, the SMM is ideal for the OpenSIMPLY project, where
its a bit slower performance becomes insignificant compared to the processor
load due to simulation routines.

Modeling large and complex systems requires multiple reuse of the maximum
amount of available memory. The "out of memory" error prevention feature
makes simulation modeling possible for Free Pascal and Lazarus on Windows.


## How to use

Place "SimplyMM" the first after the statement "uses" like

    uses
      SimplyMM,
        ....
 
 
## SimplyMM and memory leaks tracing

Exclude SimplyMM from "uses" statement when heap trace manager "HeapTrc" is active.

    uses
     // SimplyMM,
       .... 
	
 
 
## Links

Homepage: http://opensimply.org

SimplyMM is a part of [OpenSIMPLY project](https://sourceforge.net/projects/opensimply/)
