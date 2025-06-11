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


