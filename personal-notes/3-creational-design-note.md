### Course: Design Patterns in Typescript
## Terminology Introduction and Lectures 48 to 56

# Terminology Introduction: (Creational, Structural and Behavioral Design Patterns)
- Creational Design Pattern: Creational design patterns provide various object creation mechanisms, which increase flexibility and reuse of existing code.
- Structural Design Pattern: Structural design patterns explain how to assemble objects and classes into larger structures, while keeping these structures flexible and efficient.
- Behavioral Design Pattern: Behavioral design patterns are concerned with algorithms and the assignment of responsibilities between objects.
- [2] Design patterns are typical solutions to commonly occurring problems in software design. They are like pre-made blueprints that you can customize to solve a recurring design problem in your code.
- [2] You can’t just find a pattern and copy it into your program, the way you can with off-the-shelf functions or libraries. The pattern is not a specific piece of code, but a general concept for solving a particular problem. You can follow the pattern details and implement a solution that suits the realities of your own program.
- [2] Patterns are often confused with algorithms, because both concepts describe typical solutions to some known problems. While an algorithm always defines a clear set of actions that can achieve some goal, a pattern is a more high-level description of a solution. The code of the same pattern applied to two different programs may be different.
- [2] An analogy to an algorithm is a cooking recipe: both have clear steps to achieve a goal. On the other hand, a pattern is more like a blueprint: you can see what the result and its features are, but the exact order of implementation is up to you.

# Lecture 48, 49, 50, 51, 52, 53: Prototype Pattern (Creational Design Pattern)
-  Prototype Pattern is usually used for cloning objects. Since in ts there will be references instead of true copy, this helps in cloning object. 
- Situation: There is a large object which need to be cloned with some property changed. We will use prototype pattern.
- Avoidance of Reference Error: Very common in JS and TS, so you will be using Prototype Pattern extensively. 
- Shallow vs Deep Copying: 
     ```js
     let originalObject = {
        a: 'john',
        b: {
            c: 'Whiskey'
        }
     }

     let shallowCopyOriginalObject = {...originalObject};
     shallowCopyOriginalObject.b.c = 'Vodka';
     // Will be vodka.
     console.log(shallowCopyOriginalObject.b.c)
     // Will also be Vodka, should be whiskey.
     console.log(originalObject.b.c);

     // To make a deep copy:
     let deepCopyOriginalObject = JSON.parse(JSON.stringify(originalObject));
     ```
    In the above example, deep copy won't be able to copy an object with methods. 
- Other problem with prototype pattern is that if an object is complex with several methods, how would you be going around creating a deep copy of it? What would be your implementation like? This poses a challenge.
- Real Life use case: Graphic Editor, Game Development to create NPCs, Replicating DBMS Schema also utilizes Prototype pattern to clone data, even in case of Data Processing Pipeline.
- Implementation of Prototype Pattern in Java: [1]

# Lecture 54, 55, 56, 57, 58, 59 on Builder Pattern (Creational Design Pattern)
- Builder Pattern Components: Concrete Builder, Builder Part 'A', Builder Part 'B', Builder Part '...n', Director
-  I didn't get this syntax:
    ```ts 
        private product!: Product;
    ```
- Complex Object with Step by step building process would be a best fit for Builder Pattern.
- Problem of Combination Explosion. Builder pattern solve this. Read more.
- If you want to create an immutable object with many attributes, builder pattern might be a good fit.
- Client side can still use builder without a director method, which increases the chance of runtime error for builder pattern.

# References:
[1]: https://medium.com/design-patterns-with-java/understanding-prototype-pattern-377e93dd93d8
[2]: https://refactoring.guru/design-patterns/what-is-pattern