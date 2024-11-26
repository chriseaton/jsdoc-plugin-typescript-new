[![NPM](https://img.shields.io/npm/v/jsdoc-plugin-typescript-new)](https://npmjs.org/package/jsdoc-plugin-typescript-new)

> [!TIP]
> **Why hasn't this repo been updated in X months or years?!**    
> A: Because it has no dependencies, and it still works.

# JSDoc TypeScript New Plugin
Converts TypeScript "new" method types (`new()`, `new() => X`) to a JSDoc-compatible `instanceOf(X)` type.

Specifically, this creates a compatibility between Visual Studio Code's TypeScript documentation and JSDoc, as
Visual Studio Code's parser uses the `new()` function type to indicate a new instance of a type, but doesn't understand
JSDoc's `instanceOf()` (and vice-versa). 

> You may find my other JSDoc plugins interesting:
>  - [jsdoc-plugin-intersection](https://github.com/chriseaton/jsdoc-plugin-intersection)

## Solving the Problem
Using JSDoc in Visual Studio code with their TypeScript-oriented new typedef:
```js
/**
 * This is my favorite constructor-like generic function.
 * @template T
 * @typedef {new(...args: Array) => T} Constructor
 **/
```
Results in...

> ERROR: Unable to parse a tag's type expression for source file ...: Invalid type expression "new(...)": Expected "!", "=", "?", "[]", "|", or end of input but "(" found. 

Uh oh! JSDoc doesn't like this. It's a TypeScript thing and isn't meant to be supported by JSDoc!

## Resolution
Thankfully, this JSDoc plugin solves the problem by converting your new statements into new JSDoc-compatible function tags.

### Just Install
```sh
yarn add jsdoc-plugin-typescript-new --dev
```
*or*
```sh
npm install jsdoc-plugin-typescript-new --save-dev
```

Update your JSDoc configuration, and include the plugin:
```json
...
    "plugins": [
        "jsdoc-plugin-typescript-new"
    ],
...
```

That's all! 
