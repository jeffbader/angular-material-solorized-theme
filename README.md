# angular-material-solorized-theme

An angular-material custom theme based on the solorized color panel.

## Dependencies

This custom theme can be used for Angular applications which are using the [angular-material](https://material.angular.io/) components.

## Usage

Get a copy of the *angular-material-solorized.scss* from this repository and add it to your angular application project. (Sorry this theme is not available via any package managers.)

import *angular-material-solorized.scss* into your application styles.scss file.

```
// styles.scss
@import 'angular-material-solorized';
```

### Try the default themes via a CSS class on the document body

*angular-material-solorized.scss* provides default light and dark default themes under the .solorized-dark and .solorized-light CSS selector classes.  If you want to try one of these default themes simply add the appropriate CSS class to your body tag.

```
// index.html
<body class="mat-app-background solorized-light">
...
</body>
```
or 
```
// index.html
<body class="mat-app-background solorized-dark">
...
</body>
```

### Try the default themes via styles.scss

If you don't want to add the solorized theme classes your document body, you can apply the solorized themes via your styles.scss file:

```
// styles.scss
@import 'angular-material-solorized';

// for the default solorized light theme
@include solorized-material-theme($default-solorized-light-theme);

// or, for the default solorized dark theme
@include solorized-material-theme($default-solorized-dark-theme);

// NOTE: The @include statements will set the default theme for your application.  Use one, or 
// the other, but not both.

```

### Create a custom solorized theme.

The angular-material library components can be customized with primary, accent, and warning colors.  The [material design specification](https://material.io/archive/guidelines/style/color.html#color-color-palette) defines a number of standard color palettes that can be used to specify the primary, accent and warning colors.  By default all angular-material styles are based on a common set of foreground and background colors based off the mat-grey color palette.

The *angular-material-solorized.scss* file defines additional color palettes based on the 8 solorized accent colors.  Each of  these palettes is named, based on the solorized accent color. So for example, the *$solorized-blue* palette is based on the solorized *blue* color.

You can combine one or more of the $solorized-xxx color palettes with the base solorized foreground and background colors to create a custom solorized theme.

```
// styles.scss
@import 'angular-material-solorized';

// define the primary, accent, and warning pallets using a combination of the solorized accent palettes.

$app-primary: mat-palette($solorized-blue);
$app-accent:  mat-palette($solorized-blue, 900);
$app-warn:    mat-palette($solorized-red);

// generate light and/or dark themes for the app, based on your primary, accent
// and warning pallets.  All custom solorized themes will be based on the solorized forground and
// background colors.

$app-light-theme: solorized-light-theme($app-primary, $app-accent, $app-warn);
$app-dark-theme: solorized-dark-theme($app-primary, $app-accent, $app-warn);

// apply the theme to the angular-material components...

@include solorized-material-theme($app-light-theme);

// if you want to include both light and dark custom app themes, wrap one or both of your app 
// themes in a CSS selecor

.app-solorized-dark {
  // the dark theme will only be applied to elements with the class "app-solorized-dark"
  @include solorized-material-theme($app-dark-theme);
}

```
