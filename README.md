# bun compile bug reproduction

Bug reproduction repo for https://github.com/oven-sh/bun/issues/6113

Project created with `bun init`.

```
bun --revision
1.0.4+a0081f9e29e72ae800373b536e03fe1d729c68ae

# Runs fine
bun index.ts

# Compiles fine
bun build --compile index.ts

# Error when running executable
./index
```

STDERR:
```
 5 | var __hasOwnProp = Object.prototype.hasOwnProperty;
 6 | var __toESM = (mod, isNodeMode, target) => {
 7 |   target = mod != null ? __create(__getProtoOf(mod)) : {};
 8 |   const to = isNodeMode || !mod || !mod.__esModule ? __defProp(target, "default", { value: mod, enumerable: true }) : target;
 9 |
10 |   for (let key of __getOwnPropNames(mod))
                     ^
TypeError: undefined is not an object (evaluating '__getOwnPropNames(mod)')
      at __toESM (compiled://root/index:10:18)

```
