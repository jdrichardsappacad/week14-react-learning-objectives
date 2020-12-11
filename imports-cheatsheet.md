## ES6 IMPORTS

Imports are handled differently in ES6 Modules than in CommonJS. We use `import <name> from <file or package>` to import in ES6

**Importing Named Exports**<br />
We import `Named Exports` using curly braces

```js
import { num1, num2, array, obj, add } from './exports';
```

Also, when we are importing a JavaScript file, Create-React-App will automatically look for the extension. So there is no need to add it.

**Importing Default Exports**<br />
We Import `Default Exports` by giving a name of our choosing for the default export and then importing it from the file.

```js
// this will import the default variable from the file
import Subtraction from './imports';
```

**Aliases**<br />
We also have the ability to create aliases on Named Exports.

```js
import { num1 as myNumber1, num2 as myNumber2 } from './exports';
```

Go to [Exports](./exports-cheatsheet.md) to see how to export.

### LINKS

1. [Learning Objectives, (no answers)](./learning-objectives-empty.md)
2. [Learning Objectives With Answers](./learning-objectives-filled.md)
3. [Imports CheatSheet](./imports-cheatsheet.md)
4. [Exports CheatSheet](./exports-cheatsheet.md)
5. [Imports, Exports One-to-One](./import-export-glance.md)
