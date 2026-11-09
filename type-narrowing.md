# Type Narrowing in TypeScript

## Introduction

A union type allows a value to hold more than one possible type. Before using that value in a type-specific way, TypeScript needs evidence about which type is currently present. Type narrowing is the process of using checks to reduce a broad type to a more specific one.

## Detailed Discussion

The `typeof` operator is useful for primitive values such as strings and numbers. TypeScript understands the check and permits operations that match the narrowed type.

```ts
function formatValue(value: string | number): string {
  if (typeof value === "string") {
    return value.trim().toLowerCase();
  }

  return value.toFixed(2);
}
```

The `instanceof` operator checks whether an object was created from a particular class or constructor. It is useful when different classes provide different methods.

```ts
class Dog {
  bark(): string {
    return "Woof";
  }
}

class Cat {
  meow(): string {
    return "Meow";
  }
}

function makeSound(pet: Dog | Cat): string {
  if (pet instanceof Dog) {
    return pet.bark();
  }

  return pet.meow();
}
```

The `in` operator checks whether a property exists on an object. It can distinguish object types that have different property names.

```ts
type EmailUser = { email: string };
type PhoneUser = { phone: string };

function getContact(user: EmailUser | PhoneUser): string {
  if ("email" in user) {
    return user.email;
  }

  return user.phone;
}
```

## Conclusion

Type narrowing helps TypeScript verify that operations are safe without relying on `any` or unsafe assumptions. Use `typeof` for primitive values, `instanceof` for class instances, and `in` for checking object properties. These checks make union-based code clearer and safer.
