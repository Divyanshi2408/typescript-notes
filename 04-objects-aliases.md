# 📘 04. Objects & Type Aliases

---

## Object Types

You can define the structure of an object using inline type annotations:

```ts
const user: { name: string; age: number } = {
  name: "Divyanshi",
  age: 22,
};
```
This gets messy for complex objects. That's where type aliases and interfaces come in.

## 🔖 Type Alias (type)
A type lets you give a name to an object shape or any other type.

```
type User = {
  name: string;
  age: number;
  isAdmin?: boolean; // optional property
};

const user1: User = {
  name: "Divyanshi",
  age: 22,
};
```
You can also use type with unions:

```
type Status = "success" | "error" | "loading";
let state: Status = "success";
```

## 🆚 Interfaces vs Type Aliases
Both can be used to define object types, but there are subtle differences:

### ✅ Interface
```
interface Product {
  name: string;
  price: number;
}
```
### ✅ Type Alias (for objects)
```
type Product = {
  name: string;
  price: number;
};
```

## 🔄 Key Differences

| Feature                    | `interface`                      | `type`                            |
|----------------------------|----------------------------------|-----------------------------------|
| Extendable (inheritance)   | ✅ Yes (`extends`)               | ✅ Yes (with intersections `&`)   |
| Union/Intersection support | ❌ No                            | ✅ Yes                            |
| Declaration merging        | ✅ Yes                           | ❌ No                             |
| Recommended use            | Object structures                | Unions, primitives, functions     |


## 🔗 Extending Types & Interfaces
Extending an interface:
```
interface Person {
  name: string;
}

interface Employee extends Person {
  role: string;
}
```
Extending a type:
```
type Person = {
  name: string;
};

type Employee = Person & {
  role: string;
};
```

## ✅ Summary

| Concept              | Description                                                   |
|----------------------|---------------------------------------------------------------|
| Object Types         | Define structure using inline or reusable annotations         |
| Type Alias (`type`)  | Give a name to object types, unions, and primitives           |
| Interface            | Define object structure with extendable, mergeable types      |
| `interface` vs `type`| Interfaces are better for objects, types for flexibility       |
| Extensions           | Both can be extended (`extends` or `&`)                       |


## Interview / Tricky Questions for “Objects & Type Aliases”

### Q1. What are the key differences between `type` and `interface` in TypeScript?
- `interface` supports **declaration merging**; `type` does not.
- `type` can define **primitives, unions, tuples**; `interface` cannot.
- Both support extension, but their syntax differs.

---

### Q2. Can you extend a `type` from an `interface` or vice versa?
✅ Yes.

```ts
interface A {
  name: string;
}

type B = A & { age: number }; // type extends interface

type X = { id: number };

interface Y extends X {}      // interface extends type
```

---

### Q3. When would you choose `type` over `interface`?
- When you need to define **unions**, **tuples**, or use **complex types**
- When you need **flexibility in generic constraints**

---

### Q4. Can interfaces have optional properties? What about `readonly`?
✅ Yes, both are supported.

```ts
interface User {
  name: string;
  age?: number;
  readonly id: string;
}
```

---

### Q5. Why is `interface` preferred for public APIs?
- **Declaration merging** allows for extendability.
- Better **tooling support** (especially in libraries/SDKs).
- Interfaces clearly represent **structured object contracts**.

