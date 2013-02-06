# Type Up

Type Up is a Sass mixin that creates a baseline-conforming, vertically rhythmic and very readable typography based on <em>font size</em> and <em>line length</em>. You can use it to kickstart your typography on blogs and websites.

See [a couple of generated examples](http://tommikaikkonen.github.com/type-up/).

This mixin is still very much a work in progress.

## Why?

When typesetting a webpage, most of the CSS rules are based on a couple of factors such as line length and the x-height of a font. They determine the line height, which determines much of the spacing (that is, if you want to respect the baseline grid at some level). If you change one of the base factors (such as font), Type Up can save you the trouble of rewriting plenty of code.

## Basic Usage in Stylesheets

```scss
.text-wrapper {
	@include typeup-container($fontSize, $lineLength, $xHeight);
}
```


## Features

* Automatically adjusts line height for readability depending on line length
* Adjust line height with `$xHeight` for fonts with low or high x-heights
* Set baseline shift for headings with `$h[n]-baseline-shift` or for all headings with `$headingBaselineShift`. Default is `0.15em`.
* Set how many baselines of spacing headings have with `$h[n]-lines-before` or for all headings with `$heading-lines-before`. You can do the same for after.
* [Modular scale](http://modularscale.com/) for font-sizing, specify the ratio with `$ratio`
* Headings can use half a baseline, so that line-height won't be too high or too low

## Usage

1. Install extension (at the moment, copy the extensions directory to your compass project)
2. Import in your stylesheet
	```scss
	@import "typeup";
	```

3. Use the mixin
	```scss
	.main-wrapper {
		@include typeup-container(1em, 35em, 1);
	}
	```

4. Enjoy your newly generated, vertically rhythmic and readable typography.

## Known Limitations

* Accepts only `em` values for `$fontSize` and `$lineLength`
* Probably not old-browser friendly yet

## Future

* Breakpoints for responsive lineheight

## License

Copyright (c) 2013 Tommi Kaikkonen,
MIT License