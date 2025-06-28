# 📘 08. Classes & OOP in TypeScript

---

## 🏗️ Classes and Constructors

You can create classes just like in other OOP languages:

```ts
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  greet(): void {
    console.log(`Hello, I'm ${this.name}`);
  }
}

const user = new Person("Divyanshi", 22);
user.greet(); // Hello, I'm Divyanshi
```

## 🔐 Access Modifiers

| Modifier   | Scope                                              |
|------------|----------------------------------------------------|
| `public`   | (default) Accessible from anywhere                 |
| `private`  | Accessible only within the class                   |
| `protected`| Accessible within the class and its subclasses     |


Example:
```
class Animal {
  protected name: string;

  constructor(name: string) {
    this.name = name;
  }

  move(): void {
    console.log(`${this.name} is moving`);
  }
}

class Dog extends Animal {
  bark(): void {
    console.log(`${this.name} says Woof!`);
  }
}
```

## 🧬 Inheritance & Abstract Classes

### ✅ Inheritance
```
class Vehicle {
  drive(): void {
    console.log("Driving...");
  }
}

class Car extends Vehicle {
  honk(): void {
    console.log("Beep beep!");
  }
}
```
### ✅ Abstract Classes
Used to define a base class with some shared logic and some abstract methods:

```
abstract class Shape {
  abstract getArea(): number;

  describe(): void {
    console.log("I am a shape.");
  }
}

class Circle extends Shape {
  constructor(public radius: number) {
    super();
  }

  getArea(): number {
    return Math.PI * this.radius ** 2;
  }
}
```

## 🧩 Implementing Interfaces in Classes
A class can implement an interface to enforce structure:

```
interface Printable {
  print(): void;
}

class Report implements Printable {
  print(): void {
    console.log("Printing report...");
  }
}
```

## ✅ Summary

| Concept                    | Description                                               |
|----------------------------|-----------------------------------------------------------|
| Classes & Constructors     | Define reusable blueprints for objects                    |
| Public / Private / Protected | Control member accessibility                          |
| Inheritance                | Allows a class to extend another                          |
| Abstract Classes           | Provide a base class with abstract methods                |
| Implementing Interfaces    | Enforce structure on class using interfaces               |


## 🧱 Interview / Tricky Questions for “Classes & OOP”

### Q1. What’s the difference between `private`, `protected`, and `public` in TypeScript?

- `private`: Only accessible inside the class.
- `protected`: Accessible inside the class and subclasses.
- `public`: Accessible from anywhere (default).

---

### Q2. When would you use an abstract class over an interface?

- Use **abstract classes** when you want to **share base implementation** and **enforce contracts**.
- Use **interfaces** when you only need to **enforce structure** (and support multiple inheritance).

---

### Q3. Can a class implement multiple interfaces in TypeScript?
✅ Yes.

```ts
interface A { foo(): void; }
interface B { bar(): void; }

class MyClass implements A, B {
  foo() {}
  bar() {}
}
```

---

### Q4. What is the use of `readonly` in class properties?

It makes the property **immutable after initialization** — similar to constants.

---

### Q5. How does inheritance differ from implementation in TypeScript?

| Term       | Meaning                                |
|------------|----------------------------------------|
| `extends`  | Inherit from another class             |
| `implements` | Enforce structure based on interface |
