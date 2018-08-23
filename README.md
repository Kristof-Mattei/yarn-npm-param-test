Small node project to show `yarn`'s superiority in running scripts to avoid duplication of scripts. 

When you run `yarn via_yarn` you can see that `yarn` passes on the parameters of the `via_yarn` script to the script it actually calls, which allows for easy composing.

The `npm run via_npm` does not do such a thing. 

A larger example would be:

```sh
    "build-css": "node-sass-chokidar --include-path ./src --include-path ./node_modules src/ -o src/",
    "watch-css": "yarn build-css --follow --watch --recursive",
```

In this case we can how we deduplicate the commands to `node-sass-chokidar` when we use `yarn``.

With `npm` we have to do this:


```sh
    "build-css": "node-sass-chokidar --include-path ./src --include-path ./node_modules src/ -o src/",
    "watch-css": "npm run build-css && node-sass-chokidar --include-path ./src --include-path ./node_modules src/ -o src/ --follow --watch --recursive",
```

or you could start writing addititonal scripts, which then complicate cross platform development. 