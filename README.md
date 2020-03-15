# Deno NPM Demo

## What is this?

This demo shows how it's possible to use NPM packages (ones with an ES module build) with the [Deno](https://deno.land/) JavaScript runtime. You can find ESM packages to try with Deno on [Pika](https://www.pika.dev/).

In the demo, a [Preact](https://preactjs.com/) element tree is rendered to a string and logged to the console. [HTM](https://github.com/developit/htm) is used rather than JSX to avoid the need for a transpilation step.

## How do I try it?

1. Install dependencies with NPM:

   ```sh
   pnpm install
   ```

2. Run the demo with Deno:

   ```sh
   deno --importmap=import-map.json index.js
   ```

## Does this work with [my favourite package]?

Probably not - this only works with packages that can both be built as pure ES modules, and that don't require the use of any Node-specific or web-specific JavaScript APIs. Supporting the larger Node.js ecosystem would be a more ambitious project, as Deno doesn't support CommonJS imports (i.e. `require`), and a compatibility layer would need to be created to support other Node-specific APIs.

Things which likely **will** work:

- Packages that can run in both the browser and the server, e.g. Preact
- Packages that don't rely on Node-specific APIs (e.g. fs, crypto)
- Utility libraries, e.g. Lodash

Things that **won't** work:

- Packages that rely on Node-specific or web-specific APIs
- Packages that rely on native extensions
- Packages that rely on the the Node.js module system (`require`, `module` etc)
