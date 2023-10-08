# vue3-class-component-demo-webpack

This is a demo project of [vue3-class-component], using [vue-cli] with [webpack]
template.

The following steps will guide you through the project creation process.

1.  Create a Vue3 project using [vue-cli] with [webpack] template.
    ```shell
    vue create vue3-class-component-demo-webpack
    ```
2.  Upgrade yarn to modern version
    ```shell
    cd vue3-class-component-demo-webpack
    corepack enable
    yarn set version stable
    ```
    Add the following content to `.yarnrc.yml`:
    ```
    nodeLinker: pnpm
    ```
    Add the following content to `.gitignore`:
    ```
    # yarn 2.x
    .pnp.*
    .yarn/*
    !.yarn/patches
    !.yarn/plugins
    !.yarn/releases
    !.yarn/sdks
    !.yarn/versions
    ```
3.  Upgrade dependencies
    ```shell
    yarn up vue core-js @babel/core
    ```

4.  Add required dependencies
    ```shell
    yarn add @haixing_hu/vue3-class-component
    yarn add --dev @babel/runtime
    yarn add --dev @babel/preset-env
    yarn add --dev @babel/plugin-proposal-decorators
    yarn add --dev @babel/plugin-transform-class-properties
    yarn add --dev @babel/plugin-transform-runtime
    ```

5.  Edit `babel.config.js` to modify its content as follows:
    ```javascript
    module.exports = {
      presets: [
        "@babel/preset-env",    // NOTE: here we must use "@babel/preset-env"
      ],
      plugins: [
        "@babel/plugin-transform-runtime",
        ["@babel/plugin-proposal-decorators", { "version": "2023-05" }],
        "@babel/plugin-transform-class-properties",
      ],
    }
    ```

6.  Edit `src/components/HelloWorld.vue` to modify its `<script>` content as follows:
    ```javascript
    import { Component, Prop, toVue } from '@haixing_hu/vue3-class-component';

    @Component
    class HelloWorld {
      @Prop
      msg = ''
    }

    export default toVue(HelloWorld);
    ```

6.  Edit `src/App.vue` to modify its `<script>` content as follows:
    ```javascript
    import { Component, toVue } from '@haixing_hu/vue3-class-component';
    import HelloWorld from './components/HelloWorld.vue';

    @Component({
      components: {
        HelloWorld,
      },
    })
    class App {
      // empty
    }

    export default toVue(App);
    ```

8.  Run the dev-server
    ```shell
    yarn serve
    ```

[vue3-class-component]: https://github.com/Haixing-Hu/vue3-class-component
[vue-cli]: https://cli.vuejs.org/
[webpack]: https://webpack.js.org/