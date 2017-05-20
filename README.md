# Scss Scrutinizer
Scss unit testing framework

## Installation
`npm install scss-scrutinizer`

## How to Create a Test Suite
Create a scss file in the usual way and use your preferred tool to build it like normal. Scss Scrutinizer has no output except to the terminal. You can put it before your regular scss compilation tasks so that they will fail to build if Scss Scrutinizer hits an error, or create an entirely separate task.

Create a test suite for your project:
```
// your-project.spec.scss

// Import scss-scrutinizer into your project
@import ./node_modules/scss-scrutinizer/scss-scrutinizer

// Import the functions you want to test
// Here, index refers to a file that imports each function partial
@import './src/scss/functions/index';

// Import the specs you've written to test the functions
// This is an example using a function to determine if a hue is warm
@import 'is-warm.spec.scss';
```

## How to Write Specs
Write a spec by calling Scss' debug function with a string that describes your test followed by your expectations.

The expect function takes three parameters:
  1. The name of the function to call
  2. The parameters to the function (this can be a list)
  3. The expected result of the function
```
// is-warm.spec.scss
@debug('The is-warm function returns true if hue is less than or equal to 65',
  expect(is-warm, 60, true),
  expect(is-warm, 160, false)
);
```
