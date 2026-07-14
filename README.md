# scss-bem

[![NPM](https://img.shields.io/npm/v/@bbt/bem.svg)](https://www.npmjs.com/package/@bbt/bem)

Utility SCSS (sass) helpers to build strict [BEM](https://getbem.com/) selectors.

## Installation and usage

```bash
npm install --save-dev @bbt/bem
```

Usage in your stylesheets:

```scss
@use '@bbt/bem';

.my-block {
  // block styles

  @include element('my-element') {
    // element styles

    @include modifier('my-modifier') {
      // modifier styles
    }
  }

  @include modifier('my-block-modifier') {
    // block modifier styles

    @include element('my-element') {
      // block modifier element styles

      @include modifier('my-modifier') {
        // block modifier element modifier styles
      }
    }
  }
}
```

Produces CSS like:

```scss
.my-block {
  // block styles
}

.my-block .my-block__element {
  // element styles
}

.my-block .my-block__element.my-block__element--my-modifier {
  // modifier styles
}

.my-block.my-block--my-block-modifier {
  // block modifier styles
}

.my-block.my-block--my-block-modifier .my-block__my-element {
  // block modifier element styles
}

.my-block.my-block--my-block-modifier
.my-block__my-element.my-block__my-element--my-modifier {
  // block modifier element modifier styles
}
```
