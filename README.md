# D I G X

Dig values out of nested objects.

## Installation

`npm install digx --save`

or 

`yarn add digx`

## Usage

Digging values from deeply nested objects

```javascript
import dg from "digx";
const source = { param: [{}, { test: "A" }] };

dg(source, "param[1].test") //=> A
```

Sets and Maps also work in the similar manner.

```javascript
const source = new Map([
  ["param", new Set()],
  ["innerSet", new Set([new Map(), new Map([["innerKey", "value"]])])],
]);

dg(source, "innerSet[1].innerKey"); //=> value
```

When path is incorrect it returns `undefined`

```javascript
dg({ param: [] }, "param[1].test") //=> undefined
```

Or it can thrown an exception when optional `shouldThrow` parameter is set to true

```javascript
dg({ param: [] }, "param[1].test", true) //=> ! Could not dig the value using path
```
