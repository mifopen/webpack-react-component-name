## Overview

**webpack-react-component-name** is a Webpack plugin that makes your custom
React components visible within React Dev Tools and accessible by the React
selector logic built into [Reflect](https://reflect.run).

*Note: This branch contains the version of this plugin that is compatible with
Webpack 5. For support for Webpack 4, see version 4.x of this plugin in our 
[Releases](https://github.com/runreflect/webpack-react-component-name/releases) list.*

Normally React component names are minified during compilation.  This plugin
makes these component names available in production bundles by hooking into
Webpack's compilation process, traversing the AST looking for React component
definitions, and updating the emitted source code to populate the 
[displayName](https://reactjs.org/docs/react-component.html#displayname)
property.  This is the property that, when populated, is used by the React Dev
Tools extension to determine the name of a component.

Since we emit a `displayName` property value for each React component definition
(critically, **not** every React component *instance*), using this plugin will
result in a small size increase to your production bundles.

## Installation

1. Install via npm:

```
npm install webpack-react-component-name -save-dev
```

2. Add the plugin to your Webpack configuration:

```
  plugins: [
    new WebpackReactComponentNamePlugin()
  ],
```

## Troubleshooting

As you probably know, there is more than one way to define a React component.  This
plugin attempts to detect every possible way of defining a component, but there may
be some we've missed.  See the `/examples` directory and the unit tests for examples
of the different permutations of React component definitions that we currently support.

If we are not detecting one of your components, please either file an Issue containing
example source for a component which is not detected, or feel free to open a PR with
the fix.

## License

This project is licensed under the terms of the MIT license.
