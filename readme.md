# grunt-recess

[Grunt][grunt] task to lint and minify CSS and LESS, using the Twitter [RECESS][recess] module:

> Developed at Twitter to support our internal styleguide, RECESS is a simple, attractive code quality tool for CSS built on top of LESS.

> Incorporate it into your development process as a linter, or integrate it directly into your build system as a compiler, RECESS will keep your source looking clean and super manageable.


## Getting Started

Install this grunt plugin next to your project's [grunt.js gruntfile][getting_started] with: `npm install grunt-recess`

Then add this line to your project's `grunt.js` gruntfile:

```javascript
grunt.loadNpmTasks('grunt-recess');
```


## Documentation

This grunt task is a [multi task](https://github.com/cowboy/grunt/blob/master/docs/types_of_tasks.md#multi-tasks-%E2%9A%91), which means you can specify multiple subtasks and grunt will iterate over them. The `dist` below is a subtask, you could e.g. create a `dev` subtask to handle stuff while developing.


### Example usage


#### Lint

```javascript
recess: {
	dist: {
		src: ['src/main.css']
	}
}
```


#### Lint and compile

```javascript
recess: {
	dist: {
		src: ['src/main.less'],
		dest: 'dist/main.css',
		options: {
			compile: true
		}
	}
}
```

`dest` is only needed when `compile: true`, it won't output any warnings in this mode.
You can also specify `.less` files and they will be compiled.


#### Lint, compile and concat

```javascript
recess: {
	dist: {
		src: [
			'src/main.css',
			'src/component.css'
		],
		dest: 'dist/combined.css',
		options: {
			compile: true
		}
	}
}
```

You can specify more than one `src` to concat the files.


### Options

```javascript
// Default
compile: false 				// Compiles CSS or LESS. Fixes white space and sort order.
compress: false				// Compress your compiled code
noIDs: true					// Doesn't complain about using IDs in your stylesheets
noJSPrefix: true			// Doesn't complain about styling .js- prefixed classnames
noOverqualifying: true		// Doesn't complain about overqualified selectors (ie: div#foo.bar)
noUnderscores: true			// Doesn't complain about using underscores in your class names
noUniversalSelectors: true	// Doesn't complain about using the universal * selector
prefixWhitespace: true		// Adds whitespace prefix to line up vender prefixed properties
strictPropertyOrder: true	// Complains if not strict property order
stripColors: false			// Strip colors from the Terminal output
zeroUnits: true				// Doesn't complain if you add units to values of 0
```


## Tests

Grunt currently doesn't have a way to test tasks directly. You can test this task by running `grunt` and check that it passes on the valid files and fails on the invalid.


## Contribute

In lieu of a formal styleguide, take care to maintain the existing coding style.


## License

MIT License
(c) [Sindre Sorhus](http://sindresorhus.com)


[grunt]: https://github.com/cowboy/grunt
[recess]: https://github.com/twitter/recess
[getting_started]: https://github.com/cowboy/grunt/blob/master/docs/getting_started.md
