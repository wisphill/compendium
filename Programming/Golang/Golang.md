#golang
### GC and Tricolor algorithm
- All objects in the HEAP are started as WHITE.
- If the object is reachable, haven't been scanned > GREY
- If the object is reachable, fully scanned all children of their graph > BLACK
- unreachable objects: Object in the HEAP and there are no references to it and it should be WHITE after the **marking** phase
- Write barrier: additional code be added at the compiled time with the condition {{ *If the WHITE object suddenly has a reference (impacted by other goroutines) during marking phase, it will be marked to GREY and wait to be scanned* }}
- BLACK objects are never be scanned anymore in the same GC cycle > so we need the Write barrier to make sure the WHITE objects are never be cleared and all children of them are scanned as well. 
- Sweep phase: Sweep all WHITE objects.
- STW: Cleanup stack of goroutines (local stack variables, pointers), and turn on/off Write barrier. Write Barrier only protects objects in the HEAPs.