# Simply Memory Manager 1.65
****************************

Simply Memory Manager (SMM) replaces native Free Pascal memory manager on Windows.

* Works stable with Free Pascal and Lazarus on 32-bit and 64-bit Windows.

* Suitable for simulation. 

* Prevents the "out of memory" error when cyclically allocating and
  freeing a large amount of memory.

* A bit faster on avalanche-like memory allocation requests.

* SMM has a "reserved memory" feature for the "out of memory" case.


(!) Mind that the SMM runs slower than the native FPC memory manager.

This is due to the fact that when using Lazarus, some memory blocks had been already allocated even when SMM was the first module in the "use" statement.
To prevent memory errors, the SMM must recognize and process the freeing and relocating requests for memory blocks already allocated by FPC memory manager.

The memory slowdown due to SMM is especially noticeable in the GUI, due to the constant redrawing of graphical controls that use memory movement.  


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

Homepage: https://opensimply.org

SimplyMM is a part of [OpenSIMPLY project](https://sourceforge.net/projects/opensimply/)
