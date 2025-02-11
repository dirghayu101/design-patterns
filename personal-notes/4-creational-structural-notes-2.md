### Course: Design Patterns in Typescript
### Factory, Abstract Factory, Facade and Bridge Pattern.

# Lecture on Factory Pattern (60 to 65) (Creational Design Pattern)
- Abstract Class over interface in some scenario will help you in avoiding DRY. 
- You can define constructor, implement common methods in an abstract class, but this is not possible with interface.
- Factory pattern's end result is a single class responsible for creating all the similar category objects. It helps in abstracting away the complexity. One code smell is the presence of multiple similar classes, you can use factory pattern in those scenario.
- General implementation of factory pattern involves an abstract class which will have common code between classes, then a variety of classes implementing/extending the abstract classes and finally a factory class which will be responsible for creating and returning objects to the client. Client will only instantiate this factory class.
- UML diagram? Abstract Class? Other class types in typescript? Is-a relation? Implements vs Extends? 
- Creational Design Patterns deals with object creation, based on this factory design pattern is used when a set of related objects have to be created and a single factory class encapsulates and abstracts away the complexity of creating these different objects.
- Factory Method is a creational design pattern that provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created. [1]
- The Factory Method pattern suggests that you replace direct object construction calls (using the new operator) with calls to a special factory method. Don’t worry: the objects are still created via the new operator, but it’s being called from within the factory method. Objects returned by a factory method are often referred to as products.

# Lecture on Abstract Factory Pattern (66 to 71) (Creational Design Pattern) [2]
- Families of related or dependent objects without specifying their concrete classes.
- Callback functions.
- The first thing the Abstract Factory pattern suggests is to explicitly declare interfaces for each distinct product of the product family (e.g., chair, sofa or coffee table). Then you can make all variants of products follow those interfaces. For example, all chair variants can implement the Chair interface; all coffee table variants can implement the CoffeeTable interface, and so on.
- The next move is to declare the Abstract Factory—an interface with a list of creation methods for all products that are part of the product family (for example, createChair, createSofa and createCoffeeTable). These methods must return abstract product types represented by the interfaces we extracted previously: Chair, Sofa, CoffeeTable and so on.
- Now, how about the product variants? For each variant of a product family, we create a separate factory class based on the AbstractFactory interface. A factory is a class that returns products of a particular kind. For example, the ModernFurnitureFactory can only create ModernChair, ModernSofa and ModernCoffeeTable objects.
- The client code has to work with both factories and products via their respective abstract interfaces. This lets you change the type of a factory that you pass to the client code, as well as the product variant that the client code receives, without breaking the actual client code.

# Lecture Facade Pattern (72 to 78) (Structural Design Pattern)
- Structural Design Pattern deals with object composition and structure of classes and objects. They help ensure that when a change is made in one part of a system, it doesn't require changes in other parts. This makes the system more flexible and easier to maintain.
-  Structural design patterns explain how to assemble objects and classes into larger structures, while keeping these structures flexible and efficient. [3]
- Facade Pattern involves creating a wrapper interface over a complex system to hide its complexities.
- A facade is a class that provides a simple interface to a complex subsystem which contains lots of moving parts. A facade might provide limited functionality in comparison to working with the subsystem directly. However, it includes only those features that clients really care about. [4]
- A facade can become a god object coupled to all classes of an app. In object-oriented programming, a god object (sometimes also called an omniscient or all-knowing object) is an object that references a large number of distinct types, has too many unrelated or uncategorized methods, or some combination of both. The god object is an example of an anti-pattern and a code smell.

# Lecture Bridge Pattern (79 to 84) (Structural Design Pattern) [5]
- Bridge pattern is a structural design pattern that lets you split a large class or a set of closely related classes into two separate hierarchies: abstraction and implementation: these can be developed independently of each other.
- Protected access level in typescript?
- Use the Bridge pattern when you want to divide and organize a monolithic class that has several variants of some functionality (for example, if the class can work with various database servers).
- The bigger a class becomes, the harder it is to figure out how it works, and the longer it takes to make a change. The changes made to one of the variations of functionality may require making changes across the whole class, which often results in making errors or not addressing some critical side effects.
- The Bridge pattern lets you split the monolithic class into several class hierarchies. After this, you can change the classes in each hierarchy independently of the classes in the others. This approach simplifies code maintenance and minimizes the risk of breaking existing code.
- The main goal of bridge pattern is to decouple abstraction and implementation. You would want to do that because you want to work with them independently. Change in implementation would not affect change in abstraction and vice versa, this makes maintaining or extending them easier.


# References:
[1]: https://refactoring.guru/design-patterns/factory-method
[2]: https://refactoring.guru/design-patterns/abstract-factory
[3]: https://refactoring.guru/design-patterns/structural-patterns
[4]: https://refactoring.guru/design-patterns/facade
[5]: https://refactoring.guru/design-patterns/bridge