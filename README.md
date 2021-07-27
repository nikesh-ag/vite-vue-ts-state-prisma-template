# Vue 3 + Typescript + Vite

This template should help get you started developing with Vue 3 and Typescript in Vite.

---

# Vue Router

Vue Router is used to declare routes for the app. The routes are defined in the `router.ts` file in the root of the app directory.

### Installing

To install Vue Router, run the following commands:

```bash
npm install vue-router@4 --save
```

Add the `router.ts` file in the `src` directory and copy the code as given to initialize the router.
In `App.vue`, add the `<router-view></router-view>` component as a placeholder for Vue Router to place the app routes.

In the `main.ts` file, import the `router` from the `router.ts` file and add it as a plugin to the vue app as follows:

```ts
createApp(App).use(router).mount('#app)
```

It is also recommended to create a folder `views` in the `src` folder to contain the page views of the app, separate from the `components` folder which contains the components used in the views.

### Uninstalling

To remove the Vue Router, run the following commands:

```bash
npm uninstall vue-router@4 --save
```

In addition, clear the `router.ts` file and the `views` folder in `src`. Remove the `router` imported in the `main.ts` file and remove the plugin use in the create app statement. Finally, remove the `<router-view></router-view>` component from the `App.vue` file.

---

# Vuex Store

Vuex is used for **State Management**. The state store is defined in the `store` folder. It can be defined either in a `index.ts` file or in separate module files.

### Installing

To install Vuex, run the following commands:

```bash
npm install vuex@latest --save
```

Then add a folder `store` in the `src` directory for the Vuex store.

### Uninstalling

To remove the Vuex store, run the following commands:

```bash
npm uninstall vuex@latest --save
```

In addition, remove the `store` folder to clear out the store definition files.

---

# Tailwind CSS

### Installing

The starter template uses TailwindCSS for styling. It also enables Just in Time mode of Tailwind and has some plugins activated by default.

Install tailwindcss and its dependencies

```bash
npm install tailwindcss postcss autoprefixer --save-dev
npx tailwindcss init
```

In the `tailwind.config.js` file that is auto generated, add the first property as follows to enable JIT mode:

```js
module.exports = {
  mode: "jit",
  // ....
};
```

Create an `index.css` file in the `src` directory to initialize the tailwind classes. Add the following code to it:

```css
@tailwindcss /base;
@tailwindcss /components;
@tailwindcss /utilities;
```

Change the `main.ts` file to include the following import: `import "./index.css";`

To install the tailwind plugins:

```bash
npm install @tailwindcss/forms @tailwindcss/typography @tailwindcss/line-clamp @tailwindcss/aspect-ratio --save-dev
```

Add the plugins to the `tailwind.config.js` file:

```js
module.exports = {
  // ....
  plugins: [
    require("@tailwindcss/aspect-ratio"),
    require("@tailwindcss/line-clamp"),
    require("@tailwindcss/typography"),
    require("@tailwindcss/forms"),
  ],
};
```

### Uninstalling

To uninstall tailwindcss and its plugins from the project:

```bash
npm uninstall tailwindcss postcss autoprefixer
npm uninstall @tailwindcss/forms @tailwindcss/typography @tailwindcss/line-clamp @tailwindcss/aspect-ratio
```

Remove the `index.css` and the `tailwind.config.js` files from the `src` and root directories respectively.

In `main.ts` file, remove the `import "./index.css"` line.

# Supabase

### Installing

Create an account on Supabase.io and Create a new Database.

Install the supabase client library:

```bash
npm install @supabase/supabase-js --save
```

Create a `supabase.ts` file in the `src` folder and add the following:

```ts
import { createClient } from "@supabase/supabase-js";

const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseAnonKey = import.meta.env.VITE_SUPABASE_ANON_KEY;

export const supabase = createClient(supabaseUrl, supabaseAnonKey);
```

Add the `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY` variables to the `.env` file. Get these values from Settings -> API in the Supabase account.

### Uninstalling

To uninstall Supabase from the project:

```bash
npm uninstall @supabase/supabase-js
```

Remove the `supabase.ts` file from the `src` directory.

Remove the `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY` variables from the `.env` file.

If required, delete the Database created in your Supabase account.

# Prisma

### Installing

To install, run the following:

```bash
npm install prisma --save-dev
npx prisma init
```

This will generate a `prisma` folder with the base schema file in the root directory.

In the `.env` file generated in the root directory, add the `DATABASE_URL` variable based on the location of the database server. In case, using supabase, this will be the supabase database connection link.

### Uninstalling

To uninstall Prisma from the project, run the following:

