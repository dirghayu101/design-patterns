### Course: Design Patterns in Typescript
### Behavioral Design Pattern: Observer Pattern, Iterator Pattern, Strategy Pattern 

# Lecture on Observer Pattern (Behavioral Design) (103 to 109)
- Try implementing observer?? [3]
- Behavioral design pattern deals with communication between objects.
- These patterns helps in distributing responsibilities to ensure that the system is efficient, maintainable, and scalable.
- Observer behavior has following components: Subject and Observer. 
- Subject is the object being observed.
- When the state of subject change, observer gets notified. Observer in a sense have subscribed to the subject.
- The structure of this implementation:
```js
    interface Observer {
        // This method will be invoked for all the observer when the setState method is invoked in the subject.
        update(subject: Subject): void;
    }

    interface Subject {
        addObserver(observer: Observer): void;
        removeObserver(observer: Observer): void;
        notifyObservers(): void;
        getState(): number;
        setState(state: number): void;
    }
```
- The object that has some interesting state is often called subject, but since it’s also going to notify other objects about the changes to its state, we’ll call it publisher. All other objects that want to track changes to the publisher’s state are called subscribers. [1]
-  Observer pattern is used when you are polling. [2]
- Ineffective communication between objects is one of the biggest use case of observer pattern. If you see objects communicating directly with many other objects to share changes to their internal state, this is strong sign that an observer pattern is required. 
- If you don't use observer pattern and instead allow objects to share changes between their internal state, it will result in spaghetti code which is difficult to maintain and understand.
- Use the Observer pattern when changes to the state of one object may require changing other objects, and the actual set of objects is unknown beforehand or changes dynamically. You can often experience this problem when working with classes of the graphical user interface. For example, you created custom button classes, and you want to let the clients hook some custom code to your buttons so that it fires whenever a user presses a button.
- The Observer pattern lets any object that implements the subscriber interface subscribe for event notifications in publisher objects. You can add the subscription mechanism to your buttons, letting the clients hook up their custom code via custom subscriber classes.
- You will notify the observer in subject's set state method.
- One of the major advantage of this pattern is that the subject doesn't need to know anything about its observers. 
- Memory Leaks is one of the major drawbacks of observer pattern and should be taken into account. Remove observer from the subject when they are no longer needed. Over notification is also considered one of the concern.
- There is no logic usually of the chronology of observers getting triggered.


# Lecture on Iterator Pattern (Behavioral Design) (110 to 115)
- The Iterator Pattern is allows sequential access to elements in a collection, without exposing their underlying representation. The object being sequentially accessed is an aggregate object.
- Typescript and Javascript have an implementation of this pattern.
- Try to understand this problem: [4]
    - Most collections store their elements in simple lists. However, some of them are based on stacks, trees, graphs and other complex data structures.
    - But no matter how a collection is structured, it must provide some way of accessing its elements so that other code can use these elements. There should be a way to go through each element of the collection without accessing the same elements over and over.
    - This may sound like an easy job if you have a collection based on a list. You just loop over all of the elements. But how do you sequentially traverse elements of a complex data structure, such as a tree? For example, one day you might be just fine with depth-first traversal of a tree. Yet the next day you might require breadth-first traversal. And the next week, you might need something else, like random access to the tree elements.
    - Adding more and more traversal algorithms to the collection gradually blurs its primary responsibility, which is efficient data storage. Additionally, some algorithms might be tailored for a specific application, so including them into a generic collection class would be weird.
    - On the other hand, the client code that’s supposed to work with various collections may not even care how they store their elements. However, since collections all provide different ways of accessing their elements, you have no option other than to couple your code to the specific collection classes.
- The main idea of the Iterator pattern is to extract the traversal behavior of a collection into a separate object called an iterator.
- One of the most common use case of this design pattern is when your collection can have multiple traversal methods. Like in case of binary tree. 
- Iterator pattern is used to create common traversing interfaces for different collection, this abstracts away different collection's complexity thus providing additional security.
- An iterator manages its state independently. It conserve state as well, so you don't need to start iteration from the beginning in some use cases.
- Major concern of iterator pattern is the change in state of collection. What if the state of collection changes while iterator is iterating through it? This can give unpredictable results.
- You can use Iterators to traverse Composite trees. [5]


