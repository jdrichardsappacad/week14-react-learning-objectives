# EXPORTS/IMPORTS ONE-TO-ONE AT A GLANCE

**Named Export | Named Import**

```js
export const num = 12;
import { num } from '...';
```

**Default Export | Default Import**

```js
export default myFunc
import youMakeUpName from '...'
```

**Renamed Export | Named Import**

```js
export { person as newPerson }
import { newPerson }
```

**Named + Default | Import All**

```js
export const num = 22;
export default myFunc;
import * as anyName from '...';

console.log(anyName.num, anyName.myFunc());
```

**Export List + Renamed | Import List + Renamed**

```js
export { num1, num2 as newNum2 };
import { num1 as newNum1, newNum2 } from '...';
```

### LINKS

1. [Learning Objectives, (no answers)](./learning-objectives-empty.md)
2. [Learning Objectives With Answers](./learning-objectives-filled.md)
3. [Imports CheatSheet](./imports-cheatsheet.md)
4. [Exports CheatSheet](./exports-cheatsheet.md)
5. [Imports, Exports One-to-One](./import-export-glance.md)
