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

#### Syntax:

```
assert.isOk(value, [message]);
```

- **value**: The value to be checked for truthiness.
- **message**: (Optional) A custom error message to display if the assertion fails.

### assert.isNotOk

The '**assert.isNotOk** method checks whether a value is falsy. In JavaScript, a falsy value is one of false, 0, -0, 0n, "", null, undefined, or NaN.

#### Syntax:

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

#### Syntax:

```
assert.equal(actual, expected, [message])
```

### assert.notEqual()

The '**assert.notEqual()**' method checks if two values are not equal after type coercion. This means that it will consider different data types as not equal if they cannot be converted to the same value.

#### Syntax:

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

## Unit 6 - Use the Triple Equals to Assert Strict Equality

'**assert.strictEqual()**' and '**assert.notStrictEqual()**' are used to check for strict equality and inequality, respectively. These assertions compare values using the strict equality operator ('**===**'), which means they do not allow type coercion.

### assert.strictEqual()

The '**assert.strictEqual()**' method checks if two values are strictly equal, meaning that they must be of the same type and have the same value.

#### Syntax:

```
assert.strictEqual(actual, expected, [message]);
```

### assert.notStrictEqual()

The '**assert.notStrictEqual()**' method checks if two values are not strictly equal, meaning that they must either be of different types or have different values.

#### Syntax:

```
assert.strictEqual(actual, expected, [message]);
```

- **actual**: The value produced by the code.
- **expected**: The value to compare against.
- **message**: (Optional) A custom error message to display if the assertion fails.

#### Example:

```
test("#strictEqual, #notStrictEqual", function () {
    assert.notStrictEqual(6, "6");
    assert.strictEqual(6, 3 * 2);
    assert.strictEqual(6 * "2", 12);
    assert.notStrictEqual([1, "a", {}], [1, "a", {}]);
});
```

## Unit 7 - Assert Deep Equality with .deepEqual and .notDeepEqual

'**assert.deepEqual()**' and '**assert.notDeepEqual()**' are used to check for deep equality and inequality, respectively. These assertions are particularly useful when comparing complex objects, arrays, or nested structures to ensure that they have identical content.

### assert.deepEqual()

The '**assert.deepEqual()**' method checks if two values are deeply equal, meaning that they have the same properties with the same values, including nested objects and arrays.

### assert.notDeepEqual()

The '**assert.notDeepEqual()**' method checks if two values are not deeply equal, meaning that there is at least one property or value that differs between them, including in nested structures.

#### Example:

```
test("#deepEqual, #notDeepEqual", function () {
    assert.deepEqual(
        { a: "1", b: 5 },
        { b: 5, a: "1" },
        // "The order of keys doesn't matter"
    );

    assert.notDeepEqual(
        { a: [5, 6] },
        { a: [6, 5] },
        //"The order of array elements does matter"
    );
});
```

## Unit 8 - Compare the Properties of Two Elements

'**assert.isAbove**' and '**assert.isAtMost**' are methods used for making numberical comparisons, specifically to assert whether one value is greater than or less than or equal to another value.

### assert.isAbove()

The '**assert.isAbove()** method is used to assert that one value is strictly greater than anpther. This is useful for scenarios where you want to ensure that a number exceeds a certain threshold.

#### Example:

```
describe('assert.isAbove()', function() {
  test('should pass when the first value is greater than the second', function() {
    assert.isAbove(10, 5, '10 is above 5');
    assert.isAbove(100, 50, '100 is above 50');
  });

  test('should fail when the first value is not greater than the second', function() {
    assert.isAbove(5, 10, '5 is not above 10'); // This will fail
    assert.isAbove(5, 5, '5 is not above 5'); // This will fail
  });
});
```

In this example:

- The first test case will pass because '**10**' is greater than '**5**' and '**100**' is greater than '**50**'.
- The second test case will fail because 5 is not greater than 10 and 5 is not greater than 5.

### assert.isAtMost()

The '**assert.isAtMost()**' method is used to assert that one value is less than or equal to another. This is useful for scenarios where you want to ensure that a number does not exceed a certain threshold.

#### Example:

```
describe('assert.isAtMost()', function() {
  test('should pass when the first value is less than or equal to the second', function() {
    assert.isAtMost(5, 10, '5 is at most 10');
    assert.isAtMost(5, 5, '5 is at most 5');
  });

  test('should fail when the first value is greater than the second', function() {
    assert.isAtMost(10, 5, '10 is not at most 5'); // This will fail
    assert.isAtMost(6, 5, '6 is not at most 5'); // This will fail
  });
});
```

In this example:

- The first test case will pass because '**5**' is less than or equal to '**10**' and '**5**' is equal to '**5**'.
- The second test case will fail because '**10**' is greater than '**5**' and '**6**' is greater than '**5**'.

## Unit 9 - Test if One Value is Below or At Least as Large as Another

'**assert.isBelow()**' and '**assert.isAtLeast()**' are used to perform numerical comparisons. These methods help verify that one number is less than or greater than or equal to another number, respectively.

### assert.isBelow()

The '**assert.isBelow()**' method checks if the first value is strictly less than the second value. This is useful for assertions where you need to verify that a numerical value is below a certain threshold.

```
describe('assert.isBelow()', function() {
  test('should pass when the first value is less than the second', function() {
    assert.isBelow(5, 10, '5 is below 10');
    assert.isBelow(3.5, 4.5, '3.5 is below 4.5');
  });

  test('should fail when the first value is not less than the second', function() {
    assert.isBelow(10, 5, '10 is not below 5'); // This will fail
    assert.isBelow(5, 5, '5 is not below 5'); // This will fail
  });
});
```

In this example:

- The first test case will pass because '**5**' is less than '**10**' and '**3.5**' is less than '**4.5**'.
- The second test case will fail because '**10**' is not less than '**5**' and '**5**' is not less than '**5**'.

### assert.isAtLeast()

The '**assert.isAtLeast()**' method checks if the first value is greater than or equal to the second value. This is useful for assertions where you need to verify that a numerical value meets or exceeds a certain threshold.

#### Example:

```
describe('assert.isAtLeast()', function() {
  test('should pass when the first value is greater than or equal to the second', function() {
    assert.isAtLeast(10, 5, '10 is at least 5');
    assert.isAtLeast(5, 5, '5 is at least 5');
  });

  test('should fail when the first value is not greater than or equal to the second', function() {
    assert.isAtLeast(5, 10, '5 is not at least 10'); // This will fail
    assert.isAtLeast(2.5, 3.5, '2.5 is not at least 3.5'); // This will fail
  });
});
```

In this example:

- The first test case will pass because '**10**' is greater than '**5**' and '**5**' is equal to '**5**'.
- The second test case will fail because '**5**' is not greater than '**10**' and '**2.5**' is not greater than '**3.5**'.

## Unit 10 - Test if a Value Falls within a Specific Range

The '**assert.approximately()**' method in the Chai assertion library is used to check if a number is approximately equal to another number within a certain tolerance. This is particularly useful when dealing with floating-point numbers where you want to allow for a small margin of error.

In the context of the '**assert.approximately()**' method, a delta refers to the tolerance or allowable margin of error between two numerical values. It defines the range within which the actual value can differ from the expected value for the assertion to still pass.

When you use '**assert.approximately()**', you are asserting that the actual value is within a certain range (defined by the delta) of the expected value. The delta represents the maximum difference allowed between the two values. If the absolute difference between the actual value and the expected value is less than or equal to the delta, the assertion passes. Otherwise, it fails.

### assert.approximately()

The '**assert.approximately()**' method checks if two numbers are approximately equal to each other within a specified delta (tolerance). It asserts that the absolute difference between the two numbers is less than or equal to the delta.

#### Example:

```
describe('assert.approximately()', function() {
  test('should pass when the actual value is within the tolerance of the expected value', function() {
    assert.approximately(5.1, 5, 0.2, '5.1 is approximately equal to 5 within a delta of 0.2');
    assert.approximately(3.14, 3.15, 0.01, '3.14 is approximately equal to 3.15 within a delta of 0.01');
  });

  test('should fail when the actual value is outside the tolerance of the expected value', function() {
    assert.approximately(5.3, 5, 0.2, '5.3 is not approximately equal to 5 within a delta of 0.2'); // This will fail
    assert.approximately(3.14, 3.15, 0.001, '3.14 is not approximately equal to 3.15 within a delta of 0.001'); // This will fail
  });
});
```

## Unit 11 - Test if a Value is an Array

