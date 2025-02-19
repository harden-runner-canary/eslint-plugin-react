# Enforce defaultProps declarations alphabetical sorting (react/sort-default-props)

💼 This rule is enabled in the following [configs](https://github.com/jsx-eslint/eslint-plugin-react#shareable-configurations): `all`.

Some developers prefer to sort `defaultProps` declarations alphabetically to be able to find necessary declarations easier at a later time. Others feel that it adds complexity and becomes a burden to maintain.

## Rule Details

This rule checks all components and verifies that all `defaultProps` declarations are sorted alphabetically. A spread attribute resets the verification. The default configuration of the rule is case-sensitive.

The following patterns are considered warnings:

```jsx
var Component = createReactClass({
...
  getDefaultProps: function() {
    return {
      z: "z",
      a: "a",
      b: "b"
    };
  },
...
});

class Component extends React.Component {
  ...
}
Component.defaultProps = {
  z: "z",
  a: "a",
  b: "b"
};

class Component extends React.Component {
  static defaultProps = {
    z: "z",
    y: "y",
    a: "a"
  }
  render() {
    return <div />;
  }
}

const Component = (props) => (...);
Component.defaultProps = {
  z: "z",
  y: "y",
  a: "a"
};

const defaults = {
  b: "b"
};
const types = {
  a: PropTypes.string,
  b: PropTypes.string,
  c: PropTypes.string'
};
function StatelessComponentWithSpreadInPropTypes({ a, b, c }) {
  return <div>{a}{b}{c}</div>;
}
StatelessComponentWithSpreadInPropTypes.propTypes = types;
StatelessComponentWithSpreadInPropTypes.defaultProps = {
  c: "c",
  a: "a",
  ...defaults,
};

export default class ClassWithSpreadInPropTypes extends BaseClass {
  static propTypes = {
    a: PropTypes.string,
    b: PropTypes.string,
    c: PropTypes.string,
    d: PropTypes.string,
    e: PropTypes.string,
    f: PropTypes.string
  }
  static defaultProps = {
    b: "b",
    a: "a",
    ...c.defaultProps,
    f: "f",
    e: "e",
    ...d.defaultProps
  }
}
```

The following patterns are considered okay and do **not** cause warnings:

```jsx
var Component = createReactClass({
...
  getDefaultProps: function() {
    return {
      a: "a",
      b: "b",
      c: "c"
    };
  },
...
});

class Component extends React.Component {
  ...
}
Component.defaultProps = {
  a: "a",
  b: "b",
  c: "c"
};

class Component extends React.Component {
  static defaultProps = {
    a: PropTypes.any,
    b: PropTypes.any,
    c: PropTypes.any
  }
  render() {
    return <div />;
  }
}

const Component = (props) => (...);
Component.defaultProps = {
  a: "a",
  y: "y",
  z: "z"
};

const defaults = {
  b: "b"
};
const types = {
  a: PropTypes.string,
  b: PropTypes.string,
  c: PropTypes.string'
};
function StatelessComponentWithSpreadInPropTypes({ a, b, c }) {
  return <div>{a}{b}{c}</div>;
}
StatelessComponentWithSpreadInPropTypes.propTypes = types;
StatelessComponentWithSpreadInPropTypes.defaultProps = {
  a: "a",
  c: "c",
  ...defaults,
};

export default class ClassWithSpreadInPropTypes extends BaseClass {
  static propTypes = {
    a: PropTypes.string,
    b: PropTypes.string,
    c: PropTypes.string,
    d: PropTypes.string,
    e: PropTypes.string,
    f: PropTypes.string
  }
  static defaultProps = {
    a: "a",
    b: "b",
    ...c.defaultProps,
    e: "e",
    f: "f",
    ...d.defaultProps
  }
}
```

## Rule Options

```js
...
"react/sort-default-props": [<enabled>, {
  "ignoreCase": <boolean>,
}]
...
```

### `ignoreCase`

When `true` the rule ignores the case-sensitivity of the declarations order.

## When not to use

This rule is a formatting preference and not following it won't negatively affect the quality of your code. If alphabetizing `defaultProps` declarations isn't a part of your coding standards, then you can leave this rule off.
