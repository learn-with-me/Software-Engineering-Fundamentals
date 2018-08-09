Frontend Unit Testing

Typical set of modules in common projects

* mocha/tape \(unit tests\)
* chai/tape \(assertions\)
* sinon \(mock/spies\)
* istanbul \(coverage\)
* proxyquire \(JS files mocks\)

Typical set of modules in new projects

* jest \(unit tests, assertions, mocks, coverage, live test reload, JS file mocks\)

Jest

provides an integrated zero-configuration. It's smart, works with any compile-to-JS language and integrate seamlessly with Babel. Error messages are helpful, visual and color-coded. Stack trace points to the source of the problem quickly.

By default jest searches all the directories named **\_\_test\_\_ **and runs all JS files within them.

Jest will search all the file/module mocks in **\_\_mocks\_\_ **and runs all JS files within them.

Speed

```
Runs test in parallel processes to minimize runtime
Runs previously failed tests first
Automatically finds tests related to changed files to execute in the project
```

Commands

```
jest --watch
jest --coverage

```

Global Variables

```
afterAll, afterEach, beforeAll, beforeEach, check, describe, expect, gen, it, fit, jest, pit,
require, test, xdescribe, xit, xtest
```

Mocking

```
mockFn = jest.fn(?implementation)
Returns a new, unused mock/spy function. Optionally takes a mock implementation

• mockFn.mock.calls
• mockFn.mock.instances
• mockFn.mockClear()
• mockFn.mockReset()
• mockFn.mockImplementation(fn)
• mockFn.mockImplementationOnce(fn)
• mockFn.mockReturnThis()
• mockFn.mockReturnValue(value)
• mockFn.mockReturnValueOnce(value)
```

Module mocking and re-loading

```
jest.mock('../moduleName', () => {
    return jest.fn(() => 42);
});

const moduleName = require('../moduleName');
moduleName(); // Will return '42';


const React1 = require('react');
jest.resetModules();
const React2 = require('react');
React1 !== React2;
// These two are separate copies of React
Error messages are 
```

Installation

```
npm i -D babel-jest

config
------
coverageThreshold     - If the thresholds are not met, jest will return failure.

```



