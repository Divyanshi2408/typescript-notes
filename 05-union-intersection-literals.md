# 📘 05. Union & Intersection Types

---

## 🔹 Union Types (`|`)

Union types allow a variable to hold one of several types.

```ts
let value: string | number;

value = "Hello";  // ✅ OK
value = 42;       // ✅ OK
// value = true;  ❌ Error
```
Useful for accepting multiple input formats or states:

```
function printId(id: number | string) {
  console.log("ID:", id);
}
```

## 🔗 Intersection Types (&)
Intersection types combine multiple types into one. The variable must satisfy all the included types.

```
type User = { name: string };
type Admin = { role: string };

type AdminUser = User & Admin;

const admin: AdminUser = {
  name: "Divyanshi",
  role: "admin",
};
```

## 🔍 Type Narrowing (Type Guards)
To use union types effectively, we narrow them down using type guards:

### ✅ Using typeof
```
function process(value: string | number) {
  if (typeof value === "string") {
    console.log(value.toUpperCase());
  } else {
    console.log(value.toFixed(2));
  }
}
```

### ✅ Using in for object types
```
type Car = { wheels: number };
type Boat = { sails: number };

function describe(vehicle: Car | Boat) {
  if ("wheels" in vehicle) {
    console.log("Car with", vehicle.wheels, "wheels");
  } else {
    console.log("Boat with", vehicle.sails, "sails");
  }
}
```

## ✅ Summary

| Concept                 | Description                                                |
|-------------------------|------------------------------------------------------------|
| Union Types (`|`)       | Variable can be one of several types                       |
| Intersection Types (`&`)| Combine multiple types into one composite type             |
| Type Guards             | Used to narrow union types into specific types             |
| `typeof` Check          | Used to check primitive types like `string`, `number`, etc.|
| `in` Operator           | Used to check properties in object union types             |

