# 📘 07. Interfaces

---

## 🧾 Declaring Interfaces

Interfaces define the shape of an object:

```ts
interface User {
  name: string;
  age: number;
}

const user: User = {
  name: "Divyanshi",
  age: 22,
};
```

## 🔗 Extending Interfaces
Interfaces can inherit from other interfaces using extends.

```
interface Person {
  name: string;
}

interface Employee extends Person {
  role: string;
}

const emp: Employee = {
  name: "Divyanshi",
  role: "Developer",
};
```
You can also extend multiple interfaces:

```
interface Contact {
  phone: string;
}

interface FullEmployee extends Person, Contact {
  role: string;
}
```

## 🔒 Readonly & Optional Properties
readonly makes a property immutable.

? makes a property optional.

```
interface Product {
  readonly id: number;
  name: string;
  description?: string;
}

const item: Product = {
  id: 101,
  name: "Notebook",
};

// item.id = 102; ❌ Error: Cannot assign to 'id' because it is a read-only property
```

## ✅ Summary

| Concept                | Description                                             |
|------------------------|---------------------------------------------------------|
| Declaring Interfaces   | Define the shape of an object                           |
| Extending Interfaces   | Create new interfaces by inheriting others              |
| `readonly` Property    | Makes the property immutable after assignment           |
| Optional Property (`?`)| Allows a property to be omitted                         |

## 📘 Interview Questions for “Interfaces”

### Q1. How is an `interface` different from a `type` alias?
- `interface` supports **declaration merging**, `type` does not.
- `type` is more **flexible** (can describe primitives, unions, etc.).

---

### Q2. Can interfaces have methods? Can they be optional?
✅ Yes. Example:

```ts
interface Clock {
  now(): Date;
  reset?(): void;
}
```

---

### Q3. Can a class implement multiple interfaces?
✅ Yes.

```ts
interface Printable { print(): void; }
interface Scannable { scan(): void; }

class Machine implements Printable, Scannable {
  print() {}
  scan() {}
}
```

---

### Q4. What happens if you declare an interface twice?
TypeScript **merges them**:

```ts
interface A { name: string; }
interface A { age: number; }

const a: A = { name: "Divyanshi", age: 22 }; // ✅ Valid
```

---

### Q5. When should you use `interface` over `type` alias?
- When defining **object shapes** or **class contracts**
- When you want **declaration merging**
- When using **third-party library APIs**

