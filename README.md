# Quality Assurance with Chai

## Unit 1 - Learn How JavaScript Assertions Work

Assertions in the Mocha and Chai testing frameworks are statements used to validate that a particular condition is true during testing.They are essential in unit testing as they help determine if the code behaves as expected.

### Mocha

Mocha is a feature-rich JavaScript test framework that runs on Node.js and in the browser. It provides a robust set of tools for writing and running tests, but it does not include built-in assertion libraries. Instead, it allows you to use any assertion library you prefer, such as Chai.

See more - [https://mochajs.org/]

### Chai

Chai is an assertion library often used in conjuction with Mocha. It provides a variety of ways to assert values and conditions in your tests. It provides a variety of ways to assert values and conditions in your tests. Chai supports three assertion styles:

1. Assert style - similar to node.js assert module.
2. Expect style - a more expressive and readable style.
3. Should style - extends every object with a should property for natural language assertions.

## Unit 2 - Test if a Variable or Function is Defined

Using Mocha and Chai testing we can check whether a particular variable or function exists and is not undefined. This is a common test to ensure that all necessary components are properly initialized before the code under test is executed.

### Why Test if a Variable or Function is Defined?

- **Ensure Initialization**: Verify that the variables and functions are initialized before they are used, which helps catch errors early.

- **Prevent Runtime Errors**: Avoid runtime errors that occur when trying to use an undefined variable or function.

- **Improve Code Robustness**: Make the code more robust and reliable by ensuring all dependencies are properly set up.

### How to Test if a Variable or Function is Defined in Mocha and Chai

Chai provides assertions specifically designed for this purpose. The main assertions used to check if a variable or function is defined are assert.isDefined, but assert.isUndefined can also be used

```
test("#isDefined, #isUndefined", function () {
    assert.isDefined(null, "null is not undefined");
    assert.isUndefined(undefined, "undefined IS undefined");
    assert.isDefined("hello", "A string is not undefined");
});
```
