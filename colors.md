# Colors

## Color naming

Colors should be named as follows:
```
[type]-[role]-[prominence]-[interaction]
```

Types:
- bg
- text
- border

Roles:
- brand
- neutral
- error
- warning
- success

Prominences:
- primary
- secondary
- tertiary
- emphasis

Interactions:
- hover
- focus
- pressed

## Example tailwind theme

```js
const colors = require('tailwindcss/colors')

const globalColors = {
  main: colors.cyan,
  auxiliary: colors.teal,
  neutral: colors.slate,
  error: colors.red,
  success: colors.green,
  warning: colors.amber,
}

module.exports = {
  colors: globalColors,
  backgroundColor: {
    "main-primary": globalColors.main[600],
    "main-primary-hover": globalColors.main[500],
    "main-tertiary": globalColors.main[300],
    "neutral-primary": globalColors.neutral[50],
    "neutral-primary-hover": globalColors.neutral[100],
  },
  borderColor: {
    "brand-primary": globalColors.main[400],
  },
  textColor: {
    "neutral-primary": globalColors.neutral[800],
    "neutral-emphasis": globalColors.neutral[900],
    "neutral-muted": globalColors.neutral[400],
    "main-onprimary": colors.white,
  },
  ringColor: {
    "main-primary": globalColors.main[600],
  }
};

```

## References

https://www.subframe.com/blog/how-to-setup-semantic-tailwind-colors
