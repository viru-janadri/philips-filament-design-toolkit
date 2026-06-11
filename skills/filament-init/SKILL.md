---
name: filament-init
description: "Scaffold a new React project with Philips Filament Design System. Sets up .npmrc, webpack loader, theme provider, and installs core packages. TRIGGERS: 'set up filament', 'init filament', 'new filament project', 'add filament to this project', 'scaffold filament'."
---

# Filament Project Initializer

You scaffold the Philips Filament Design System into a React project. This covers everything a developer needs to go from zero to rendering Filament components.

## Workflow

### Step 1: Detect project state

Check what already exists:
- Does `package.json` exist? (if not, this isn't a JS project — ask)
- Does `.npmrc` already have `@filament` scopes?
- Does webpack config already reference `@filament/react-webpack-loader`?
- Is `@filament/react` already in dependencies?

Report what's missing and proceed only with what's needed.

### Step 2: Set up `.npmrc`

Add these scoped registries (don't duplicate if they exist):

```ini
@filament:registry=https://artifactory.hsdp.io/artifactory/api/npm/filament-npm/
@filament-icons:registry=https://artifactory.hsdp.io/artifactory/api/npm/filament-npm/
@filament-react:registry=https://artifactory.hsdp.io/artifactory/api/npm/filament-npm/
@filament-theme:registry=https://artifactory.hsdp.io/artifactory/api/npm/filament-npm/
always-auth=true
```

Remind the user: for local installs they need `HSDP_TOKEN` env var set. Add a comment line:
```ini
#//artifactory.hsdp.io/artifactory/api/npm/filament-npm/:_authToken=${HSDP_TOKEN}
```

### Step 3: Install packages

Run the appropriate install command based on the project's package manager:

```bash
# yarn (if yarn.lock exists)
yarn add @filament/react @filament-icons/react
yarn add -D @filament/react-webpack-loader @vanilla-extract/webpack-plugin

# npm (if package-lock.json exists)
npm install @filament/react @filament-icons/react
npm install -D @filament/react-webpack-loader @vanilla-extract/webpack-plugin
```

### Step 4: Configure webpack

Find the webpack config (common locations: `webpack.config.js`, `configs/webpack/*.js`).

Add the Filament webpack loader:

```js
const { VanillaExtractPlugin } = require('@vanilla-extract/webpack-plugin');
const filamentLoader = require('@filament/react-webpack-loader');

module.exports = {
  plugins: [
    new VanillaExtractPlugin(),
    // ...existing plugins
  ],
  module: {
    rules: [
      filamentLoader(),
      // ...existing rules
    ],
  },
};
```

If the project uses a webpack-merge pattern (like ix-sdc-simulator), add to the common config.

### Step 5: Set up theme provider

Create or update the app's root component to include the Filament theme:

```tsx
import { Portal } from '@filament/react';
import { base } from '@filament/react/styles';
import { blue, light, medium } from '@filament/react/themes';

function App() {
  return (
    <Portal themes={[base, blue, light, medium]}>
      {/* app content */}
    </Portal>
  );
}
```

### Step 6: Verify setup

Run the build to confirm everything resolves:
```bash
# yarn
yarn build

# npm
npm run build
```

If there are errors, check:
- Auth token is set (`HSDP_TOKEN`)
- Webpack loader version matches Filament version
- `@vanilla-extract/webpack-plugin` is compatible with the webpack version

## Output

Report what was done:
```
## Filament Setup Complete

- [x] .npmrc configured with HSDP Artifactory registries
- [x] Installed @filament/react, @filament-icons/react
- [x] Installed @filament/react-webpack-loader, @vanilla-extract/webpack-plugin
- [x] Webpack configured with Filament loader + VanillaExtract plugin
- [x] Theme provider added to app root
- [ ] Build verified (run `yarn build` / `npm run build`)

Next: use `/filament-ui` to map a design, or `/filament-lookup` to explore components.
```
