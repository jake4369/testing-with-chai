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

#### Example:

```
test("#isDefined, #isUndefined", function () {
    assert.isDefined(null, "null is not undefined");
    assert.isUndefined(undefined, "undefined IS undefined");
    assert.isDefined("hello", "A string is not undefined");
});
```

## Unit 3 - Use Assert.isOK and Assert.isNotOK

In the Chai assertions library, '**assert.isOK**' and '**assert.isNotOk**' are methods used to test the truthiness or falsiness of a value, respectively. These methods are part of Chai's '**assert**' interface and help you validate that a given expression evaluates to a truthy or falsy value in JavaScript.

### assert.isOk

the '**assert.isOk**' method checks whether a value is truthy. In javaScript, a truthy value is any value that is not false, 0, -0, 0n (BingInt zero), "", null, undefined, or NaN.

```
assert.isOk(value, [message]);
```

- **value**: The value to be checked for truthiness.
- **message**: (Optional) A custom error message to display if the assertion fails.

### assert.isNotOk

The '**assert.isNotOk** method checks whether a value is falsy. In JavaScript, a falsy value is one of false, 0, -0, 0n, "", null, undefined, or NaN.

```
assert.isNotOk(value, [message]);
```

- **value**: The value to be checked for falsiness.
- **message**: (Optional) A custom error message to display if the assertion fails.

#### Example:

```
test("#isOk, #isNotOk", function () {
    assert.isNotOk(null, "null is falsey");
    assert.isOk("I'm truthy", "A string is truthy");
    assert.isOk(true, "true is truthy");
});
```

## Unit 4 - Test for Truthiness

'**isTrue**', '**isNotTrue**', '**isFalse**', and '**isNotFalse**' are specific assertions used to validate the truthiness or falsiness of expressions.

### isTrue

- **Purpose**: Asserts that the target is strictly equal to '**true**'
- **Usage**: If the express is strictly '**true**', the assertions passes. If it's anything else (including '**false**', '**null**', '**undefined**', '**0**', or any other falsy value), the assertion fails.

### isNotTrue

- **Purpose**: Asserts that the target is not strictly equal to true.
- **Usage**: If the expression is anything other than '**true**', the assertion passes.

### isFalse

- **Purpose**: Asserts that the target is strictly equal to '**false**'.
- **Usage**: If the expression is strictly '**false**', the assertion passes. If it’s anything else, the assertion fails.

### isNotFalse

- **Purpose**: Asserts that the target is not strictly equal to '**false**'.
- **Usage**: If the expression is anything other than '**false**', the assertion passes.

#### Example:

```
test("#isTrue, #isNotTrue", function () {
    assert.isTrue(true, "true is true");
    assert.isTrue(
    !!"double negation",
    "Double negation of a truthy value is true"
    );
    assert.isNotTrue(
    { value: "truthy" },
    "Objects are truthy, but are not boolean values"
    );
});
```

## Unit 5 - Use the Double Equals to Assert Equality

In the Chai assertions library, '**assert.equal()**' and '**assert.notEqual()**' are used to check for loose equality and inequality, respectively. These assertions compare values using the loose equality operator ('**==**'), which means they allow type coercion during comparison.

### assert.equal()

The '**assert.equal()**' method checks if two values are equal after type coercion. This means that it will consider different data types as equal if they can be converted to the same value.

```
assert.equal(actual, expected, [message])
```

### assert.notEqual()

The '**assert.notEqual()**' method checks if two values are not equal after type coercion. This means that it will consider different data types as not equal if they cannot be converted to the same value.

```
assert.notEqual(actual, expected, [message])
```

- **actual**: The value produced by the code.
- **expected**: The value to compare against.
- **message**: (Optional) A custom error message to display if the assertion fails.

#### Example:

```
test("#equal, #notEqual", function () {
    assert.equal(12, "12", "Numbers are coerced into strings with ==");
    assert.notEqual({ value: 1 }, { value: 1 }, "== compares object references");
    assert.equal(6 * "2", "12");
    assert.notEqual(6 + "2", "12");
});
```