# Lecture on Strategy Pattern (Behavioral Design) (116 to 121)
-  Strategy pattern lets you define a family of algorithms put each of them into separate classes, and make their objects interchangeable. The end goal is to the change the behavior of an object at runtime without changing its implementation.
-  Components of Strategy Pattern: Context, Strategy and Concrete Strategy.
- Context will provide which strategy has to be implemented. Strategy handles switch between strategy and concrete strategy is the business logic for implementation.
- Strategy pattern is used mostly in an existing bloated code base with lot of conditional to make it more maintainable.
- Helps in avoiding conditional logic and also helps in introducing Open/Close principle in codebase.
- Use Case: If you wanna modify sorting algorithm used for a certain set of data; image rendering (based on image rendering strategy); etc.
- The Strategy pattern suggests that you take a class that does something specific in a lot of different ways and extract all of these algorithms into separate classes called strategies. The original class, called context, must have a field for storing a reference to one of the strategies. The context delegates the work to a linked strategy object instead of executing it on its own.
- The context isn’t responsible for selecting an appropriate algorithm for the job. Instead, the client passes the desired strategy to the context. In fact, the context doesn’t know much about strategies. It works with all strategies through the same generic interface, which only exposes a single method for triggering the algorithm encapsulated within the selected strategy.
- This way the context becomes independent of concrete strategies, so you can add new algorithms or modify existing ones without changing the code of the context or other strategies. [6]


# Lecture on Template Method Pattern (Behavioral Design) (122 to 127)
- You define the skeleton of an algorithm in a base class but facilitates subclasses to override specific steps of the algorithm without changing its structure. This allows you to make parts of an algorithm optional, mandatory, or customizable by the subclasses.
- You use template pattern when you are repeating yourself between classes, or you have a lot of branching (conditional) inside the core method of a class.
- Template Method Pattern helps you to comply with Interface Segregation and Dependency Inversion in your source code.
- Since the template method pattern make use of inheritance, this leads to tight coupling which hinders the flexibility.
- The Template Method pattern suggests that you break down an algorithm into a series of steps, turn these steps into methods, and put a series of calls to these methods inside a single template method. The steps may either be abstract, or have some default implementation. [7]


# Lecture on Command Design Pattern (Behavioral Design) (127 to 133)
- This design pattern helps to turn a request into a standalone object that contains all information about the request. This transformation lets you pass requests as a method arguments, delay or queue a request's execution and support un-doable operations.
- This is a bit complicated command. Best explanation: [9]. Read the structure and pseudocode section. Here is some explanation from structure:
    1. The Sender class (aka invoker) is responsible for initiating requests. This class must have a field for storing a reference to a command object. The sender triggers that command instead of sending the request directly to the receiver. Note that the sender isn’t responsible for creating the command object. Usually, it gets a pre-created command from the client via the constructor.
    2. The Command interface usually declares just a single method for executing the command.
    3. Concrete Commands implement various kinds of requests. A concrete command isn’t supposed to perform the work on its own, but rather to pass the call to one of the business logic objects. However, for the sake of simplifying the code, these classes can be merged.
    Parameters required to execute a method on a receiving object can be declared as fields in the concrete command. You can make command objects immutable by only allowing the initialization of these fields via the constructor.
    4. The Receiver class contains some business logic. Almost any object may act as a receiver. Most commands only handle the details of how a request is passed to the receiver, while the receiver itself does the actual work.
    5. The Client creates and configures concrete command objects. The client must pass all of the request parameters, including a receiver instance, into the command’s constructor. After that, the resulting command may be associated with one or multiple senders.
- Undo and redo operations are implemented in Command Design Pattern.
- Commands which result in changing the state of the editor (e.g., cutting and pasting) make a backup copy of the editor’s state before executing an operation associated with the command. After a command is executed, it’s placed into the command history (a stack of command objects) along with the backup copy of the editor’s state at that point. Later, if the user needs to revert an operation, the app can take the most recent command from the history, read the associated backup of the editor’s state, and restore it.


