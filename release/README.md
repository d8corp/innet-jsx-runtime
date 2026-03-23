<a href="https://www.npmjs.com/package/innet">
  <img src="https://raw.githubusercontent.com/d8corp/innet/main/logo.svg" align="left" width="90" height="90" alt="InnetJs logo by Mikhail Lysikov">
</a>

# @innet/jsx-runtime

&nbsp;

[![NPM](https://img.shields.io/npm/v/@innet/jsx-runtime.svg)](https://www.npmjs.com/package/@innet/jsx-runtime)
[![npm downloads](https://img.shields.io/npm/dm/@innet/jsx-runtime.svg)](https://www.npmtrends.com/@innet/jsx-runtime)
[![install size](https://packagephobia.com/badge?p=@innet/jsx-runtime)](https://github.com/d8corp/innet-jsx-runtime/tree/main/release)
[![TypeScript](https://img.shields.io/npm/types/@innet/jsx-runtime)](https://www.typescriptlang.org)
[![license](https://img.shields.io/npm/l/@innet/jsx-runtime)](https://github.com/d8corp/innet-jsx-runtime/blob/main/LICENSE)
[![changelog](https://img.shields.io/badge/Changelog-⋮-brightgreen)](https://github.com/d8corp/innet-jsx-runtime/blob/main/CHANGELOG.md)

`@innet/jsx-runtime` is a package that enables **React-style JSX syntax** for the [Innet](https://www.npmjs.com/package/innet) framework.

Use it to write JSX/TSX in your Innet applications without manual transpilation.

Born as part of the [@innet](https://www.npmjs.com/search?q=%40innet) ecosystem.

[![stars](https://img.shields.io/github/stars/d8corp/innet-jsx-runtime?style=social)](https://github.com/d8corp/innet-jsx-runtime/stargazers)
[![watchers](https://img.shields.io/github/watchers/d8corp/innet-jsx-runtime?style=social)](https://github.com/d8corp/innet-jsx-runtime/watchers)

## Index

<sup>**[ [Install](#install) ]**</sup>  
<sup>**[ [Usage](#usage) ]** [TypeScript Setup](#typescript-setup) • [Runtime Exports](#runtime-exports) • [Example](#example)</sup>  

## Install
###### [🏠︎](#index) / Install [↓](#usage)

npm
```shell
npm i -D @innet/jsx-runtime
```

## Usage
###### [🏠︎](#index) / Usage [↑](#install)

<sup>[TypeScript Setup](#typescript-setup) • [Runtime Exports](#runtime-exports) • [Example](#example)</sup>

The library provides JSX runtime functions that transform JSX syntax into JavaScript function calls.
When you write JSX in your TypeScript/JavaScript files, the compiler transforms it using these runtime functions.

### TypeScript Setup
###### [🏠︎](#index) / [Usage](#usage) / TypeScript Setup [↓](#runtime-exports)

Configure your `tsconfig.json` to use `@innet/jsx-runtime` as the JSX import source:

#### react-jsx (Recommended)
```json
{
  "compilerOptions": {
    "jsx": "react-jsx",
    "jsxImportSource": "@innet/jsx-runtime"
  }
}
```

#### react-jsxdev (Development with debug info)
```json
{
  "compilerOptions": {
    "jsx": "react-jsxdev",
    "jsxImportSource": "@innet/jsx-runtime"
  }
}
```

### Runtime Exports
###### [🏠︎](#index) / [Usage](#usage) / Runtime Exports [↑](#typescript-setup) [↓](#example)

The package provides two runtime modules:

**jsx-runtime** — Production runtime
```javascript
import { jsx, jsxs, Fragment } from '@innet/jsx-runtime/jsx-runtime'
```

**jsx-dev-runtime** — Development runtime with enhanced debugging
```javascript
import { jsxDEV, Fragment } from '@innet/jsx-runtime/jsx-dev-runtime'
```

### Example
###### [🏠︎](#index) / [Usage](#usage) / Example [↑](#runtime-exports)

Write JSX in your Innet application:

```tsx
// App.tsx
import { State } from 'watch-state'

function Counter() {
  const count = new State(0)
  
  return (
    <button onclick={() => count.value++}>
      Count: {count}
    </button>
  )
}
```

The TypeScript compiler transforms it to:

```javascript
// App.js (compiled)
import { jsx } from '@innet/jsx-runtime/jsx-runtime'
import { State } from 'watch-state'

function Counter() {
  const count = new State(0)
  
  return jsx('button', {
    onClick: () => count.value++,
    children: ['Count: ', count]
  })
}
```

## Links
You can find more packages in the [@innet ecosystem](https://www.npmjs.com/search?q=%40innet)

- [innet](https://www.npmjs.com/package/innet) — Core engine
- [@innet/jsx](https://www.npmjs.com/package/@innet/jsx) — JSX plugin system
- [@innet/dom](https://www.npmjs.com/package/@innet/dom) — Client-side framework
- [@innet/server](https://www.npmjs.com/package/@innet/server) — Server-side framework
- [innet-jsx](https://www.npmjs.com/package/innet-jsx) — JSX to JS transpiler

## Issues
If you find a bug or have a suggestion, please file an issue on [GitHub](https://github.com/d8corp/innet-jsx-runtime/issues)

[![issues](https://img.shields.io/github/issues-raw/d8corp/innet-jsx-runtime)](https://github.com/d8corp/innet-jsx-runtime/issues)
