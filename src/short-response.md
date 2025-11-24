# Section 2 — Short Response

Write your responses directly in this file. Follow markdown formatting guidelines. Check the rubric.md file to see how your short responses will be graded. 

As a quick guide, check the following before submitting:
- [] Answered all parts of every question
- [] No typos or grammar mistakes (use grammarly!)
- [] Accurately uses relevant technical terminology
- [] Uses markdown to enhance readability (preview in VS Code with Command/Control + Shift + V)
- [] Responses are concise and easy to comprehend

---

## Question 1

In your own words, explain what does _encapsulation_ refer to? Why is this concept beneficial when programming? 

Provide a code snippet to illustrate _encapsulation_.

## Response 1
**Encapsulation** refers to the class properties as **private** and prevents direct access from outside the class. The concept is beneficial when programming because it maintains **data integrity**. By hiding the data, it becomes easier to control who can access or modify it.

For example, you can create an `Account` class with a private `balance` property. This balance cannot be accessed directly from outside the class. To get the balance, you will need a getter method. If you try to access the private property `balance` directly from the console, you will not be able to access it.

```js
class Account {
  #balance = 8547;

  get balance() {
    return this.#balance;
  }
}

const acc = new Account()
console.log(acc.balance)
```

---

## Question 2

Explain what the `this` keyword is. Why is the `this` keyword useful?

In the code snippet below, what does `this` refer to?

```js
class Counter {
	constructor() {
		this.count = 0;
	}
  increment() {
    this.count++;
  }
}

const counterA = new Counter();
const counterB = new Counter();

counterA.increment();
counterA.increment();
counterA.increment();

counterB.increment();

console.log(counterA.count);
console.log(counterB.count);
```

## Response 2
The `this` keyword contains a reference to the object itself. It can also be the name of a reference that an object can use to refer to itself. The `this` keyword is useful when it is needed to reference the data hidden by a method, constructor parameter, or to invoke an overloaded constructor.

In the following code snippet, the `this` keyword refers to two objects, `counterA` and `counterB`, that are **instances** of the `Counter` class. Both of the objects are their own separate objects and store their own values.  The constructor has a property `this.count` refer to the new object that is being created and is initialize to 0. When `increment()` is called, it increases the instances `count` property by 1.

For example, the `increment()` method, `counterA`, is invoked three times, and `counterB` is invoked one time. Each object's `count` property will track how many times the `increment` method has been invoked. The console will output `counterA` count: 3, and `counterB` count: 1.

---

## Question 3

In your own words, explain what **polymorphism** means in OOP. Provide an example in code that demonstrates polymorphism.

## Response 3
**Polymorphism** means an object of a subclass can be used wherever its superclass is used. It is usually implemented through method overriding in subclasses, which requires **inheritance**. The subclass must extend a parent class to override its methods.

```js
class Animal {
  makeNoise() {
    console.log('...');
  }
}

class Dog extends Animal {
  makeNoise() {
    console.log('Bark!');
  }
}

class Cat extends Animal {
  makeNoise() {
    console.log('Meow!');
  }
}
```
From the following code above, `Dog` and `Cat` are subclasses of `Animal`. Both of the subclasses override the `speak()` method inherited from `Animal`, where each behavior is specific to each animal. This is called **method overriding**, allowing each subclass to have its own version of `speak()`. 

---

## Question 4

You're building a game where players can raise different digital pets: Cats, Dogs, and Birds. All pets have have a `name`, `energy` level, and `happiness` level and can all `sleep`. Cats have the ability to `hunt`, dogs have the ability to `chase`, and birds have the ability to `fly`.

**Part A:** Describe in words how you would use inheritance to organize these classes.

**Part B:** Explain one advantage of using inheritance here instead of creating three completely separate classes.

## Response 4
#### **Part A**
I would create a superclass `Pet` and the subclasses `Cat`, `Dog`, and `Bird` that extend `Pet`. The superclass would have a constructor with instance properties: `name`, `energy`, and `happiness` and a `sleep()` method. For each subclass, they have their own unique behavior: `Cat` would have `hunt()` method, `Dog` would have `chase()` method, and `Bird` would have `fly()` method. 

#### **Part B**
One advantage of using inheritance here instead of creating three different classes reduces redundant repetition. It makes the program clearer and easier to understand because all pets share the same features, such as `name`, `energy`, `happiness`, and the ability to sleep. There is no need to rewrite them in each class.