```bash
npm uninstall prisma
```

Remove the `DATABASE_URL` variable from the `.env` file or if not required, you can remove the entire `.env` file.

Remove the `prisma` folder from the root directory.

# XState

### Installing

To add XState to the project:

```bash
npm install xstate @xstate/vue
```

Create a fodler `machines` in the `src` directory to hold all the state machine definitions.

### Uninstalling

To uninstall XState from the project:

```bash
npm uninstall xstate @xstate/vue
```

Remove the `machines` folder from the `src` directory.

# Unit Testing (Jest + Testing Library)

### Installing

```bash
npm install jest @types/jest ts-jest vue-jest@next @testing-library/vue@next --save-dev

// Initialize Jest Config
npx jest --init
// OR
./node_modules/.bin/jest --init
```

Make 2 changes in the generated Jest Config

```js
// jest.config.js
module.exports = {
  moduleFileExtensions: ["js", "ts", "json", "vue"],
  transform: {
    "^.+\\.ts$": "ts-jest",
    "^.+\\.vue$": "vue-jest",
  },
};
```

Modify tsconfig.json to add the types

```json
// tsconfig.json
{
  "compilerOptions": {
    ...
    "types": ["vite/client", "@types/jest"],
    ...
  },
  ...
}
```

Add the script to run the jest runner to test

```json
// package.json
{
  ...
  "scripts": {
    ...
    "test:unit": "./node_modules/.bin/jest tests/unit"
  },
  ...
}
```

Create the test folder in the root directory as `tests/unit`

### Uninstalling

```bash
npm uninstall jest @types/jest ts-jest vue-jest@next @testing-library/vue@next --save-dev
```

Remove the `tests/unit` folder, `jest.config.ts` file.

Remove the types definition `@types/jest` in the `tsconfig.json` file.

Remove the `test:unit` script from the `package.json` file.

# End-to-End Testing (Cypress)

### Installing

```bash
npm install cypress start-server-and-test --save-dev
npx cypress open
```

`start-server-and-test` utility library can start the development server, wait until it responds to the given URL, and then runs the Cypress tests. In the end, it stops all running processes during the cleanup phase.

In the auto-generated cypress.json file, add the following:

```json
{
  "baseUrl": "http://localhost:3000",
  "fixturesFolder": "tests/e2e/fixtures",
  "integrationFolder": "tests/e2e/integration",
  "pluginsFile": "tests/e2e/plugins/index.ts",
  "screenshotsFolder": "tests/e2e/screenshots",
  "supportFile": "tests/e2e/support/index.ts",
  "videosFolder": "tests/e2e/videos"
}
```

Modify tsconfig.json to add the types

```json
// tsconfig.json
{
  "compilerOptions": {
    ...
    "types": [..., "cypress"],
    ...
  },
  ...
}
```

Add the script to run the cypress tests

```json
// package.json
{
  ...
  "scripts": {
    ...
    "test:e2e": "./node_modules/.bin/cypress"
  },
  ...
}
```

Move the `cypress` folder from the root directory into the `tests` folder. Rename it to `e2e`.

### Uninstalling

```bash
npm uninstall cypress start-server-and-test
```

Remove the `cypress.json` file and the `tests/e2e` folder.

Remove the `cypress` type definitions from the `tsconfig.json` file.

Remove the `test:e2e` script from the `package.json` file.

---

# Other Information

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur). Make sure to enable `vetur.experimental.templateInterpolationService` in settings!

### If Using `<script setup>`

[`<script setup>`](https://github.com/vuejs/rfcs/pull/227) is a feature that is currently in RFC stage. To get proper IDE support for the syntax, use [Volar](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar) instead of Vetur (and disable Vetur).

## Type Support For `.vue` Imports in TS

Since TypeScript cannot handle type information for `.vue` imports, they are shimmed to be a generic Vue component type by default. In most cases this is fine if you don't really care about component prop types outside of templates. However, if you wish to get actual prop types in `.vue` imports (for example to get props validation when using manual `h(...)` calls), you can use the following:

### If Using Volar

Run `Volar: Switch TS Plugin on/off` from VSCode command palette.

### If Using Vetur

1. Install and add `@vuedx/typescript-plugin-vue` to the [plugins section](https://www.typescriptlang.org/tsconfig#plugins) in `tsconfig.json`
2. Delete `src/shims-vue.d.ts` as it is no longer needed to provide module info to Typescript
3. Open `src/main.ts` in VSCode
4. Open the VSCode command palette
5. Search and run "Select TypeScript version" -> "Use workspace version"
