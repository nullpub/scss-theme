# @nll/scss-theme

Some simple scss files that help with setting application wide themes.

## How To Use

This package requires that your build process renders sass. To use:

`npm i -D @nll/scss-theme`

Then import into your root sass style:

```scss
@import '~@nll/scss-theme/theme';
```

### Theme Variables (theme-vars.scss)

Takes a set of sass variables and creates css variables at :root. Can be customized by setting the following:

```scss
$thm-base-color: #111111;
$thm-base-contrast: #f4f4f4;
$thm-light-color: #a463f2;
$thm-light-contrast: #f4f4f4;
$thm-primary-color: #eeeeee;
$thm-primary-contrast: #5e2ca5;
$thm-secondary-color: #eeeeee;
$thm-secondary-contrast: #a463f2;
$thm-accent-color: #555555;
$thm-accent-contrast: #ffb700;
$thm-info-color: #f4f4f4;
$thm-info-contrast: #357edd;
$thm-warning-color: #ff4136;
$thm-warning-contrast: #ffd700;
$thm-error-color: #ff4136;
$thm-error-contrast: #ffdfdf;
```

Use these variables in your application as `fallback` variables, and use the generated css variables too. For example:

```scss
.my-custom-class {
  border-color: $thm-primary-color;
  border-color: var(--thm-primary-color);
}
```

This will allow you to substitute other css variables at runtime to change the theme (rather than loading a complete css file)

### Theme Classes (theme-classes.scss)

Generates simple "functional" theme classes based on the defined theme variables. The classes will use css variables if the browser supports them, but will fall back to the predefined hardcoded scss variables if it doesn't. Theme classes follow the theme variable names:

- .thm-base, .thm-base-color, .thm-base-contrast
- .thm-light, .thm-light-color, .thm-light-contrast
- .thm-primary, .thm-primary-color, .thm-primary-contrast
- .thm-secondary, .thm-secondary-color, .thm-secondary-contrast
- .thm-accent, .thm-accent-color, .thm-accent-contrast
- .thm-info, .thm-info-color, .thm-info-contrast
- .thm-warning, .thm-warning-color, .thm-warning-contrast
- .thm-error, .thm-error-color, .thm-error-contrast

Each class looks like this:

```scss
.thm-base-color {
  color: $thm-base-color; // Fallback Color
  color: var(--thm-base-color);
}
.thm-base-contrast {
  background-color: $thm-base-contrast; // Fallback Color
  background-color: var(--thm-base-contrast);
}
.thm-base {
  @extend .thm-base-color;
  @extend .thm-base-contrast;
}
```
