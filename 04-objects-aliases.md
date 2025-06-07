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
