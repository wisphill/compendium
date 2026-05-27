**JIT compiler**
	- Builder convert C# to the IL, IL will be converted to the machine code by JIT when running application in the first time.
	- CLR: JIT compiler, GC, Exception manager, thread manager

**ref in out**
ref in: to refer to the existing struct in the inner function or other function. 
out: define the variable and assign the value in the function then return it to the outer scope. it's developed before the Tuple type.  

**boxing / unboxing:** 
Convert any kind of value to object > the value is stored in HEAP mem. 

**`Span<T>` là value hay reference** 
Span là ref struct, nằm trên stack, không được phép nằm trên heap: Span looks at the contiguous memory in the Stack, cannot be used with async await
if we want to store it on HEAP > convert it to the `Memory<T>`
Memory can be used only for the async/await, not for calculation.

**async/await**
- Create a smallest task, unit of work
- Snapshot the function stack to the HEAP > that why the span cannot be used with async/await, any kind of ref struct is not possible

**Enums is on the Stack, value type**

1 Managed Thread = 1 OS Thread & ThreadPool

I/O: File I/O, Network I/O Console I/O, waiting for the inputs
Default: C# using multiple threads without creating too much threads

When I need threads: Can be rendering, a task running for life time while running the application

Event loop: a loop,  a train with 6 stations, for 6 kind of events, code logic will block the event loop
Goroutine: multiple goroutines can be created by 1 OS thread

**`Nullable<int>` is int?** it's a struct type ? is the boolean value in the Struct

**Class is always on HEAP**, and its properties must be on HEAP mem as well

**RAM:**
OS allocates some memories for the program, and the runtime separates the HEAP and stack

**finalizer**
It's used for GC

**`IDisposable` / `using`**
Release unmanaged resources like the FileStream, connection to avoid memory leak

**Access modifiers in C#**
	Public: access from anywhere
	Private: In the class only
	Protected: Can be used in the child class
	Private protected: Child class **AND** in the same project. 
	Protected internal: Same project with the class **OR** in another project but must be in the child class.
	Internal: Access in the same project only

**.dll file**
Dynamic link, it's IL. Use the dll import to use features that implemented by the dll

**sealed class**
Avoid inheritance, avoid overriding.

**virtual / override**: go together to override methods, it's polymorphism of OOP

**new function in the class**
Not polymorphism: even casting the object to the parent function, it's still the new function

**volatile**
Similar with Java, to use the value in the RAM directly to avoid race condition, the value is cached in the L2/L3 cache layer. 

**throw/ throw ex**
Mechanism: 
throw: keep & update the stack trace in the HEAP memory (it's snapshotted from Stack before)
throw ex: new beginning of error trace and loose the stack trace, hide error trace, CLR writes the throws line trace to the object ex > loose the trace `ex.StackTrace = [New Snapshot tại dòng hiện tại]`.
throw new InnerException("error", ex): wrap error and keep the trace.

**Garbage collector in C#**
Gen 0: New objects
Gen 1: Existed objects after running the GC for 1 time
Gen 2: Existed objects after running the GC for 2 times
LOH (Large Object Heap): Gen 2
Stop the world -> compacting memory (moving objects from gen 0 to gen 1)
Background GC (new): Clearing the Gen 2, Mark and Sweep but not compacting.
Last dance: Full blocking GC to compact the gen 2 objects.

**Record**
	- record - record class: value equality not reference equality like class, on the HEAP, immutable. Create a clone with the **with** keyword. **Use case**: DTO
	- C# 10 - record struct: on the Stack, mutable. Difference with struct > auto implement equal function. 

**ConfigureAwait(false)** **& SynchronizationContext**
- When waiting for an async function to be completed inside the UI thread, the context will be snapshotted as `SynchronizationContext`, the UI thread will be freed to execute something else. When the async action is done, the UI thread will continue on the Synchronization Context.
- WinForm UI 1 thread for the UI, can choose any thread to process the workflow without waiting to reload the UI thread.
- ASP.NET Legacy: Each request has their own context. 
- .NET Core do not have SynchronizationContext, can use any threads to continue works. 