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