# Lecture on State Design Pattern (Behavioral Design) (134 to 139)
- State Design Pattern is a behavioral design pattern that allows an object to change its behavior when its internal state changes.
- Situation to use: When behavior of an object is changing based on the current state.
- Take a drawing app as context and think about the tool you use in that application to draw on canvas.
- The main idea is that, at any given moment, there’s a finite number of states which a program can be in. Within any unique state, the program behaves differently, and the program can be switched from one state to another instantaneously. However, depending on a current state, the program may or may not switch to certain other states. These switching rules, called transitions, are also finite and predetermined.
- State machines are usually implemented with lots of conditional statements (if or switch) that select the appropriate behavior depending on the current state of the object. Usually, this “state” is just a set of values of the object’s fields. Even if you’ve never heard about finite-state machines before, you’ve probably tries to implement an if else condition with multi-set of business logic based on flow.
- The biggest weakness of a state machine based on conditionals reveals itself once we start adding more and more states and state-dependent behaviors. Most methods will contain monstrous conditionals that pick the proper behavior of a method according to the current state. Code like this is very difficult to maintain because any change to the transition logic may require changing state conditionals in every method. [10]
- The State pattern suggests that you create new classes for all possible states of an object and extract all state-specific behaviors into these classes. Instead of implementing all behaviors on its own, the original object, called context, stores a reference to one of the state objects that represents its current state, and delegates all the state-related work to that object.
- To transition the context into another state, replace the active state object with another object that represents that new state. This is possible only if all state classes follow the same interface and the context itself works with these objects through that interface.
- This structure may look similar to the Strategy pattern, but there’s one key difference. In the State pattern, the particular states may be aware of each other and initiate transitions from one state to another, whereas strategies almost never know about each other.
- It helps in introducing SRP (Single Responsibility Principle) and OCP (Open/Closed Principle) in your source code.


# Lecture on Chain of Responsibility Pattern (Behavioral Design) (140 to 145)
- You pass a request along a chain of handlers. Upon receiving the request each handler decides either to process the request or to pass it to the next handler in the chain.
- The chain of responsibility pattern is generally applicable when you have multiple objects that can potentially handle a request and their exact handler isn't predetermined but is determined at the runtime.
- Dependency on Order of Handlers is a big caveat of this Behavior Design Pattern, you need extra logic to make it functional.
- Middleware works in Chain of Responsibility Behavior pattern.
- Consider these scenarios:
    - One of your colleagues suggested that it’s unsafe to pass raw data straight to the ordering system. So you added an extra validation step to sanitize the data in a request.
    - Later, somebody noticed that the system is vulnerable to brute force password cracking. To negate this, you promptly added a check that filters repeated failed requests coming from the same IP address.
    - Someone else suggested that you could speed up the system by returning cached results on repeated requests containing the same data. Hence, you added another check which lets the request pass through to the system only if there’s no suitable cached response.
- Chain of Responsibility relies on transforming particular behaviors into stand-alone objects called handlers. In our case, each check should be extracted to its own class with a single method that performs the check. The request, along with its data, is passed to this method as an argument. [11]
- It’s crucial that all handler classes implement the same interface. Each concrete handler should only care about the following one having the execute method. This way you can compose chains at runtime, using various handlers without coupling your code to their concrete classes.
- Each linked handler has a field for storing a reference to the next handler in the chain. In addition to processing a request, handlers pass the request further along the chain. The request travels along the chain until all handlers have had a chance to process it. A handler can decide not to pass the request further down the chain and effectively stop any further processing.
- However, there’s a slightly different approach (and it’s a bit more canonical) in which, upon receiving a request, a handler decides whether it can process it. If it can, it doesn’t pass the request any further. So it’s either only one handler that processes the request or none at all.


# Random Stuff:
- Polling, Long Polling and Short Polling
- !== vs !=?
- Generic T in typescript?
- Aggregate: a whole formed by combining several (typically disparate) elements.
- Protected access modifier in typescript.
- SOLID Design Principles Posters. [8]
- Shift method in array.
- UML diagram for modelling class diagram before implementing.
- Subclasses?
- .?, ?: and other expressions in typescript. Abstract Class, Interface, protected, public and private access modifier. Union of types. T type. extends vs implements differences. Abstract Methods. Super keyword and its workings.
- Interface, abstract classes, inheritance and extension symbol in UML modelling.
- You can make a data flow structure using a class like structure with interfaces and abstract classes to create a blueprint of data flow in a system. This is a good way to practice and learn UML.

# References:
[1]: https://refactoring.guru/design-patterns/observer
[2]: https://www.geeksforgeeks.org/polling-in-system-design/#polling-strategies
[3]: https://khalilstemmler.com/blogs/typescript/node-starter-project/
[4]: https://refactoring.guru/design-patterns/iterator
[5]: https://refactoring.guru/design-patterns/iterator
[6]: https://refactoring.guru/design-patterns/strategy
[7]: https://refactoring.guru/design-patterns/template-method
[8]: https://www.globalnerdy.com/2009/07/15/the-solid-principles-explained-with-motivational-posters/
[9]: https://refactoring.guru/design-patterns/command
[10]: https://refactoring.guru/design-patterns/state
[11]: https://refactoring.guru/design-patterns/chain-of-responsibility