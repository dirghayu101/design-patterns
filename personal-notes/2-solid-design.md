# SOLID definition:
- S - Single Responsibility Principle (SRP): This principle states that a class should have one, and only one, reason to change. In other words, a class should have only one job or responsibility. This makes the system easier to manage and reduces the potential of code breaking when changes are made.
- O - Open-Closed Principle (OCP): This principle dictates that software entities (classes, modules, functions, etc.) should be open for extension but closed for modification. This means that you should be able to add new features or functionality to a system without altering its existing code. You can extend the behavior of the object, but you should not modify its source code.
- L - Liskov Substitution Principle (LSP): This principle suggests that if a program is using a Base class, it should be able to use any of its Subclasses without the program knowing it. Essentially, subclasses must be substitutable for their base classes without affecting the correctness of the program.
- I - Interface Segregation Principle (ISP): This principle states that clients should not be forced to depend on interfaces that they do not use. In other words, a class should not have to implement methods it does not use. This principle leads to a system where classes have very specific interfaces and are not overloaded with methods that they don't need.
- D - Dependency Inversion Principle (DIP): This principle stresses the need to depend on abstractions, not on concretions. High-level modules should not depend on low-level modules. Both should depend on abstractions. This makes the system more modular, promoting scalability and reducing coupling. 


# Single Responsibility Pointers:
- If a class has more than one responsibility, it has more than one reason to change, which can make it more complex and difficult to maintain.
- The goal is to minimize the impact of change by isolating it. If we have to change something, we should only need to update one class.
- Code that follows SRP tends to be more readable and understandable. Each class has a single focus, and its purpose is generally clear to developers. This saves a lot of time in code comprehension, which is a big part of software development.
- Example:  Let's say you have a User class in a web application, and this class handles both user data management (like user details and preferences) and user authentication. According to SRP, these should be separate classes because they represent different areas of responsibility. A potential change in the way user data is managed should not affect the way user authentication is handled, and vice versa.

# Open Closed Principle:
- This principle dictates that software entities (classes, modules, functions, etc.) should be open for extension but closed for modification. This means that you should be able to add new features or functionality to a system without altering its existing code. You can extend the behavior of the object, but you should not modify its source code.
- Open for extension: This means that the behavior of the software entity can be extended, that is, we should be able to add new features or behavior to it.
- Closed for modification: This means that once the software entity is developed and it has been reviewed and tested, the code should not be touched (to correct the software behavior).
- The example shows a neat trick to implement open closed principle to make changes to a code base with if-else and switch. Instead of adding on code to if else and nesting, we use classes. Highly recommended example: https://cloudaffle.com/series/solid-design-principles/open-closed-principle/
- Existing code isn't modified, so new features don't introduce bugs to existing functionality.
```ts       
// With if-else: Violates Open-closed principle:
class Discount {
  giveDiscount(customer: Customer): number {
    if (customer.type === "Regular") {
      return 10;
    } else if (customer.type === "Premium") {
      return 20;
    } else if (customer.type === "Gold") {
      return 30;
    }
    return 0;
  }
}
```
```ts
// Using interface and classes to achieve the same result. Follows open closed principle and is cleaner comparatively:
interface Customer {
  giveDiscount(): number;
}

class RegularCustomer implements Customer {
  giveDiscount(): number {
    return 10;
  }
}

class PremiumCustomer implements Customer {
  giveDiscount(): number {
    return 20;
  }
}

class Discount {
  giveDiscount(customer: Customer): number {
    return customer.giveDiscount();
  }
}
```

# Liskov's Substitution Principle? [1] [2] [3]
- If S is a subtype of T, then objects of type T in a program may be replaced with objects of type S without altering any of the desirable properties of that program.

# Interface Segregation Principle: 
- In the field of software engineering, the interface segregation principle (ISP) states that no code should be forced to depend on methods it does not use.[1] ISP splits interfaces that are very large into smaller and more specific ones so that clients will only have to know about the methods that are of interest to them. Such shrunken interfaces are also called role interfaces.[2] ISP is intended to keep a system decoupled and thus easier to refactor, change, and redeploy. 
- This principle is all about reducing the side effects and frequency of required changes by splitting large, complex interfaces into smaller, more specific ones. If an interface is broken down into specific sets of methods, it will allow the client to only know about the methods that are of interest to them.

# Dependency Inversion Principle: [4]
- High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.
- High-level modules should not depend on low-level modules. Both should depend on abstractions: This is suggesting that the high-level modules ( modules that implement business logic or use cases) should not directly depend on or interact with the low-level modules (modules that perform basic, low-level functions like writing to a database or handling HTTP requests). Both should interact through abstractions (like interfaces or abstract classes).
- Abstractions should not depend on details. Details should depend on abstractions: This means the abstraction does not know about the underlying implementation. It's the responsibility of the underlying detail (i.e., the classes implementing the interface) to adhere to the contract defined by the abstraction.



# References:
[1]: https://www.linkedin.com/pulse/liskov-substitution-principle-lsp-frontend-prithveesh-goel/
[2]: https://stackoverflow.com/questions/56860/what-is-an-example-of-the-liskov-substitution-principle
[3]: https://cloudaffle.com/series/solid-design-principles/liskov-substitution-principle/
[4]: https://cloudaffle.com/series/solid-design-principles/dependency-inversion-principle/