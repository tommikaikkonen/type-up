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
	1 /* x-height ratio */
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
## List of Settings

<table>
	<tr>
		<th>Variable</th>
		<th>Default</th>
		<th>Description</th>
	</tr>
	<tr>
		<td>
			$fontSize
		</td>
		<td>
			1em
		</td>
		<td>
			The size of your font in ems or pixels. Pixels will be converted to ems inside Type Up.
		</td>
	</tr>
	<tr>
		<td>
			$lineLength
		</td>
		<td>
			35em
		</td>
		<td>
			The width of your text, in ems or pixels. Pixels will be converted to ems inside Type Up.
		</td>
	</tr>
	<tr>
		<td>
			$xHeight
		</td>
		<td>
			1
		</td>
		<td>
			Use this to adjust the global line height (for example with fonts with very short or tall x-heights).
		</td>
	</tr>
	<tr>
		<td>
			$ratio
		</td>
		<td>
			fourth()
		</td>
		<td>
			The ratio for modular scale. Can be set as a number, such as 11/10.
		</td>
	</tr>
	<tr>
		<td>
			$headingLinesBefore
		</td>
		<td>
			1
		</td>
		<td>
			Multiplier for heading spacing above it. The value to be multiplied is the calculated line height of the heading.
		</td>
	</tr>
	<tr>
		<td>
			$headingLinesAfter
		</td>
		<td>
			0
		</td>
		<td>
			Multiplier for heading spacing below it. The value to be multiplied is the calculated line height of the heading.

		</td>
	</tr>
	<tr>
		<td>
			$headingBaselineShift
		</td>
		<td>
			0em
		</td>
		<td>
			The amount of baseline shift for all headings.

		</td>
	</tr>
	<tr>
		<td>
			$h[1-6]LinesBefore
		</td>
		<td>
			$headingLinesBefore
		</td>
		<td>
			Multiplier for the specific heading's spacing above. The value to be multiplied is the calculated line height of the heading.

		</td>
	</tr>
	<tr>
		<td>
			$h[1-6]LinesAfter
		</td>
		<td>
			$headingLinesAfter
		</td>
		<td>
			Multiplier for the specific heading's spacing below. The value to be multiplied is the calculated line height of the heading.

		</td>
	</tr>
	<tr>
		<td>
			$h[1-6]BaselineShift
		</td>
		<td>
			$headingBaselineShift
		</td>
		<td>
			The amount of baseline shift for a specific heading level.

		</td>
	</tr>
	<tr>
		<td>
			$pixelSnapBaseSize: true
		</td>
		<td>
			true
		</td>
		<td>
			A boolean deciding whether the fontSize value you give TypeUp is pixel snapped.

		</td>
	</tr>
	<tr>
		<td>
			$baseFontSize
		</td>
		<td>
			16px
		</td>
		<td>
			The browser base font size that TypeUp does its calculations from. You shouldn't have to change this.
		</td>
	</tr>
	<tr>
		<td>
			$minimumLineHeight
		</td>
		<td>
			0.7
		</td>
		<td>
			The minimum line height that TypeUp sets for any element. Unless you're working with some funky typesetting, you don't need to change this.
		</td>
	</tr>
	<tr>
		<td>
			$doubleStrandedHeadingClasses
		</td>
		<td>
			false
		</td>
		<td>
			If set to true, will clone each headings styles into a corresponding `.headingN` class using @extend.
		</td>
	</tr>
	<tr>
		<td>
			$startModularScaleAt
		</td>
		<td>
			4
		</td>
		<td>
			The modular scale number that is assigned to `h1`. Next one gets 3, next one gets 2, etc. The modular scale cuts off at 0, so with the default settings `h5` and `h6` get a modular scale number of 0.
		</td>
	</tr>
</table>

## Mixins

### Body
```scss
@include typeup-body($fontSize, $lineLength, $xHeight);
```
The typeup-body mixin should be included by itself, not under any selector.

### Container
```scss
@include typeup-container($fontSize, $lineLength, $xHeight);
```
The typeup-container mixin should be used when you want the rules to apply only under a specific element. It should be included inside a selector. This mixin also establishes the width of the element with $lineLength.

### Spacer
```scss
@include typeup-spacer(
	$size-in-ems,
	$before: $headingLinesBefore, // uses default value if not supplied
	$after: $headingLinesAfter, // uses default value if not supplied
	$baselineShift: $headingBaselineShift, // optional
	$overrideSpacingWithBaseline: $overrideSpacingWithBaseline // uses default value if not supplied
	);
```
The spacer mixin is used to give vertical rhythm to headings inside TypeUp, but you can use it for other things.

This is how it works:

1. See how many baselines are needed to meet $size-in-ems, in half increments
2. Multiply by the global line height, pixel snap it
3. Multiply that number with `before` to get `margin-top` and `after` to get `margin-bottom`
4. Apply baseline shift if larger than 0 em with `position:relative` and `top`

If $overrideSpacingWithBaseline is true (default is false), the `before` and `after` values are multiplied by the global line height.

You could use the mixin to make simple paragraphs: `@include typeup-spacer($fontSize, 0, 1, 0, false);` which would apply a line-height and some margin to the bottom. Or any other element where you have a differing font size - line height will be adjusted correctly. 

## Limitations

* Not tested on older browsers

## Author

Type Up is created by [Tommi Kaikkonen](http://www.kaikkonendesign.fi).

## License

Copyright 2013 Tommi Kaikkonen. Released under MIT License.