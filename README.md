# Type Up

A nifty Compass plugin for quick and precise typesetting without hours of math churning.

[See examples](http://tommikaikkonen.github.com/type-up/#examples)

Type Up gives you the CSS rules for beautiful vertical rhythm (line-heights, paddings, margins) based on font size and line length. Customize the details as you please or use the defaults.

## Features

* Line height is based on both font size and line length for optimized readability at all measures
* Everything is in `em`s
* [Modular scale](https://github.com/scottkellum/modular-scale) for heading sizes
* Headings work with half a baseline as needed

## Usage

Get started with the defaults:
```scss
@include typeup-body(
	1em, /* font size */
	35em /* line length */
);

// Your container element for text
.text-wrapper {
	width: 35em;
}
```

## Installation

1. Get the [source](https://github.com/tommikaikkonen/type-up) and copy the extension folder into your [Compass](http://compass-style.org/) project
2. Install the [Modular Scale](https://github.com/scottkellum/modular-scale) gem and require it in your Compass `config.rb` file
3. Import Type Up in your stylesheet with `@import "typeup";`
4. Apply styles to body with `@include typeup-body($fontSize, $lineLength, $xHeight)` or to a container with `@include typeup-container($fontSize, $lineLength, $xHeight)`
5. Cool typesetting, bro!

## Settings

Declare settings before importing typeup!
```scss
$h1LinesBefore: 2;
@import "typeup";
```
or, make a settings file:
```scss
@import "mytypeupsettings";
@import "typeup";
```
### List of Settings

#### General Settings

* `$fontSize`: the size of your font in `em`s. Default: `1em`
* `$lineLength`: the width of your text, in `em`s. Default: `35em`
* `$xHeight`: Use this to adjust the global line height (for example with fonts with very short or tall x-heights). Default is `1`, values between `0.5` to `1.5` should work all right.

#### Heading Scale

Type Up uses [Modular Scale](https://github.com/scottkellum/modular-scale) as its dependency to calculate heading sizes based on the base font size. Set the ratio used with `$ratio: golden();` or manually `$ratio: 5/4;`.

#### Heading Spacing

By default, each heading is spaced with [heading's calculated line height] * 1 on top and 0 on bottom. You can change these setting for all headings with

* `$headingLinesBefore`: the amount of line-heights as top margin for all headings unless overrided, default is `1`.
* `$headingLinesAfter` the amount of line-heights as bottom margin for all headings unless overrided, default is `0`.
* `$headingBaselineShift`: the amount of baseline shift for all headings unless overrided in `em`s. Default is `0em`. 

and for `h[n]`, you can set

* `$h[n]LinesBefore`: the amount of line-heights as top margin for heading *n*, default is `1`.

* `$h[n]LinesAfter`: the amount of line-heights as bottom margin for heading *n*, default is `1`.

* `$h[n]BaselineShift`: the amount of baseline shift for heading *n* in `em`s. Default is `0em`.

## Limitations

* Not tested on older browsers

## Author

Type Up is created by [Tommi Kaikkonen](http://www.kaikkonendesign.fi).

## License

Copyright 2013 Tommi Kaikkonen. Released under MIT License.