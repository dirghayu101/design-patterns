# Programming Paradigms:
- Object Oriented Programming: Object Oriented Programming (OOP) is a programming paradigm that uses the concept of objects as a way to structure and organize code. It is based on the principles of abstraction, encapsulation, inheritance, and polymorphism, which enable developers to build more flexible, reusable, and maintainable software.
- Concurrent Programming: This paradigm is designed to handle multiple tasks simultaneously, either by dividing a problem into smaller sub-tasks that can be executed concurrently or by running multiple independent tasks in parallel. Concurrent programming often relies on constructs like threads, processes, or coroutines, and requires developers to consider synchronization and communication between tasks. Examples of languages that support concurrent programming include Go, Rust, and Java.
- Event Driven Programming: In this paradigm, the flow of the program is determined by events, such as user actions, sensor outputs, or messages from other programs. The program defines event handlers, which are functions that are triggered when specific events occur. This paradigm is often used in graphical user interfaces, real-time systems, and serverless computing. Examples of event-driven programming languages or frameworks include JavaScript, Node.js, and Python's Twisted.
- Logic Programming: This paradigm is based on formal logic, where programs consist of a series of statements expressing facts and rules about a problem domain. The programming language's interpreter searches for proofs of queries by applying inference rules on the facts and rules defined in the program. Examples of logic programming languages include Prolog and Mercury.
- Functional Programming: Functional programming treats computation as the evaluation of mathematical functions and avoids changing state or mutable data. It emphasizes immutability, first-class functions, and the use of higher-order functions, leading to more predictable and easier-to-debug code. Examples of functional programming languages include Haskell, Lisp, Erlang, and Clojure.
- Procedural Programming: This paradigm is based on the concept of procedures (also known as routines, subroutines, or functions), which are a series of computational steps to be carried out. Procedural programming focuses on the explicit sequence of actions required to solve a problem, using constructs such as loops, conditionals, and variables. Examples of procedural programming languages include C, Pascal, and Fortran.


# Abstraction:
- It involves hiding the implementation details of a system and exposing only the essential features to the user. Abstraction allows developers to focus on the core functionality of a component without being concerned with the underlying complexity, making code easier to understand, maintain, and extend.
- In TypeScript, abstraction is achieved through classes and interfaces. Classes allow you to define blueprints for creating objects, while interfaces define the contract that a class must adhere to. Interfaces are used to enforce a certain structure on classes, ensuring that they have the required properties and methods.

# Encapsulation:
- Encapsulation is a fundamental concept in object-oriented programming (OOP) that refers to the practice of bundling together data (attributes) and the methods ( functions) that operate on that data within a single unit, typically a class. 
- In encapsulation, an object's internal state is protected from direct manipulation or access by external code. Instead, access to the object's state is provided through a well-defined interface, usually in the form of getter and setter methods. This allows for better control and validation of data, and it ensures that the object's internal state remains consistent.
- Encapsulation isn't just about hiding data or making it private. It's about bundling related data and behaviors into a single unit, and defining clear interfaces for interacting with that data.

# Polymorphism:
- Polymorphism is a fundamental concept in object-oriented programming (OOP) that allows objects of different classes to be treated as objects of a common superclass.
- Abstract classes and methods are used to facilitate polymorphism in TS. 
- An abstract class can have shared state or functionality. An interface is only a promise to provide the state or functionality. A good abstract class will reduce the amount of code that has to be rewritten because it's functionality or state can be shared. The interface has no defined information to be shared

