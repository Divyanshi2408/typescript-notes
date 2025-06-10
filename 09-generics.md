# 📘 09. Generics in TypeScript

---

## 🧠 What are Generics?

Generics allow you to write reusable, type-safe code by allowing types to be passed as parameters.

> ✅ Think of generics as variables for types.

---

## 🔧 Generic Functions

```ts
function identity<T>(value: T): T {
  return value;
}

const str = identity<string>("Hello");
const num = identity<number>(123);
```
Type <T> is a placeholder for any type passed when calling the function.

## 🧱 Generic Interfaces
```
interface Box<T> {
  content: T;
}

const stringBox: Box<string> = { content: "Text" };
const numberBox: Box<number> = { content: 100 };
```

## 🏗️ Generic Classes
```
class DataStore<T> {
  private items: T[] = [];

  add(item: T): void {
    this.items.push(item);
  }

  getAll(): T[] {
    return this.items;
  }
}

const numberStore = new DataStore<number>();
numberStore.add(10);
numberStore.add(20);
```

## 🚫 Generic Constraints
Use extends to constrain types that can be used:

```
function logLength<T extends { length: number }>(item: T): void {
  console.log(item.length);
}

logLength("hello");
logLength([1, 2, 3]);
// logLength(10); ❌ Error: number doesn't have length
```

## 📦 Built-in Utility Generics

TypeScript provides several helpful built-in generic types:

| Utility Type   | Description                                      |
|----------------|--------------------------------------------------|
| `Partial<T>`   | Makes all properties optional                    |
| `Readonly<T>`  | Makes all properties read-only                   |
| `Record<K, T>` | Creates a type with keys `K` and values `T`      |
| `Pick<T, K>`   | Picks specific keys from type `T`                |
| `Omit<T, K>`   | Omits specific keys from type `T`                |


### ✅ Example: Partial
```
interface User {
  name: string;
  age: number;
}

const updateUser = (user: Partial<User>) => {
  // user.name and user.age are optional here
};
```

## ✅ Summary

| Concept              | Description                                                    |
|----------------------|----------------------------------------------------------------|
| Generic Functions    | Functions that work with any type                              |
| Generic Interfaces   | Interfaces with flexible type properties                       |
| Generic Classes      | Reusable class logic for multiple types                        |
| Constraints (`extends`) | Restrict types to have specific structure                 |
| Utility Generics     | Built-in helpers like `Partial`, `Readonly`, `Pick`, etc.      |
