**`==` khác `equals()` thế nào**
== : compare the reference, address of the pointer
equal: compare the real value, can be overrided

**hashCode()**
Return unique id for the 

**JVM, JRE, JDK khác nhau thế nào**
3. JVM: Java virtual machine, converting .class > byte code
4. JRE: Java runtime env (include jvm) to run the jar file
5. JDK: Development kit, javac. Java to .class


**Java là pass-by-value hay pass-by-reference**
Pass by value for native type
Pass by value (copy of reference) for the object type


**String Constant Pool**.
`String` immutable vì sao, vì nó dùng string pool, nếu value có trong pool rồi thì nó sẽ dùng reference tới value đấy. Vì string immutable nên hash của value cũng không đổi nên có thể được cache.

**Khác nhau giữa `String`, `StringBuilder`, `StringBuffer`**
String: immutable
StringBuilder: mutable, non-thread safe, no locking
StringBuffer: mutable, thread safe

**`final`, `finally`, `finalize()` khác nhau?**
finalize() -> using for GC
finally -> try catch
final -> constant

**`static` dùng khi nào? Nhược điểm?**
Khi muốn value tồn tại suốt vòng đời của chương trình,
Nằm trong heap, không giải phóng bởi GC, shared memory, hard to write unit tests

**ClassLoader là gì? Có mấy loại?**
Bootstrap Classloader, it's parent class loader, written by C++ to import important classes like Object List, ...
Extension Classloader: Load class from external library to extend features of java runtime
Application Classloader: To load our own classes.

**Overloading vs Overriding?**
Overriding: Override method in the same class to have different implementation in the child class
Overloading: Same function but with multiple function signatures, different params

**Checked Exception vs Unchecked Exception**
Checked Exception: managed exception and can be controlled and checked at the compile-time
Unchecked Exception: Fault of programmers, it's like the null pointer exception

**`throw` vs `throws`?**
throw exceptions
throws used at the function signature to define list of exceptions that can be happened

**`try-with-resources` hoạt động thế nào?**
Auto close the resource, replacing for the finally + Close function

**`clone()` có nên dùng không? Vì sao?**
Clone can make the shallow copy, we should use the copy constructor instead, to control deep copy. 
clone() hiệu quả với kiểu dữ liệu nguyên thủy

**Deep copy vs shallow copy?**
Deep copy: create another value in mem
Shallow copy: just copy the reference

**Reflection là gì? Dùng khi nào?**
Watching objects, classes in the program
Allow modifying, defining, running and ignoring OOP principle. Reflection could be slow, because the checking is on the runtime, some logic could be known at the compile time.

**Marker interface**, to tag the object with a empty class. Can use the marker interface for checking, compile-time type checking


**`Optional` sinh ra để giải quyết vấn đề gì?**
Avoid multiple null checks, if we have a sequence of function calls.
A.B().C()

**`transient` dùng khi nào?**
Does not store the value of the variable when converting the object to bytes via Serialization (converting to bytes) to writes to file / transfer via network.

**`volatile` giải quyết vấn đề gì?**
volatile will ignore the CPU L1/L2 cache when using multiple thread, to make sure the value will be updated from RAM directly. Threads will see the newest value of a variable

**Immutable object là gì? Cách tạo? 5**
1. Class is final, no overriding
2. private fileds
3. final fields
4. No setter
5. Deep copy for mutable objects, for the getter function as well


**Wrapper class là gì? Autoboxing/unboxing?**
Wrap primitive types to object type, allowing null to wrap them to be used with ArrayList and HashMap (where we only can use the object type). int to Integer

**Khi nào dùng abstract class, khi nào dùng interface?**
abstract class: Generation of classes, new classes has same behaviors of the parents. Present for the relationship "IS-A"
interface: (Loose Coupling),  Present for the relationship "CAN-DO" 
each set of logic can be a contract. Separate between definition and implementation. 

**`synchronized` hoạt động thế nào?**
- For method
- For block of code
- For an object
- It has a specificity: Reentrant, if a thread holds a lock of a object, it can access to all synchronized methods of that object.
Thread 1: Locking -> Unlocking, Thread 2: Waiting in the Entry Set.

**Intrinsic lock là gì?**
It's monitor lock, the default locking mechanism inside each object in Java. In Java, all objects are locks.

**Atomic classes dùng để làm gì?**
Handling the thread-safety problems for variables without using the lock (lock-free)
Mechanism: CAS, Optimistic lock, Set value, compare result with expectation and retry.
To avoid ABA issue with the reference type: Use the stamp/version for the object like AtomicStampedReference