The Chai assertion library includes methods for asserting whether a value is an array or not an array. These methods are '**assert.isArray**' and '**assert.isNotArray**'.

### assert.isArray()

The '**assert.isArray()**' method checks if a given value is an array. This is useful when you want to validate that a certain variable or expression results in an array.

#### Syntax:

```
assert.isArray(value, [message]);
```

- **value**: The value that you want to check.
- **message**: (Optional) A custom error message to display if the assertion fails.

#### Example:

```
describe('assert.isArray()', function() {
  test('should pass when the value is an array', function() {
    assert.isArray([1, 2, 3], 'value is an array');  // Passes
    assert.isArray([], 'value is an array');        // Passes
  });

  test('should fail when the value is not an array', function() {
    assert.isArray('not an array', 'value is not an array');  // Fails
    assert.isArray({ a: 1 }, 'value is not an array');       // Fails
    assert.isArray(null, 'value is not an array');           // Fails
  });
});
```

In this example:

- The first test case passes because '**[1, 2, 3]**' and '**[]**' are arrays.
- The second test case fails because '**not an array**', '**{ a: 1 }**', and '**null**' are not arrays.

### assert.isNotArray()

The '**assert.isNotArray()**' method checks if a given value is not an array. This is useful when you want to ensure that a certain variable or expression does not result in an array.

#### Syntax:

```
assert.isNotArray(value, [message]);
```

#### Example:

```
describe('assert.isNotArray()', function() {
    test('should pass when the value is not an array', function() {
        assert.isNotArray('not an array', 'value is not an array');
        assert.isNotArray({ a: 1 }, 'value is not an array');       // Passes
        assert.isNotArray(null, 'value is not an array');           // Passes
    });

    test('should fail when the value is an array', function() {
        assert.isNotArray([1, 2, 3], 'value is an array');  // Fails
        assert.isNotArray([], 'value is an array');        // Fails
    });
});
```

In this example:

- The first test case passes because '**not an array**', '**{ a: 1 }**', and '**null**' are not arrays.
- The second test case fails because '**[1, 2, 3]**' and '**[]**' are arrays.

These assertions are useful for type-checking in your tests, ensuring that values meet the expected type requirements, which is particularly important when dealing with functions and methods that return or operate on arrays.

## Unit 12 - Test if an Array Contains an Item

'**assert.include**' and '**assert.notInclude**' are methods used to assert the presence or absence of a value within a collection. This includes arrays, strings, and objects. They are particularly useful for checking if a specific element element exists within a container or if a substring exists within a string.

### assert.include()

The '**asert.include**' method checks if a value is present within a collection (an array, string, or object). If the value is found, the assertion passes; otherwise, it fails.

#### Syntax:

```
assert.include(haystack, needle, [message]);
```

- **haystack**: The collection to search within. This can be an array, string, or object.
- **needle**: The value to search for within the haystack.
- **message**: (Optional) A custom error message to display if the assertion fails.

#### Example with Arrays:

```
describe('assert.include() with arrays', function() {
  test('should pass when the array includes the value', function() {
    assert.include([1, 2, 3], 2, 'array includes 2');  // Passes
    assert.include(['a', 'b', 'c'], 'b', 'array includes b');  // Passes
  });

  test('should fail when the array does not include the value', function() {
    assert.include([1, 2, 3], 4, 'array does not include 4');  // Fails
  });
});
```

### assert.notInclude()

The '**assert.notInclude()**' method checks if a value is not present within a collection (an array, string, or object). If the value is not found, the assertion passes; otherwise, it fails.

#### Syntax:

```
assert.notInclude(haystack, needle, [message]);
```

#### Example with Arrays:

```
describe('assert.notInclude() with arrays', function() {
  test('should pass when the array does not include the value', function() {
    assert.notInclude([1, 2, 3], 4, 'array does not include 4');  // Passes
  });

  test('should fail when the array includes the value', function() {
    assert.notInclude([1, 2, 3], 2, 'array includes 2');  // Fails
  });
});
```

These assertions are particularly useful for verifying the presence or absence of elements or substrings within collections, ensuring that your data contains or excludes specific values as expected.

## Unit 13 - Test if a Value is a String

'**assert.isString**' and '**assert.isNotString**' are methods used to assert whether a given value is a string or not a string, respectively. These methods are useful for type-checking in your tests to ensure that values are of the expected type.

