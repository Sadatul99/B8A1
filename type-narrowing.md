# Type Narrowing in TypeScript

## Introduction

Type narrowing: TypeScript reduces a broad type to a more specific type after checking a value. We can safely use properties and methods that belong to one possible type with the help of type narrowing. 

## How narrowing works

The `typeof` operator is useful for primitive values. For example a function may receive a string or a number:

```ts
const print = (value: string | number) => {
  if (typeof value === "string") {
    return value.toUpperCase();
  } else {
    return value;
  }
};
```

Here inside the first branch, TypeScript knows `value` is a string. In the second branch, it knows `value` is a number.on the other hand `instanceof` checks whether an object was created from a class. This is helpful when different classes provide different methods:

```ts
class EmailNotice {
  sendEmail(): string { return "Email sent"; }
}

function send(notice: EmailNotice | Date): string {
  if (notice instanceof EmailNotice) return notice.sendEmail();
  return notice.toDateString();
}
```

The `in` operator checks whether a property exists on an object. For example, a `Bird` may have `fly`, while a `Fish` may have `swim`. Checking `"fly" in animal` allows TypeScript to identify which object is being used before calling its method.

```ts
type Bird = { fly: () => void };
type Fish = { swim: () => void };

const move = (animal: Bird | Fish) => {
  if ("fly" in animal) {
    animal.fly();
    return;
  }

  animal.swim();
};
```

## Conclusion

Union types are useful and safe when using narrowing. Use `typeof` with primitive values, `instanceof` with class instances and `in` where object shapes contain different properties. These checks also provide explanations to the reader of the program's decisions.
