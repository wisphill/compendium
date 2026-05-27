#design-patterns

Operational design pattern
- Chain of responsibilities
- Iterator: to travel the complex object (LinkedList), and exposing the iterator methods only. requires to implement the iterator interface.
- Observer: like the subscriber, publisher (Redis)
- Template Method: Breakdown the algorithm in the superclass and allow overriding (some specific steps) in the subclass, without changing its structure.
- Mediator: 

#### 5 creational design patterns
- Singleton: only one instance in the whole process
- Factory method: 
  - In the simple way, it just provides **an abstract method** to create object in the superclass, the creation method should be implemented in the subclass with an shared interface between all object classes.
  - Core logic can be created in the super class and consume some logics that are provided by the object classes, are relied on the type that is defined in the superclass
  - Use case: when we only know the interface of all objects, do not know the exact type.
- Abstract factory: 
  - Using an factory interface to provide all shared interface methods and object creation methods.
  - All object will be created in the sub factory classes (object family class)
  - The main flow will create factory object and interact with the factory interface. 
  - Use case: There is no mess up between wrong variant types/families of product / object. Use this design pattern when we have to handle multiple families of products / objects.
- Builder: Pattern to construct complex object step by step > provider different types of object with the same construction code.
- Prototype: allow for cloning a object without coupling, redefining methods, private methods in the subclass. Class that implements the copy interface can be called as a property.