### assert.isString()

The '**assert.isString()**' method checks if a given value is a string. If the value is a string, the assertion passes; otherwise, it fails.

#### Syntax:

```
assert.isString(value, [message]);
```

- **value**: The value to check.
- **message**: (Optional) A custom error message to display if the assertion fails.

#### Example:

```
describe('assert.isString()', function() {
  test('should pass when the value is a string', function() {
    assert.isString('hello world', 'value is a string');  // Passes
    assert.isString('', 'empty string is still a string');  // Passes
  });

  test('should fail when the value is not a string', function() {
    assert.isString(123, 'value is not a string');  // Fails
    assert.isString({ key: 'value' }, 'object is not a string');  // Fails
    assert.isString(['a', 'b', 'c'], 'array is not a string');  // Fails
  });
});
```

In this example:

- The first test case passes because '**hello world**' and **''** are strings.
- The second test case fails because '**123**', '**{ key: 'value' }**', and '**['a', 'b', 'c']**' are not strings.

### assert.isNotString()

The '**assert.isNotString()**' method checks if a given value is not a string. If the value is not a string, the assertion passes; otherwise, it fails.

#### Syntax:

```
assert.isNotString(value, [message]);
```

#### Example:

```
describe('assert.isNotString()', function() {
  test('should pass when the value is not a string', function() {
    assert.isNotString(123, 'value is not a string');  // Passes
    assert.isNotString({ key: 'value' }, 'object is not a string');  // Passes
    assert.isNotString(['a', 'b', 'c'], 'array is not a string');  // Passes
  });

  test('should fail when the value is a string', function() {
    assert.isNotString('hello world', 'value is a string');  // Fails
    assert.isNotString('', 'empty string is still a string');  // Fails
  });
});
```

## Unit 14 - Test if a String Contains a Substring

'**assert.include**' and '**assert.notInclude**' are methods used to assert the presence or absence of a value within a collection. This includes arrays, strings, and objects. They are particularly useful for checking if a specific element element exists within a container or if a substring exists within a string.

### assert.include()

The '**assert.include()**' method checks if a value is present within a collection (an array, string, or object). If the value is found, the assertion passes; otherwise, it fails.

#### Syntax:

```
assert.include(haystack, needle, [message]);
```

- **haystack**: The collection to search within. This can be an array, string, or object.
- **needle**: The value to search for within the haystack.
- **message**: (Optional) A custom error message to display if the assertion fails.

#### Example:

```
describe('assert.include() with strings', function() {
  test('should pass when the string includes the substring', function() {
    assert.include('hello world', 'world', 'string includes world');  // Passes
    assert.include('chai assertion library', 'assertion', 'string includes assertion');  // Passes
  });

  test('should fail when the string does not include the substring', function() {
    assert.include('hello world', 'foo', 'string does not include foo');  // Fails
  });
});
```

### assert.notInclude()

The '**assert.notInclude()**' method checks if a value is not present within a collection (an array, string, or object). If the value is not found, the assertion passes; otherwise, it fails.

#### Syntax:

```
assert.notInclude(haystack, needle, [message]);
```

#### Example:

```
describe('assert.notInclude() with strings', function() {
  test('should pass when the string does not include the substring', function() {
    assert.notInclude('hello world', 'foo', 'string does not include foo');  // Passes
  });

  test('should fail when the string includes the substring', function() {
    assert.notInclude('hello world', 'world', 'string includes world');  // Fails
  });
});
```

For example of how to use '**assert.include()**' and '**assert.notInclude()**' with arrays, see **Unit 12 - Test if an Array Contains an Item**

## Unit 15 - Use Regular Expressions to Test a String

'**assert.match**' and '**assert.notMatch**' are methods used to assert whether a given string matches or does not match a regular expression pattern. These methods are particularly useful for validating that a string conforms to a certain format or contains specific patterns.

### assert.match()

The '**assert.match()**' method checks if a given string matches a specified regular expression pattern. If the string matches the pattern, the assertion passes; otherwise, it fails.

#### Syntax:

```
assert.match(string, regexp, [message]);
```

**string**: The string to test against the regular expression.
**regexp**: The regular expression pattern to match.
**message**: (Optional) A custom error message to display if the assertion fails.

