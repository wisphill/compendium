
#design-patterns #oop #solid
```table-of-contents
```

| **Đặc điểm**    | **Factory Method**                                         | **Abstract Factory**                                                     |
| --------------- | ---------------------------------------------------------- | ------------------------------------------------------------------------ |
| **Mục tiêu**    | Quản lý việc tạo ra **một** sản phẩm cụ thể.               | Quản lý việc tạo ra một **Họ (Family)** các sản phẩm liên quan.          |
| **Cơ chế**      | Sử dụng **Kế thừa** (Inheritance). Lớp con ghi đè hàm tạo. | Sử dụng **Composition** (Chứa trong). Đối tượng Factory được truyền vào. |
| **Sản phẩm**    | Chỉ có 1 loại sản phẩm (ví dụ: `ITransport`).              | Nhiều loại sản phẩm đi cùng nhau (ví dụ: `IButton`, `ICheckbox`).        |
| **Độ phức tạp** | Thấp hơn, thường chỉ cần 1 cấp abstract.                   | Cao hơn, cần nhiều interface cho cả Factory và từng loại Sản phẩm.       |

### Factory method
1. Base abstract class has factory method
2. Concrete class implements the factory method to create objects with targeted class
3. The factory method will be used inside the base abstract class
4. *Main function - define the Factory and call the needed functions*

### Abstract factory
Abstraction to manage a family of related products.
1. Family of objects with their interfaces
2. Factory interface to create family of objects
3. Concrete factory to implement the interface to build materials
4. Main function - using factory interface for creating functionalities, passing the concrete factory as material

### SOLID
S: Single responsibility: One class - one responsibility
O: Opened/closed principle: When having new features, we don't need changes current classes, just extend, adding new code 
L: Liskov Substitution principle: Can design the system and if substitute the usages parent class with the child class without changing the correctness of the program 
I: Interface segregation: Smaller interfaces, each interface has their own contract, behaviors
D: Dependencies Inversion: Module, classes should depended on abstraction, not specific class.


### OOP
Encapsulation: Groups of related properties, behaviors, and do not exposing, protecting the props inside, and expose via getters/setters
Inheritance: Concrete class has specifications of parent class
Polymorphism: One object can be existed under multiple forms or different behaviors
Abstraction: Hiding details, exposing essential features.






