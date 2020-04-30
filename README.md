# FluidMS

FluidMS offers a font-size system that enables you to use [Modular Scale](https://www.modularscale.com/) in combination with the [Fluid Typography](https://css-tricks.com/snippets/css/fluid-typography/) technique. It also ensures that all your typography always sits on a baseline grid which size you can define.

## Getting Started

### Installing

In order to use FluidMS, first install the package:

```
$ npm install fluidms --save
```

Next, you need to import the Sass files into your project:

```scss
// Your `main.scss` file.

@import "<path-to-fluidms-node-package>/src/fluidms.scss";
```

If you are following an [ITCSS](https://csswizardry.com/2018/11/itcss-and-skillshare/) approach in your project, you might want to import the individual partials of FluidMS instead:

```scss
// Your `main.scss` file.

// Settings
@import "<path-to-fluidms-node-package>/src/settings/settings.config";

// Tools
@import "<path-to-fluidms-node-package>/src/tools/tools.utils";
@import "<path-to-fluidms-node-package>/src/tools/tools.ms";
@import "<path-to-fluidms-node-package>/src/tools/tools.font-size";
@import "<path-to-fluidms-node-package>/src/tools/tools.line-height";

// Generic
@import "<path-to-fluidms-node-package>/src/generic/generic.ms-custom-properties";

// Elements
@import "<path-to-fluidms-node-package>/src/elements/elements.page";

// Objects
...

// Components
...

// Utilities
...
```

### Using

To use FluidMS, you only need to apply the `fluidms-font-size()` mixin to the elements you want to assign font-sizes to:

```scss
.foo {
    @include fluidms-font-size();
}
```

Just calling the mixin without any arguments assigns the base font-size to the element along with a line-height that is calculated to automatically fit into the defined baseline grid.

Let’s see how we can affect the generated font-size of an element:

```scss
.larger-text {
    @include fluidms-font-size(
        $font-size: ms(1)
    );
}
```

Here we are calling the mixin with altering the `$font-size` parameter. For that, we are using the `ms()` function (`ms` stands for “Modular Scale”). What we are doing here is to say: “Assign a font-size here, but set the font-size to the next bigger scale entity than our base font-size (hence **1**).” We could also set the font-size to the next bigger scale entity by passing `$font-size: ms(2)` and so on.

Negative entites are also possible:

```scss
.smaller-text {
    @include fluidms-font-size(
        $font-size: ms(-2)
    );
}
```

Read more about Modular Scale [here](https://alistapart.com/article/more-meaningful-typography/).

#### Custom font-size

Instead of relying on the modular scale for a specific font-size and using the `ms()` function for the `$font-size` parameter, you can also pass a custom font-size:

```scss
.custom-font-size {
    @include fluidms-font-size(
        $font-size: 38px
    );
}
```

Any value that is [valid for the native CSS `font-size` property](https://developer.mozilla.org/en-US/docs/Web/CSS/font-size#Values) is also valid here.

#### Changing the line-height

By default, the line height is automatically calculated so that it fits onto the defined baseline grid. However, if you need to manually assign a custom line-height to an element, you can do so with an additional argument:

```scss
.custom-line-height {
    @include fluidms-font-size(
        $font-size: ms(3),
        $line-height: 50px
    );
}
```

Possible values for the `$line-height` parameter are:

* A number with any unit that’s valid for `line-height` declarations (or unit-less)
* The keyword `inherit`
* The keyword `normal`

You can also completely omit the output of a line-height declaration by setting its value to `false`:

```scss
.no-line-height {
    @include fluidms-font-size(
        $font-size: ms(3),
        $line-height: false
    );
}
```

(`$line-height: none` also works for omitting the output)

##### Increasing/Decreasing the line-height

There may be situations where the generated line-height is not quite what you need, but you still want to benefit from the automatic baseline grid adaptation. So instead of assigning a custom line-height and risking loosing the anchoring to the baseline grid, you can tweak the line-height upwards or downwards and still be on the baseline grid:

```scss
.slightly-smaller-line-height {
    @include fluims-font-size(
        $line-height-modifier: -1
    );
}

.slightly-bigger-line-height {
    @include fluims-font-size(
        $line-height-modifier: 1
    );
}
```

As you can see, we can deviate from the default line-height in integer increments (positive and negative). In theory, every integer is possible here (e.g. `1.000.000`), but mostly you will only tweak the line-height a little bit.

Note that `$line-height-modifier` only has affect when the `$line-height` parameter is set to `auto` (default).

#### `!important`

You will not find any CSS jokes about the usage of `!important` here. The fact is, it may well be that you need an `!important` here and there and actually, it sometimes [can be a pretty good idea](https://csswizardry.com/2016/05/the-importance-of-important/), too.

Anyhow, FluidMS has got you covered for these situations:

```scss
.i-need-important {
    @include fluidms-font-size(
        $font-size: ms(1),
        $important: true
    );
}
```

This outputs the font-size as well as the line-height with a trailing `!important` in the declaration.

## Adjusting

FluidMS comes with predefined configuration settings that you can fit to your needs. You’ll find all the config in the provided `_settings.config.scss` file.

### Changing the baseline grid

FluidMS provides a baseline grid out of the box. That means that every line-height that is automatically generated by FluidMS sits on this vertical grid. You can change the size of that grid by altering the `$FLUIDMS-GLOBAL-BASELINE` variable:

```scss
$FLUIDMS-GLOBAL-BASELINE: 0.25rem !default;
```

`$FLUIDMS-GLOBAL-BASELINE` needs to be defined with a `rem` unit. It has been proven to be a good idea to define a value between `0.1rem` – `0.333rem`.

If your design doesn’t require a global baseline grid, you can also disable it:

```scss
$FLUIDMS-GLOBAL-BASELINE: false !default;
```

### Changing the global line-height

You can define an ideal line-height that is taken into account when calculating the actual line-height. The value you define here is more just a rough direction of what the resulting line-height will be.

```scss
$FLUIDMS-GLOBAL-LINE-HEIGHT: 1.5 !default;
```

### Changing the global line-height ratio

The bigger font-sizes get, the lesser the line-height needs to be in relation to its font-size. Hence, we provide an option to decrease the line-height in proportion to the font-size, the bigger the font-size gets.

```scss
$FLUIDMS-GLOBAL-LINE-HEIGHT-RATIO: 1 !default;
```

Don’t get crazy with this variable’s value! Only nudge the ratio slightly and always test all the possible font-sizes with multiline text.

### Configure the Fluid Typography values

With Fluid Typography, you basically define a viewport range in which all the font-sizes are fluid, i.e. the font-sizes are sized according to the viewport size — if the viewport size is small, the font-size is too. If the viewport size is large, so is the font-size.

#### Defining the viewport range

You can define the range in which the typography is fluid with the `min-viewport` and `max-viewport` entries in the `$FLUIDMS-CONFIG` Sass map:

```scss
$FLUIDMS-CONFIG: (
    min-viewport: 480px,
    max-viewport: 1280px,
) !default;
```

#### Defining the base font-size

This means that on every viewport that’s between `480px` and `1280px` wide, the typography will be fluid. How big the font-size is below and above this range can be defined with the `min-font-size` and `max-font-size` entries in `$FLUIDMS-CONFIG`:

```scss
$FLUIDMS-CONFIG: (
    min-font-size: 16px,
    max-font-size: 24px,
    min-viewport: 480px,
    max-viewport: 1280px,
) !default;
```

Below a viewport of `480px`, the font-size will be `16px` and not smaller. Above a viewport of `1280px` the font-size will be `24px` and not larger. Between these two viewport sizes, the font-size will evenly scale between `16px` and `24px`. However these are just the base values when the default font-size is used. If we assign a larger font-size for an element like this:

```scss
.larger-text {
    @include fluidms-font-size(
        $font-size: ms(1)
    );
}
```

then the minimum and maximum font-size should of course be bigger. How much bigger it is can be defined via the `ratio` entry in the `$FLUIDMS-CONFIG` Sass map:

#### Defining a font-size ratio

```scss
$FLUIDMS-CONFIG: (
    min-font-size: 16px,
    max-font-size: 24px,
    min-viewport: 480px,
    max-viewport: 1280px,
    ratio: 1.1,
) !default;
```

With a ratio of `1.1`, the font-size of the example above will be `17.6px` (`16px * 1.1`) on screens smaller than `480px`. On screens larger than `1280px`, the font-size will be `26.4px` (`24px * 1.1`).

If we use the mixin with `$font-size: ms(2)`, this font-size will be again 1.1x bigger than that one and so on.

#### Changing the ratio at different breakpoints

What seems like a good ratio on small screens might not be suited on larger screens as the different font-sizes are too similar to each other related to the viewport size. In this case you can optionally change the ratio for different breakpoints:

```scss
$FLUIDMS-CONFIG: (
    min-font-size: 16px,
    max-font-size: 24px,
    min-viewport: 480px,
    max-viewport: 1280px,
    ratio: 1.1,
    1024px: (
        ratio: 1.3,
    ),
) !default;
```

Our default ratio is still `1.1`, but above screens of `1024px`, our ratio is increased to `1.3`. This means that our different font-sizes are more diverging in their sizes.

#### Defining a set of scales

In order to even be able to use different font-sizes, we need to define a set of different font-size entities. For that, we add a `scales` list to the `$FLUIDMS-CONFIG` map.

```scss
$FLUIDMS-CONFIG: (
    min-font-size: 16px,
    max-font-size: 24px,
    min-viewport: 480px,
    max-viewport: 1280px,
    ratio: 1.1,
    1024px: (
        ratio: 1.3,
    ),
    scales: (
        6,
        5,
        4,
        3,
        2,
        1,
        0,
        -1,
        -2,
        -3,
    ),
) !default;
```

Positive and negative integers are valid here. The numbers we add here basically result in the values we can use in the `ms()` function.

## Browser Support

As FluidMS uses [CSS custom properties](https://developer.mozilla.org/en-US/docs/Web/CSS/--*), the [browser support](https://caniuse.com/#feat=css-variables) is limited accordingly. A non-supporting browser will simply ignore the defined font-sizes and falls back to anything that is defined before the mixin call (ultimately to the browser default styles).
