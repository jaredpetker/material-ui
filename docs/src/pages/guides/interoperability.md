# Interoperability with Style Libraries

This guide aims to help Material UI users to use Style Libraries like Glamorous, Styled-components or CSS Modules.

## React JSS

![stars](https://img.shields.io/github/stars/cssinjs/react-jss.svg?style=social&label=Star)
![npm](https://img.shields.io/npm/dm/react-jss.svg?)

Material-UI's styling solution shares many building blocks with [react-jss](https://github.com/cssinjs/react-jss).
We went ahead and forked the project in order to handle our unique needs, but we're working to merge the changes and fixes from Material-UI back to react-jss.

In the following demo we demonstrate how to use `injectSheet()` and "the styles as a function of the properties" feature:

```js
const styles = theme => ({
 root: {
   color: props => (props.variant === 'primary'
     ? theme.palette.primary[500]
     : 'inherit'),
   textDecoration: 'inherit',
 },
});
```

{{"demo": "pages/guides/ReactJss.js"}}

## Styled Components

![stars](https://img.shields.io/github/stars/styled-components/styled-components.svg?style=social&label=Star)
![npm](https://img.shields.io/npm/dm/styled-components.svg?)

The `styled()` method works perfectly on all of our components.

```jsx
import React from 'react';
import styled from 'styled-components';
import Button from 'material-ui/Button';

const StyledButton = styled(Button)`
  background-color: grey;
  color: pink;
  width: 240px;
`;

function StyledComponentsButton() {
  return (
    <div>
      <Button color="accent" raised>
        Material-UI
      </Button>
      <StyledButton color="accent" raised>
        Styled Components
      </StyledButton>
    </div>
  );
}

export default StyledComponentsButton;
```

[![Edit Button](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/mzwqkk1p7j)

**Note:** Both styled-components and JSS inject their styles at the bottom of the `<head />`. If you don't want to mark style attributes with **!important**, you need to change [the CSS injection order](/customization/css-in-js#css-injection-order) as we do in the demo.

## Glamorous

![stars](https://img.shields.io/github/stars/paypal/glamorous.svg?style=social&label=Star)
![npm](https://img.shields.io/npm/dm/glamorous.svg?)

A clean way to apply styles to Material-UI components with glamorous It's just passing our component as a glamorous param. We are gona take the [raised button example](/demos/buttons/#raised-buttons) from Material-UI documentation and use glamorous to style it:

```jsx
import React from 'react';
import glamorous from 'glamorous';
import Button from 'material-ui/Button';

const StyledButton = glamorous(Button)({
  backgroundColor: 'grey',
  color: 'pink',
  width: 240
});

function GlamorousButton() {
  return (
    <div>
      <Button color="accent" raised>
        Materialized
      </Button>
      <StyledButton color="accent" raised>
        Glamoroused
      </StyledButton>
    </div>
  );
}

export default GlamorousButton:
```

[![Edit Button](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/n3jmn72wrm)

**Note:** Both Glamor and JSS inject their styles at the bottom of the `<head />`. If you don't want to mark style attributes with **!important**, you need to change [the CSS injection order](/customization/css-in-js#css-injection-order) as we do in the demo.

## Glamor

![stars](https://img.shields.io/github/stars/threepointone/glamor.svg?style=social&label=Star)
![npm](https://img.shields.io/npm/dm/glamor.svg?)

A good way to apply styles with Glamor is using the **css()** function and then **classnames** to get them as strings:

```jsx
import React from 'react';
import glamorous from 'glamorous';
import { css } from 'glamor';
import classnames from 'classnames';
import Button from 'material-ui/Button';

const buttonStyles = {
  backgroundColor: 'grey',
  color: 'pink',
  width: 240,
};

// First we get the classNames with Glamor css function
const buttonClasses = css(buttonStyles);

// We need the class names to be strings
const className = buttonClasses.toString();

// Then we just assign them the Button's className attribute
function GlamorButton() {
  return (
    <div>
      <Button color="accent" raised>
        Material-UI
      </Button>
      <Button color="accent" className={className} raised>
        Glamor
      </Button>
    </div>
  );
}

export default GlamorButton;
```

[![Edit Button](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/ov5l1j2j8z)

**Note:** Both Glamor and JSS inject their styles at the bottom of the `<head />`. If you don't want to mark style attributes with **!important**, you need to change [the CSS injection order](/customization/css-in-js#css-injection-order) as we do in the demo.
