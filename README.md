# gatsby-cypress-with-code-coverage

This repository was scaffolded from the official [starter example](https://github.com/gatsbyjs/gatsby-starter-hello-world). Then I have added [babel-plugin-istanbul]() following the [Gatsby Babel documentation](https://github.com/gatsbyjs/gatsby-starter-hello-world)

```
npm i -D babel-preset-gatsby babel-plugin-istanbul
+ babel-preset-gatsby@0.8.0
+ babel-plugin-istanbul@6.0.0
```

The [.babelrc](.babelrc) imports the plugins

```json
{
  "plugins": [
    [
      "babel-plugin-istanbul"
    ]
  ],
  "presets": [
    [
      "babel-preset-gatsby",
      {
        "targets": {
          "browsers": [
            ">0.25%",
            "not dead"
          ]
        }
      }
    ]
  ]
}
```

Immediately you can see the `window.__coverage__` object in the DevTools console

![Coverage object](images/coverage.png)

We do not want `.cache` files in the coverage list, we only want our local `src` files instrumented. We can modify the plugin's settings in `.babelrc` to include only files in the `src` folder.

```json
{
  "plugins": [
    [
      "babel-plugin-istanbul", {
        "include": ["src/**/*.js"]
      }
    ]
  ]
}
```

The `window.__coverage__` object now has a single entry.

![Coverage for src pages only](images/coverage-src.png)
