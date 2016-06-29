## Website Performance Optimization portfolio project

In this challenge, I optimized this online portfolio for speed. In particular, I optimized the critical rendering path to make pages render as quickly as possible by applying the techniques I picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

### Getting started

To view optimizations, clone or download the repository and inspect the code (mainly `index.html` and `views/js/main.js`).

####Part 1: Optimized PageSpeed Insights score for `index.html`

These are the steps I took to achieve a Page Speed score of 90+:

	1. Resized portfolio thumbnail images as small as possible without pixelating
	2. Compressed image files using Grunt imagemin
	3. Inlined CSS to avoid render blocking
	4. Removed Google Fonts
	5. Added `async` to scripts and moved to bottom of `body` tag

####Part 2: Optimized frames per second in `pizza.html`

These are the steps I took to achieve a consistent frame-rate of 60fps when scrolling:

	Refactored `updatePostions()` to avoid forced synchronous layout by:
		* Finding that there are the same four values of the `phase` calculation by logging values to the console
		* Using a `for` loop, putting these values into an array to reference instead of recalculating each time
		* Creating a separate `for` loop to update `left` property of each pizza (only 48 pizzas instead of 200)

These are the steps I took so the time to resize pizzas is less than 5 ms using pizza size slider:

	Simplified `resizePizzas()` by:
		* Removing uncessary calculation of `dx` with `determineDx()` and `sizeSwitcher()`
		* Assigned new pizza width directly through `changePizzaSizes()`
