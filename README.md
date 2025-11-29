**Project Overview**

This is a minimal TypeScript + ES module backend example that demonstrates a small HTTP server (for example using `express`) implemented in TypeScript and organized as ES modules. It shows the basic project layout, how to build the project to plain JavaScript, and how to run it locally.

**Prerequisites**

- **Node**: Recommended Node.js 18 or later.
- **npm**: Comes with Node.js.
- **TypeScript**: Not required globally; we use `npx` in examples.

**Project Structure**

- `package.json`: npm metadata and dependency list.
- `tsconfig.json`: TypeScript compiler configuration (ES module output).
- `src/`:
  - `index.ts`: Example entry point for the server.

**Quick Start (Development)**

Use these PowerShell commands from the project root (`.` is the project folder):

```powershell
# install dependencies
npm install

# run with ts-node (fast dev). If you don't have ts-node installed, use npx:
npx ts-node-esm src/index.ts
```

Notes:
- `npx ts-node-esm` is convenient for TypeScript + ESM development. If `ts-node-esm` is not available in your environment, you can install `ts-node` and use it with ESM config or use a build step below.

**Build & Run (Production / Node runtime)**

Compile TypeScript to JavaScript and run the compiled output with Node:

```powershell
# compile
npx tsc

# run the compiled app (adjust path if your tsconfig outputs to a different folder)
node dist/index.js
```

If `tsconfig.json` outputs to a different directory (for example `build/`), change the `node` path accordingly.

**Test the Server**

Once the server is running (commonly on port `3000` in small examples), test with either `curl` or PowerShell's `Invoke-RestMethod`:

```powershell
# curl (works in modern Windows)
curl http://localhost:3000/

# PowerShell alternative
Invoke-RestMethod http://localhost:3000/
```

**Example package.json scripts**

You can add these scripts to `package.json` for convenience:

```json
"scripts": {
  "build": "tsc",
  "start": "node dist/index.js",
  "dev": "ts-node-esm src/index.ts"
}
```

**Notes & Troubleshooting**

- ESM and TypeScript: When targeting ES modules from TypeScript, ensure `tsconfig.json` sets `module` to an ES module kind (for example `ESNext`) and `moduleResolution` to `node` (or `bundler` depending on toolchain). Also set `"type": "module"` in `package.json` if you intend Node to treat `.js` files as ESM.
- If you see errors about imports or `require`/`exports`, verify the compiled output and `package.json` `type` field.
- If you're using native ESM with TypeScript, prefer `npx ts-node-esm` for development or build with `npx tsc` and run the compiled `.js` files with Node 18+.

**Where to look**

- Entry point: `src/index.ts` — open this file to see the example server code.
- Compiler options: `tsconfig.json` — check `outDir`, `module`, and `target` for runtime compatibility.

Enjoy exploring the example!
