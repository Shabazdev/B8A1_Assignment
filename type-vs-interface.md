# Type Aliases vs Interfaces in TypeScript

## Introduction

TypeScript offers both `type` aliases and `interface` declarations for describing the shape of data. They often look similar, but each has features that make it useful in different situations. Choosing the right one can make a codebase easier to understand and extend.

## Detailed Discussion

An interface is commonly used to describe the structure of objects and classes. Interfaces can be extended with `extends`, allowing one contract to build on another.

```ts
interface Person {
  name: string;
}

interface Developer extends Person {
  language: string;
}

const developer: Developer = {
  name: "Mina",
  language: "TypeScript"
};
```

A type alias can describe an object too, but it can also represent unions, intersections, tuples, and primitive aliases. This makes it useful when a type is more than a simple object shape.

```ts
type Status = "pending" | "approved" | "rejected";

type Account = {
  id: number;
  status: Status;
};

type AdminAccount = Account & {
  permissions: string[];
};
```

Another difference is declaration merging. Multiple declarations with the same interface name can merge their members. Type aliases cannot be reopened in this way. Both support many everyday object-typing tasks, so consistency across a project is important.

## Conclusion

Choose an interface when defining object contracts that may be extended or augmented, especially for class-oriented designs. Choose a type alias when creating unions, tuples, intersections, or other composite types. The best choice is the one that communicates the intended structure clearly and follows the conventions of the project.