#### Example:

```
describe('assert.match()', function() {
  test('should pass when the string matches the regular expression', function() {
    assert.match('hello world', /hello/, 'string contains "hello"');  // Passes
    assert.match('abc123', /^\w+\d+$/, 'string matches alphanumeric pattern');  // Passes
  });

  test('should fail when the string does not match the regular expression', function() {
    assert.match('goodbye world', /hello/, 'string does not contain "hello"');  // Fails
    assert.match('123abc', /^\w+\d+$/, 'string does not match pattern');  // Fails
  });
});
```

In this example:

The first test case passes because '**hello world**' contains '**hello**' and '**abc123**' matches the alphanumeric pattern.
The second test case fails because '**goodbye world**' does not contain '**hello**' and '**123abc**' does not match the alphanumeric pattern at the start.

### assert.notMatch()

The '**assert.notMatch()**' method checks if a given string does not match a specified regular expression pattern. If the string does not match the pattern, the assertion passes; otherwise, it fails.

#### Syntax:

```
assert.notMatch(string, regexp, [message]);
```

#### Example:

```
describe('assert.notMatch()', function() {
  test('should pass when the string does not match the regular expression', function() {
    assert.notMatch('goodbye world', /hello/, 'string does not contain "hello"');  // Passes
    assert.notMatch('123abc', /^\w+\d+$/, 'string does not match pattern');  // Passes
  });

  test('should fail when the string matches the regular expression', function() {
    assert.notMatch('hello world', /hello/, 'string contains "hello"');  // Fails
    assert.notMatch('abc123', /^\w+\d+$/, 'string matches alphanumeric pattern');  // Fails
  });
});
```

In this example:

The first test case passes because '**goodbye world**' does not contain '**hello**' and '**123abc**' does not match the alphanumeric pattern at the start.
The second test case fails because '**hello world**' contains '**hello**' and '**abc123**' matches the alphanumeric pattern.

These assertions are particularly useful for validating that strings adhere to specific formats or contain certain patterns, which is important in many scenarios such as input validation, parsing, and ensuring data integrity.

## Unit 16 - Test if an Object has a Property

'**assert.property**' and '**assert.notProperty**' are methods used to assert the presence or absence of a specific property in an object. These methods are particularly useful for verifying that an object has (or does not have) a certain property, which is important when dealing with objects that must conform to specific schemas or structures.

### assert.property()

The '**assert.property()**' method checks if a given object has a specified property. If the object has the property, the assertion passes; otherwise, it fails.

#### Syntax:

```
assert.property(object, property, [message]);
```

- **object**: The object to check.
- **property**: The name of the property to check for.
- **message**: (Optional) A custom error message to display if the assertion fails.

#### Example:

```
describe('assert.property()', function() {
  test('should pass when the object has the specified property', function() {
    const obj = { a: 1, b: 2, c: 3 };
    assert.property(obj, 'a', 'object has property a');  // Passes
    assert.property(obj, 'b', 'object has property b');  // Passes
  });

  test('should fail when the object does not have the specified property', function() {
    const obj = { a: 1, b: 2, c: 3 };
    assert.property(obj, 'd', 'object does not have property d');  // Fails
  });
});
```

In this example:

- The first test case passes because the object '**obj**' has properties '**a**' and '**b**'.
- The second test case fails because the object '**obj**' does not have '**a**' property '**d**'.

### assert.notProperty()

The '**assert.notProperty()**' method checks if a given object **does not** have a specified property. If the object does not have the property, the assertion passes; otherwise, it fails.

#### Syntax:

```
assert.notProperty(object, property, [message]);
```

#### Example:

```
describe('assert.notProperty()', function() {
  test('should pass when the object does not have the specified property', function() {
    const obj = { a: 1, b: 2, c: 3 };
    assert.notProperty(obj, 'd', 'object does not have property d');  // Passes
    assert.notProperty(obj, 'e', 'object does not have property e');  // Passes
  });

  test('should fail when the object has the specified property', function() {
    const obj = { a: 1, b: 2, c: 3 };
    assert.notProperty(obj, 'a', 'object has property a');  // Fails
  });
});
```

In this example:

- The first test case passes because the object '**obj**' does not have properties '**d**' and '**e**'.
- The second test case fails because the object '**obj**' has '**a**' property '**a**'.
