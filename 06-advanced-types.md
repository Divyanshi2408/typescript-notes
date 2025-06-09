# 📘 06. Advanced Types

---

## 🔹 Literal Types

A literal type is a specific value you allow a variable to have.

```ts
type Direction = "left" | "right" | "up" | "down";

let move: Direction;
move = "left";  // ✅ OK
// move = "forward"; ❌ Error
```
Useful for modeling limited states.

## ❓ Nullable Types
You can explicitly allow null or undefined in your types:

```
let name: string | null = null;

function greet(user?: string) {
  if (user) {
    console.log("Hello", user);
  } else {
    console.log("Hello guest");
  }
}
```
Use union (|) to combine with null/undefined.

## ⚙️ Type Inference
TypeScript infers the type automatically based on the assigned value:

```
let age = 25; // inferred as number
let username = "divyanshi"; // inferred as string
```
You can still explicitly type it if needed:

```
let age: number = 25;
```
## 🏷️ as Keyword (Type Assertions)
Used when you know more about the type than TypeScript does:

```
let value: unknown = "hello";
let strLength = (value as string).length;
```
You can also use angle bracket syntax:

```
let len = (<string>value).length;
```

## 🔑 keyof, typeof, in, infer
keyof
Returns the keys of a type:

```
type User = { name: string; age: number };
type UserKeys = keyof User; // "name" | "age"
```
## typeof
Extracts the type of a variable or function:

```
let user = { name: "Divyanshi", age: 22 };
type UserType = typeof user; // same as { name: string; age: number }
```

## in
Used in mapped types:

```
type Keys = "name" | "age";
type Person = {
  [K in Keys]: string;
};
```

## infer (Used in Conditional Types)
Extracts a type part from another:

```
type GetReturnType<T> = T extends (...args: any[]) => infer R ? R : never;

type Result = GetReturnType<() => number>; // number
```

## ✅ Summary

| Concept           | Description                                                       |
|-------------------|-------------------------------------------------------------------|
| Literal Types     | Restrict variable to exact values (`"up"`, `"down"`, etc.)        |
| Nullable Types    | Allow `null` or `undefined` with union types                      |
| Type Inference    | TypeScript guesses variable types from assignment                 |
| `as` Keyword      | Force type with type assertions                                   |
| `keyof`           | Gets property names of a type as a union of string literals       |
| `typeof`          | Gets the type of a value or variable                              |
| `in`              | Used in mapped types to iterate over keys                         |
| `infer`           | Extracts type in conditional types                                |
