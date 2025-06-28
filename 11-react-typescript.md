# ⚛️ 11. Using TypeScript with React

---

## 🛠️ Setup

Install React + TypeScript template:

```bash
npx create-react-app my-app --template typescript
```

Or manually install in an existing React project:

```
npm install --save typescript @types/react @types/react-dom
```

## 📋 TypeScript with React Components
### ✅ Function Components
```
type Props = {
  name: string;
  age?: number;
};

const Greeting: React.FC<Props> = ({ name, age }) => {
  return <h1>Hello, {name} {age && `(${age})`}</h1>;
};
```

## 📝 useState with Types
```
const [count, setCount] = useState<number>(0);
```
Use union types:
```
const [status, setStatus] = useState<"loading" | "success" | "error">("loading");
```

## 🎯 Event Handling
```
const handleClick = (e: React.MouseEvent<HTMLButtonElement>) => {
  console.log(e.currentTarget);
};
```

## 🔄 useRef
```
const inputRef = useRef<HTMLInputElement>(null);
```

## 📦 Props and Children
```
type CardProps = {
  children: React.ReactNode;
};

const Card = ({ children }: CardProps) => {
  return <div className="card">{children}</div>;
};
```

## 🔌 Forms & Input Types
```
const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
  setValue(e.target.value);
};
```

## ✅ Summary

| Concept          | Description                                                        |
|------------------|--------------------------------------------------------------------|
| Component Props  | Define `Props` type and use with `React.FC<Props>`                |
| useState         | Use generic types like `useState<number>()`                        |
| Event Handling   | Type events like `React.ChangeEvent<HTMLInputElement>`             |
| useRef           | Use generics like `useRef<HTMLInputElement>(null)`                |
| ReactNode        | Use `React.ReactNode` for reusable children props                 |

## Interview / Tricky Questions

### Q1. Why is `useRef<HTMLInputElement>(null)` used?
To safely reference **DOM elements** in functional components using TypeScript.

---

### Q2. What's the difference between `React.FC<Props>` and explicitly typed props?

| Feature         | `React.FC`                 | Explicit Props               |
|------------------|-----------------------------|-------------------------------|
| Children Support | ✅ Included automatically     | ❌ Must be added manually      |
| Default Props    | ❌ Not inferred automatically | ✅ Works better                |
| Community Usage  | ⚠️ Optional                  | ✅ Recommended by many teams   |

---

### Q3. How do you type event handlers in TypeScript?

```tsx
const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {};
const handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {};
```

---

### Q4. How do you handle dynamic form inputs?

```tsx
type FormFields = "name" | "email";

const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
  const field: FormFields = e.target.name as FormFields;
};
```
