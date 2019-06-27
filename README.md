# nuxt-edge @2.9.0-26026572.fc5502cd breaks css-loader

This is a simple repository to reproduce nuxt-edge css-loader build bug
Tested on windows WSL and docker running Linux Alpine.

# steps to reproduce

## working command

```
git checkout master
yarn // install deps
yarn run build // build with no error
```

## Problematic command

```
git checkout master nuxt-edge-2.9.0-26026572.fc5502cd
yarn // install deps
yarn run build // build spits out errors
```

This generate the following errors:

```
ERROR in ./pages/index.vue?vue&type=style&index=0&id=f6a825ce&lang=scss&scoped=true& (./node_modules/css-loader/dist/cjs.js??ref--9-oneOf-1-1!./node_modules/@nuxt/webpack-edge/node_modules/vue-loader/lib/loaders/stylePostLoader.js!./node_modules/postcss-loader/src??ref--9-oneOf-1-2!./node_modules/sass-loader/lib/loader.js??ref--9-oneOf-1-3!./node_modules/vue-loader/lib??vue-loader-options!./pages/index.vue?vue&type=style&index=0&id=f6a825ce&lang=scss&scoped=true&)
Module build failed (from ./node_modules/css-loader/dist/cjs.js):
ValidationError: CSS Loader Invalid Options

options should NOT have additional properties

    at validateOptions (/dev/nuxt-css-loader-failure/node_modules/schema-utils/src/validateOptions.js:32:11)
    at Object.loader (/dev/nuxt-css-loader-failure/node_modules/css-loader/dist/index.js:44:28)
 @ ./pages/index.vue?vue&type=style&index=0&id=f6a825ce&lang=scss&scoped=true& (./node_modules/vue-style-loader??ref--9-oneOf-1-0!./node_modules/css-loader/dist/cjs.js??ref--9-oneOf-1-1!./node_modules/@nuxt/webpack-edge/node_modules/vue-loader/lib/loaders/stylePostLoader.js!./node_modules/postcss-loader/src??ref--9-oneOf-1-2!./node_modules/sass-loader/lib/loader.js??ref--9-oneOf-1-3!./node_modules/vue-loader/lib??vue-loader-options!./pages/index.vue?vue&type=style&index=0&id=f6a825ce&lang=scss&scoped=true&) 4:14-425
 @ ./pages/index.vue?vue&type=style&index=0&id=f6a825ce&lang=scss&scoped=true&
 @ ./pages/index.vue
 @ ./.nuxt/router.js
 @ ./.nuxt/index.js
 @ ./.nuxt/client.js
 @ multi ./.nuxt/client.js
```
