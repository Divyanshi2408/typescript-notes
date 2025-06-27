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


## Interview / Tricky Questions for “Union & Intersection Types”

### Q1. When would you use a union vs. an intersection?
- Use **union (`|`)** when a value can be one of many types.
- Use **intersection (`&`)** when a value should have all types’ properties.

---

### Q2. How does TypeScript narrow union types?
Through **type guards** such as:
- `typeof` (for primitives)
- `in` operator (for objects)
- `instanceof` (for classes)

---

### Q3. What is a discriminated union?
A **union of types** that share a common **literal property** (e.g., `kind`) used to narrow the type with `switch-case`.

---

### Q4. Can you use unions with literal types? Why is that useful?
✅ Yes! It restricts values to a defined set.

```ts
type Mode = "dark" | "light";
```

Useful for:
- UI themes
- HTTP methods
- Status codes

---

### Q5. What happens if two intersected types have conflicting property types?
❌ TypeScript throws an error due to incompatible type intersection:

```ts
type A = { id: string };
type B = { id: number };
// type C = A & B; // ❌ Error: Type 'string' is not assignable to type 'number'
```
