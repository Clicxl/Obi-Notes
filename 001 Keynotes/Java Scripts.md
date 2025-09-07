#coding #webdev 
Java script or js is a prototype based programming language used to run the web. It adds interactivity to the plan old [[HTML]] and [[CSS]]. Currently it is also being used to run servers (nodejs, bun), desktop apps (electron, tauri) and mobiles apps (react native) too.

- New day mechanism .js file is first tokenized or parsed into a syntax tree. Then this syntax tree is sent out to the JIT compiler (Just-In-Time Compiler), then this JITC compiles the file into Bytecode (just before machine code) and then to machine code.
- JS datatypes are of 2 types 
  1. Primitive: Strings, Numbers, null, undefined, Boolean, Symbols
  2. Non-Primitive: Objects -> objects (dicts), arrays, functions 
- Prototype Based: Its a alternative to Oops where every method or data that a variable holds it stored in `.__proto__`  and can be passed around to other variables like classes and objects. 
- Setter `set` and Getter `get`: They are special methods that are applied on variable used for accessing and changing values of the variables in a class.
- **BOM** (Browser Object Model): It has access to all the information about the browser like location, protocol name, screen size, and etc.
- Generator function are special functions (`function* <funcName>`) that generate one value when called.
- If not a default import, in js an import is done by `import {<name>,..} from "path/to/file.js`.

### Notes
- `process.stdout.write(<str>)` is also a way of printing out js string to the console.
- `undefined` states that the value exists but its datatype is not defined.
- `null` states that the value DOES NOT exists.
- `symbol` 
- `this` is a reference to the object running the current function or code block.
- A function can take in another function (without the parenthesis) as an argument, but the parameters are passed to it when calling it inside the outer function. `function func1(func2) { func2(paras..) }`, these are called higher order functions or first class function.
- You can even return a function with its full functionality.
- Inner functions explicitly have access to all the local variables of the outer function.
- `Object.getPrototypeOf(<object>)` returns all the prototypes of the passed object that are externally stated.
- `new` this is a keyword that instantiate a new function object or class object.
- `new.target` returns a boolean stating if the object was called with the new keyword or not.
- `static` is a special function that can be called only by the class and nobody else but not by the objects initiated.
- `yield`is a special keyword that reads through a `generator function` and outputs the value.
- `Promise.all([<asyncfunc1>,<asyncfunc2>,..])` Takes in multiple async functions and fetches them at the same time.
- `require("path/to/file.js")` is used to import functions and other stuff via commonJS.