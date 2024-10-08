# ⚡ Vite plugin for Zalo Mini App

## How to setup?

### 1. Install

```bash
npm i -D zmp-vite-plugin
```

### 2. Update your `vite.config.ts`

```typescript
import { defineConfig, splitVendorChunkPlugin } from "vite";
import react from "@vitejs/plugin-react";
import zaloMiniApp from "zmp-vite-plugin";

export default () => {
  return defineConfig({
    plugins: [
      react(), // If you are using React
      splitVendorChunkPlugin(), // If you want to split vendor chunk to reduce the size of the main bundle
      zaloMiniApp({
        app: {
          title: "Mini App Name",
          headerTitle: "Mini App Name",
          headerColor: "#F25730",
          textColor: "black",
          statusBar: "normal",
          actionBarHidden: true,
          hideAndroidBottomNavigationBar: true,
          hideIOSSafeAreaBottom: true,
        },
      }), // If you want to read configs from app-config.json, pass nothing, i.e., zaloMiniApp()
    ],
  });
};
```

> Because this plugin will automatic generate `app-config.json` for you with the configuration you provided in `vite.config.ts`. So if you have `app-config.json` in your project, you should remove it.

## Run & Deploy

### 1. Install the latest `zmp-cli`

If you don't have `zmp-cli` installed, you can install it by running:

```bash
pnpm add -g zmp-cli
```

### 2. Update your `package.json`

```json
{
  "scripts": {
    "start": "vite dev",
    "build": "tsc && vite build",
    "deploy:dev": "zmp-cli deploy --existing",
    "deploy:testing": "zmp-cli deploy --existing --testing"
  }
}
```

### 3. Run

- 🔥 `pnpm start` to start local development server
- 🚀 `pnpm build` to build your project
- 🚢 `pnpm deploy` to deploy the app in **DEVELOPMENT** mode
- ⚡ `pnpm deploy:testing` to deploy the app in **TESTING** mode
