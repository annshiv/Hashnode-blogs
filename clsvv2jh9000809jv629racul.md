---
title: "TypeScript Narrowing: Powerful Techniques for Precise Type Checking"
datePublished: Wed Feb 21 2024 13:59:49 GMT+0000 (Coordinated Universal Time)
cuid: clsvv2jh9000809jv629racul
slug: typescript-narrowing-powerful-techniques-for-precise-type-checking
canonical: https://medium.com/@annamalaipalani11/typescript-narrowing-powerful-techniques-for-precise-type-checking-85234e593096
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/VPmMy8YA_cU/upload/c8a1e3fe69181e4e7c187609cf9d37f6.jpeg
tags: reactjs, typescript

---

TypeScript is a powerful and popular programming language that brings static typing to JavaScript. One of its key features is its strong type inference and type checking capabilities, which help catch bugs and improve code quality. One powerful technique in TypeScript is “narrowing,” which allows developers to precisely narrow down the types of variables or expressions based on certain conditions, leading to more accurate and reliable type checking. In this blog post, we will explore different techniques for mastering TypeScript narrowing and leverage its benefits to write robust and error-free code.

![](https://miro.medium.com/v2/resize:fit:1400/0*G1Ier7MADpOiOCUJ align="left")

Photo by [Cookie the Pom](https://unsplash.com/@cookiethepom?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

1. **Type Guards:**
    

Type guards are functions or conditions that allow TypeScript to narrow down the type of a variable based on a runtime check. For example, using the typeof operator, we can create a type guard to differentiate between different types of variables, such as strings, numbers, or booleans. We can also use instance-of to narrow down the type of an object based on its constructor.

Example:

```typescript
function printLength(value: string | number): void {
  if (typeof value === 'string') {
    console.log(value.length); // TypeScript knows that value is a string, so length is valid
  } else {
    console.log(value); // TypeScript knows that value is a number
  }
}
```

**2\. Discriminated Unions:**

Discriminated Unions, also known as tagged unions or algebraic data types, are a powerful pattern in TypeScript for narrowing down types based on a common discriminator property. By using a shared property with a unique value across all variants of a union, we can create a type guard that narrows down the type based on that property.

Example:

```typescript
interface Circle {
  kind: 'circle';
  radius: number;
}

interface Square {
  kind: 'square';
  sideLength: number;
}

type Shape = Circle | Square;

function printArea(shape: Shape): void {
  if (shape.kind === 'circle') {
    console.log(Math.PI * shape.radius * shape.radius); // TypeScript knows that shape is a circle
  } else {
    console.log(shape.sideLength * shape.sideLength); // TypeScript knows that shape is a square
  }
}
```

**3\. Nullish Coalescing Operator:**

The nullish coalescing operator (`??`) is a handy tool for narrowing down types when dealing with potentially nullable or undefined values. It allows us to provide a default value when the variable is null or undefined, and TypeScript can accurately narrow down the type based on the result.

Example:

```typescript
function printUsername(username: string | null): void {
  const name = username ?? 'Guest'; // TypeScript knows that name is a string, even if username is null
  console.log(`Hello, ${name}!`);
}
```

**4\. Custom Type Predicates:**

TypeScript also allows developers to create their own custom type predicates, which are functions that return a boolean value and can be used as type guards. Custom type predicates can be helpful when dealing with complex data structures or custom validation logic.

Example:

```typescript
function isPerson(obj: any): obj is Person {
  return obj && typeof obj === 'object' && 'name' in obj && 'age' in obj;
}

function printPersonDetails(person: Person | string): void {
  if (isPerson(person)) {
    console.log(`Name: ${person.name}, Age: ${person.age}`); // TypeScript knows that person is a Person object
  } else {
    console.log(person); // TypeScript knows that person is a string
  }
}
```

In conclusion, TypeScript narrowing is a powerful technique that allows developers to write more precise and reliable type checking in their code.