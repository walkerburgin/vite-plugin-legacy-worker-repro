# vite-plugin-legacy-worker-repro

## Repro

- Run `pnpm install` to install dependencies 
- Run `pnpm build && pnpm preview`
- Observe the runtime error when previewing the app in the browser:
  ```
  ReferenceError: Can't find variable: __VITE_IS_LEGACY__
  ```

Alternately:

- Run `pnpm install` to install dependencies
- Run `pnpm build`
- Observe that the worker output file (e.g. `dist/assets/worker-NmsWRLpo.js`) contains a reference to `__VITE_IS_LEGACY__`:
  ```js
  (function() {
      "use strict";
      console.log("[worker] import.meta.env", {
          BASE_URL: "/",
          MODE: "production",
          DEV: !1,
          PROD: !0,
          SSR: !1,
          LEGACY: __VITE_IS_LEGACY__
      })
  })();
  ```
