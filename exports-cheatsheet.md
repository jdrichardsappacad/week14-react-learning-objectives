## EXPORTS

**There are 2 types of exports:**

1. Named Exports
2. Default Exports

You can have as many named exports as you want in a file/module.
But you can only have **one** default export.

You can export any data structure you choose.

If you do not export a variable or function from the file it will not be accessible
to other files/modules

### Named Export Examples

```js
export const str = 'Hello World';

export const num1 = 100;
export const num2 = 200;

export const array = ['apple', 'pear', 'banana'];

export const obj = {
  firstName: 'Foo',
  lastName: 'Bar'
};

export function add(number1, number2) {
  return number1 + number2;
}
```

**You Can Only Have One Default export**

```js
export default subtract(number1, number2){
return number1 - number2;
}
```

\*\*\* _This also applies to components. If you have more than one component in the same file to export, you can only export default one of them_

Go to [Imports](./imports.md) to see how to import

### Links:

- [Answers](./learning-objectives-filled)
- [Imports CheatSheet](./imports-cheatsheet)
- [Exports CheatSheet](./exports-cheatsheet)
- [Read Me](./README.md)
