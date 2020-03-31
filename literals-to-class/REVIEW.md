# es6-classes/

> 3/31/2020, 3:14:16 PM 

## literals-to-class/ - error

* [../REVIEW.md](../REVIEW.md)

### files

* [challenge-1.js](#challenge-1js---error) - error
* [challenge-2.js](#challenge-2js---error) - error
* [challenge-3.js](#challenge-3js---error) - error
* [challenge-4.js](#challenge-4js---error) - error
* [example.js](#examplejs---pass) - pass

---

## challenge-1.js - error

* [review source](challenge-1.js)

```txt
ReferenceError: _ is not defined
    at Object.<anonymous> ( [...] /literals-to-class/challenge-1.js:27:19)
    at Module._compile (internal/modules/cjs/loader.js:777:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:788:10)
    at Module.load (internal/modules/cjs/loader.js:643:32)
    at Function.Module._load (internal/modules/cjs/loader.js:556:12)
    at Module.require (internal/modules/cjs/loader.js:683:19)
    at require (internal/modules/cjs/helpers.js:16:16)
    at evaluateFile ( [...] /review.js:101:5)
    at  [...] /review.js:139:28
    at Array.map (<anonymous>)
```

```js
// the challenge

const literalA = {
  numbers: [-1, 1, 0, -2, 2],
  get evens() {
    return this.numbers.filter(num => num % 2 === 0);
  },
  get odds() {
    return this.numbers.filter(num => num % 2 !== 0);
  }
};

const literalB = {
  numbers: [3, 67, -21, 6, -4],
  get evens() {
    return this.numbers.filter(num => num % 2 === 0);
  },
  get odds() {
    return this.numbers.filter(num => num % 2 !== 0);
  }
};

// the solution

class EvenOdd { };

const instanceA = _;
const instanceB = _;

// the tests

const test1a = instanceA instanceof EvenOdd;
const test1b = instanceB instanceof EvenOdd;
console.assert(test1a, 'Test 1.A - instanceof');
console.assert(test1b, 'Test 1.B ');

const test2a = instanceA.hasOwnProperty('numbers');
const test2b = instanceB.hasOwnProperty('numbers');
console.assert(test2a, 'Test 2.A - own properties');
console.assert(test2b, 'Test 2.B');

const test3a = !instanceA.hasOwnProperty('evens') && !instanceA.hasOwnProperty('odds');
const test3b = !instanceB.hasOwnProperty('evens') && !instanceB.hasOwnProperty('odds');
console.assert(test3a, 'Test 3.A - inherited properties');
console.assert(test3b, 'Test 3.B');

const test4a = instanceA.evens.toString() === '0,-2,2';
const test4b = instanceB.evens.toString() === '6,-4';
console.assert(test4a, 'Test 4.A - evens');
console.assert(test4b, 'Test 4.B');

const test5a = instanceA.odds.toString() === '-1,1';
const test5b = instanceB.odds.toString() === '3,67,-21';
console.assert(test5a, 'Test 5.A - odds');
console.assert(test5b, 'Test 5.B');

instanceA.numbers = [5, 4, 3, 2, 1, 0];
instanceB.numbers = [0, -1, -2, -3, -4, -5];

const test6a = instanceA.evens.toString() === '4,2,0';
const test6b = instanceB.evens.toString() === '0,-2,-4';
console.assert(test6a, 'Test 6.A - evens');
console.assert(test6b, 'Test 6.B');

const test7a = instanceA.odds.toString() === '5,3,1';
const test7b = instanceB.odds.toString() === '-1,-3,-5';
console.assert(test7a, 'Test 7.A - odds');
console.assert(test7b, 'Test 7.B');

```

[TOP](#es6-classes)

---

## challenge-2.js - error

* [review source](challenge-2.js)

```txt
+ PASS: Test 1.A - instanceof
+ PASS: Test 1.B 
- FAIL: Test 2.A - own properties
- FAIL: Test 2.B
+ PASS: Test 3.A - inherited properties
+ PASS: Test 3.B
TypeError: Cannot read property 'max' of undefined
    at Object.<anonymous> ( [...] /literals-to-class/challenge-2.js:54:32)
    at Module._compile (internal/modules/cjs/loader.js:777:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:788:10)
    at Module.load (internal/modules/cjs/loader.js:643:32)
    at Function.Module._load (internal/modules/cjs/loader.js:556:12)
    at Module.require (internal/modules/cjs/loader.js:683:19)
    at require (internal/modules/cjs/helpers.js:16:16)
    at evaluateFile ( [...] /review.js:101:5)
    at  [...] /review.js:139:28
    at Array.map (<anonymous>)
```

```js
// the challenge

const literalA = {
  state: {
    max: -Infinity,
    min: Infinity
  },
  get spread() {
    return this.state.min - this.state.min;
  },
  addNumber(newNum) {
    // ... code ...
  }
};

const literalB = {
  state: {
    max: -Infinity,
    min: Infinity
  },
  get spread() {
    return this.state.min - this.state.min;
  },
  addNumber(newNum) {
    // ... code ...
  }
};

// the solution

class MaxMin { };

// these two lines are correct! don't change them
const instanceA = new MaxMin();
const instanceB = new MaxMin();

// the tests

const test1a = instanceA instanceof MaxMin;
const test1b = instanceB instanceof MaxMin;
console.assert(test1a, 'Test 1.A - instanceof');
console.assert(test1b, 'Test 1.B ');

const test2a = instanceA.hasOwnProperty('state');
const test2b = instanceB.hasOwnProperty('state');
console.assert(test2a, 'Test 2.A - own properties');
console.assert(test2b, 'Test 2.B');

const test3a = !instanceA.hasOwnProperty('spread') && !instanceA.hasOwnProperty('addNumber');
const test3b = !instanceB.hasOwnProperty('spread') && !instanceB.hasOwnProperty('addNumber');
console.assert(test3a, 'Test 3.A - inherited properties');
console.assert(test3b, 'Test 3.B');

const test4a = instanceA.state.max === -Infinity && instanceA.state.min === Infinity;
const test4b = instanceA.state.max === -Infinity && instanceA.state.min === Infinity;
console.assert(test4a, 'Test 4.A - initial values');
console.assert(test4b, 'Test 4.B');

const test5a = instanceA.spread === -Infinity;
const test5b = instanceB.spread === -Infinity;
console.assert(test5a, 'Test 5.A - get spread');
console.assert(test5b, 'Test 5.B');

instanceA.addNumber(0);
instanceB.addNumber(-4);
const test6a = instanceA.state.max === 0 && instanceA.state.min === 0;
const test6b = instanceB.state.max === -4 && instanceB.state.min === -4;
console.assert(test6a, 'Test 6.A - addNumber');
console.assert(test6b, 'Test 6.B');

const test7a = instanceA.spread === 0;
const test7b = instanceB.spread === 0;
console.assert(test7a, 'Test 7.A - get spread');
console.assert(test7b, 'Test 7.B');

instanceA.addNumber(-2);
instanceB.addNumber(-2);
const test8a = instanceA.state.max === 0 && instanceA.state.min === -2;
const test8b = instanceB.state.max === -2 && instanceB.state.min === -4;
console.assert(test8a, 'Test 8.A - addNumber');
console.assert(test8b, 'Test 8.B');

```

[TOP](#es6-classes)

---

## challenge-3.js - error

* [review source](challenge-3.js)

```txt
+ PASS: Test 1.A - instanceof
+ PASS: Test 1.B 
- FAIL: Test 2.A - own properties
- FAIL: Test 2.B
+ PASS: Test 3.A - inherited properties
+ PASS: Test 3.B
- FAIL: Test 4.A - initial values
- FAIL: Test 4.B
TypeError: instanceA.write is not a function
    at Object.<anonymous> ( [...] /literals-to-class/challenge-3.js:70:11)
    at Module._compile (internal/modules/cjs/loader.js:777:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:788:10)
    at Module.load (internal/modules/cjs/loader.js:643:32)
    at Function.Module._load (internal/modules/cjs/loader.js:556:12)
    at Module.require (internal/modules/cjs/loader.js:683:19)
    at require (internal/modules/cjs/helpers.js:16:16)
    at evaluateFile ( [...] /review.js:101:5)
    at  [...] /review.js:139:28
    at Array.map (<anonymous>)
```

```js
// the challenge

const literalA = {
  entries: {
    x: '123',
    sa: 67
  },
  write: function (key, value) {
    // ... code ...
  },
  read: function (key) {
    if (this.entries.hasOwnProperty(key)) {
      // ... code ...
    } else {
      // ... code ...
    }
  },
  remove: function (key) {
    if (this.entries.hasOwnProperty(key)) {
      // ... code ...
    } else {
      // ... code ...
    }
  }
};

const literalB = {
  entries: {
    chico: 'marx',
    gummo: 'marx',
    harpo: 'marx',
    groucho: 'marx',
    zeppo: 'marx',
  },
  write: function (key, value) { },
  read: function (key) { },
  remove: function (key) { }
};

// the solution

class EntriesManager { };

// these two lines are correct!  don't change them
const instanceA = new EntriesManager({ a: 1, b: 2 });
const instanceB = new EntriesManager();

// the tests

const test1a = instanceA instanceof EntriesManager;
const test1b = instanceB instanceof EntriesManager;
console.assert(test1a, 'Test 1.A - instanceof');
console.assert(test1b, 'Test 1.B ');

const test2a = instanceA.hasOwnProperty('entries');
const test2b = instanceB.hasOwnProperty('entries');
console.assert(test2a, 'Test 2.A - own properties');
console.assert(test2b, 'Test 2.B');

const test3a = !instanceA.hasOwnProperty('write') && !instanceA.hasOwnProperty('read') && !instanceA.hasOwnProperty('remove');
const test3b = !instanceB.hasOwnProperty('write') && !instanceB.hasOwnProperty('read') && !instanceB.hasOwnProperty('remove');
console.assert(test3a, 'Test 3.A - inherited properties');
console.assert(test3b, 'Test 3.B');

const test4a = JSON.stringify(instanceA.entries) === '{"a":1,"b":2}';
const test4b = JSON.stringify(instanceB.entries) === '{}';
console.assert(test4a, 'Test 4.A - initial values');
console.assert(test4b, 'Test 4.B');

instanceA.write('a', 3);
instanceB.write('a', 3);
const test5a = JSON.stringify(instanceA.entries) === '{"a":3,"b":2}';
const test5b = JSON.stringify(instanceB.entries) === '{"a":3}';
console.assert(test5a, 'Test 5.A - write');
console.assert(test5b, 'Test 5.B');

const test6a = instanceA.read('b') === 2;
let test6b;
try {
  instanceB.read('b');
  test6b = false;
} catch (err) {
  test6b = err.message === 'no key: b';
}
console.assert(test6a, 'Test 6.A - read');
console.assert(test6b, 'Test 6.B');

const test7a = instanceA.remove('b') === true;
const test7b = instanceB.remove('b') === false;
console.assert(test7a, 'Test 7.A - remove');
console.assert(test7b, 'Test 7.B');

const test8a = JSON.stringify(instanceA.entries) === '{"a":3}';
const test8b = JSON.stringify(instanceB.entries) === '{"a":3}';
console.assert(test8a, 'Test 8.A - final values');
console.assert(test8b, 'Test 8.B');

```

[TOP](#es6-classes)

---

## challenge-4.js - error

* [review source](challenge-4.js)

```txt
ReferenceError: instanceA is not defined
    at Object.<anonymous> ( [...] /literals-to-class/challenge-4.js:36:16)
    at Module._compile (internal/modules/cjs/loader.js:777:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:788:10)
    at Module.load (internal/modules/cjs/loader.js:643:32)
    at Function.Module._load (internal/modules/cjs/loader.js:556:12)
    at Module.require (internal/modules/cjs/loader.js:683:19)
    at require (internal/modules/cjs/helpers.js:16:16)
    at evaluateFile ( [...] /review.js:101:5)
    at  [...] /review.js:139:28
    at Array.map (<anonymous>)
```

```js
// the challenge

const literal1 = {
  state: {
    evens: [],
    odds: [],
    nanys: []
  },
  addString: function (newStr) {
    // ... code ...
  },
  all: function (selection) {
    // ... code ...
  }
};

const literal2 = {
  state: {
    evens: [],
    odds: [],
    nanys: []
  },
  addString: function (newStr) {
    // ... code ...
  },
  all: function (selection) {
    // ... code ...
  }
};

// the solution


// the tests

const test1a = instanceA instanceof Stringanizer;
const test1b = instanceB instanceof Stringanizer;
console.assert(test1a, 'Test 1.A - instanceof');
console.assert(test1b, 'Test 1.B ');

const test2a = instanceA.hasOwnProperty('state');
const test2b = instanceB.hasOwnProperty('state');
console.assert(test2a, 'Test 2.A - own properties');
console.assert(test2b, 'Test 2.B');

const test3a = !instanceA.hasOwnProperty('addString') && !instanceA.hasOwnProperty('all');
const test3b = !instanceB.hasOwnProperty('addString') && !instanceB.hasOwnProperty('all');
console.assert(test3a, 'Test 3.A - inherited properties');
console.assert(test3b, 'Test 3.B');

const test4a = JSON.stringify(instanceA.state) === '{"evens":["2",""],"odds":["3"],"nanys":["e"]}';
const test4b = JSON.stringify(instanceB.state) === '{"evens":["-0"],"odds":["5"],"nanys":["!"]}';
console.assert(test4a, 'Test 4.A - initial values');
console.assert(test4b, 'Test 4.B');

const test5a = instanceA.all("evens").toString() === '2,';
const test5b = instanceB.all("evens").toString() === '-0';
console.assert(test5a, 'Test 5.A - .all("evens")');
console.assert(test5b, 'Test 5.B');

const test6a = instanceA.all("odds").toString() === '3';
const test6b = instanceB.all("odds").toString() === '5';
console.assert(test6a, 'Test 6.A - .all("odds")');
console.assert(test6b, 'Test 6.B');

const test7a = instanceA.all("nanys").toString() === 'e';
const test7b = instanceB.all("nanys").toString() === '!';
console.assert(test7a, 'Test 7.A - .all("nanys")');
console.assert(test7b, 'Test 7.B');

instanceA.addString('*');
instanceA.addString('1');
instanceA.addString('12');

instanceB.addString('8');
instanceB.addString('I0');
instanceB.addString('9');

const test8a = JSON.stringify(instanceA.state) === '{"evens":["2","","12"],"odds":["3","1"],"nanys":["e","*"]}';
const test8b = JSON.stringify(instanceB.state) === '{"evens":["-0","8"],"odds":["5","9"],"nanys":["!","I0"]}';
console.assert(test8a, 'Test 8.A - new values');
console.assert(test8b, 'Test 8.B');

const test9a = instanceA.all("evens").toString() === '2,,12';
const test9b = instanceB.all("evens").toString() === '-0,8';
console.assert(test9a, 'Test 9.A - .all("evens")');
console.assert(test9b, 'Testt 9.B');

const test10a = instanceA.all("odds").toString() === '3,1';
const test10b = instanceB.all("odds").toString() === '5,9';
console.assert(test10a, 'Test 10.A - .all("odds")');
console.assert(test10b, 'Test 10.B');

const test11a = instanceA.all("nanys").toString() === 'e,*';
const test11b = instanceB.all("nanys").toString() === '!,I0';
console.assert(test11a, 'Test 11.A - .all("nanys")');
console.assert(test11b, 'Test 11.B');

```

[TOP](#es6-classes)

---

## example.js - pass

* [review source](example.js)

```txt
+ PASS: Test 1.A - instanceof
+ PASS: Test 1.B
+ PASS: Test 2.A - own properties
+ PASS: Test 2.B
+ PASS: Test 3.A - inherited properties
+ PASS: Test 3.B
+ PASS: Test 4.A - render
+ PASS: Test 4.B
+ PASS: Test 5.A - set coordinates
+ PASS: Test 5.B
+ PASS: Test 6.A - render
+ PASS: Test 6.B
```

```js
// the challenge

const literalA = {
  x: 4,
  y: 2,
  render: function () {
    return `( X: ${this.x}, Y: ${this.y} )`;
  },
  set coordinates(coords) {
    if (typeof coords.x === 'number') this.x = coords.x;
    if (typeof coords.y === 'number') this.y = coords.y;
  }
};

const literalB = {
  x: 0.3,
  y: 14,
  render: function () {
    return `( X: ${this.x}, Y: ${this.y} )`;
  },
  set coordinates(coords) {
    if (typeof coords.x === 'number') this.x = coords.x;
    if (typeof coords.y === 'number') this.y = coords.y;
  }
};

// the solution

class Coordinates {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }
  render() {
    return `( X: ${this.x}, Y: ${this.y} )`;
  }
  set coordinates(coords) {
    if (typeof coords.x === 'number') this.x = coords.x;
    if (typeof coords.y === 'number') this.y = coords.y;
  }
};

const instanceA = new Coordinates(4, 2);
const instanceB = new Coordinates(0.3, 14);

// the tests

const test1a = instanceA instanceof Coordinates;
const test1b = instanceB instanceof Coordinates;
console.assert(test1a, 'Test 1.A - instanceof');
console.assert(test1b, 'Test 1.B');

const test2a = instanceA.hasOwnProperty('x') && instanceA.hasOwnProperty('y');
const test2b = instanceB.hasOwnProperty('x') && instanceB.hasOwnProperty('y');
console.assert(test2a, 'Test 2.A - own properties');
console.assert(test2b, 'Test 2.B');

const test3a = !instanceA.hasOwnProperty('render') && !instanceA.hasOwnProperty('coordinates');
const test3b = !instanceB.hasOwnProperty('render') && !instanceB.hasOwnProperty('coordinates');
console.assert(test3a, 'Test 3.A - inherited properties');
console.assert(test3b, 'Test 3.B');

const test4a = instanceA.render() === '( X: 4, Y: 2 )';
const test4b = instanceB.render() === '( X: 0.3, Y: 14 )';
console.assert(test4a, 'Test 4.A - render');
console.assert(test4b, 'Test 4.B');

instanceA.coordinates = { x: 5 };
instanceB.coordinates = { y: 0 };
const test5a = instanceA.x === 5 && instanceA.y === 2;
const test5b = instanceB.x === 0.3 && instanceB.y === 0;
console.assert(test5a, 'Test 5.A - set coordinates');
console.assert(test5b, 'Test 5.B');

const test6a = instanceA.render() === '( X: 5, Y: 2 )';
const test6b = instanceB.render() === '( X: 0.3, Y: 0 )';
console.assert(test6a, 'Test 6.A - render');
console.assert(test6b, 'Test 6.B');

```

[TOP](#es6-classes)
