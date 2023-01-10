
# Table of contents
- [Table of contents](#table-of-contents)
- [Unit Tests](#unit-tests)
- [FIRST Acronym](#first-acronym)
- [TEets](#teets)


# Unit Tests


# FIRST Acronym

In software testing, the "FIRST" acronym stands for:

* `F`: Fast
* `I`: Independent
* `R`: Repeatable
* `S`: Self-validating
* `T`: Timely

These are characteristics that are often considered to be desirable properties of a software testing process.

`Fast` means that the tests should be quick to execute, so that developers can run them frequently without incurring a significant time overhead.

`Independent` means that the tests should not depend on the results of other tests, so that they can be run in any order without affecting the outcome.

`Repeatable` means that the tests should always produce the same results, regardless of when or where they are run.

`Self-validating` means that the tests should have a clear pass/fail outcome, so that it is easy to determine whether the system under test is working correctly.

`Timely` means that the tests should be written and run at the appropriate time in the development process, so that any issues are detected and resolved as early as possible.

These are considered to be best practice for effective software testing. When those best practices are applied, it makes the testing process more effective, efficient, maintainable and robust.

```javascript
const myModule = require('./myModule');

describe('myModule', () => {
  it('should add two numbers together', () => {
    const result = myModule.add(3, 4);
    expect(result).toEqual(7);
  });
});
```

This test is designed to be "FIRST" because it meets the following criteria:

* "Fast": The test is simple and doesn't involve any complex operations, so it runs quickly.

* "Independent": The test doesn't depend on any external state or the results of other tests, so it can be run in any order without affecting the outcome.

* "Repeatable": The test always produces the same result when given the same inputs, regardless of when or where it is run.

* "Self-validating": The test has a clear pass/fail outcome, determined by whether the result of the function myModule.add(3,4) matches the expected output 7.

* "Timely": The test is written and run as part of the development process, ideally at the same time the function is implemented

# TEets