# Type Up

Typeup is a Sass mixin that creates a baseline-conforming, vertically rhythmic and very readable typography based on <em>font size</em> and <em>line length</em>. You can use it to kickstart your typography on blogs and websites.

See [a couple of generated examples](http://tommikaikkonen.github.com/type-up/).

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
* Line-height is based on line length to maintain readability at all times


You can also supply a `$xHeight` argument (default `1`) to finetune the baseline with fonts that have very low or high x-heights.

## Usage

1. Install extension (at the moment, copy the extensions directory to your compass project)
2. Import in your stylesheet
	```scss
	@import "typeup";
	```

3. Write your settings
	```scss
	$fontSize: 1.25em;
	$lineLength: 35em;
	$xHeight: 1;
	```

3. Use the mixin
	```scss
	.main-wrapper {
		@include typeup($fontSize, $lineLength, $xHeight);
	}
	```
	For example:
	```scss
	.main-wrapper {
		@include typeup(1em, 35em, 1);
	}
	```

4. Enjoy your newly generated, vertically rhythmic and readable typography.

## Known Limitations

* Accepts only `em` values for `$fontSize` and `$lineLength`
* Probably not old-browser friendly yet

## License

Copyright (c) 2013 Tommi Kaikkonen
MIT License