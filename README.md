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
</table>

## Mixins
```scss
@include typeup-body($fontSize, $lineLength, $xHeight);
```
The typeup-body mixin should be included by itself, (not under any selector).

```scss
@include typeup-container($fontSize, $lineLength, $xHeight);
```
The typeup-container mixin should be used when you want the rules to apply only under a specific element. It should be included inside a selector. This mixin also establishes the width of the element with $lineLength.

## Limitations

* Not tested on older browsers

## Author

Type Up is created by [Tommi Kaikkonen](http://www.kaikkonendesign.fi).

## License

Copyright 2013 Tommi Kaikkonen. Released under MIT License.