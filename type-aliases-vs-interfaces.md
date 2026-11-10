# Type Aliases vs Interfaces in TypeScript

## Introduction


Type aliases and interfaces both give the structure of an object. But it has some major differences. Both are usefull for different situations.



## Main differences

we can extend a interface but not the type, that means same interface name in two different places merge together and act as one. On the other hand we cannnot do this with the Type aliases:

```ts
interface Person {
  name: string;
}

interface Person {
  age: number;
}

const person: Person = { name: "sadatul", age: 24 };
```



Here we can see typescript merges two interfaces named `Person`.This feature is useful when a library lets other developers add fields to an existing interface.



In type alias we use keyword named `type`. rather than describing an object shape it can also describe the unions , primitives and tuples.

```ts
type Status = "loading" | "success" | "error";
type Point = [number, number];
type Account = { username: string; active: boolean };
```

Here we see type aliases can combine types with unions (`|`) and intersections (`&`). Unlike interfaces, repeating a type alias declaration with the same name causes an error.


## Conclusion

In conclusion , we should choose the type aliases when we need a union, tuple, primitive alias, or a combination of types and choose an interface for object contracts that may be extended or merged
