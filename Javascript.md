## [Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
### Array.from
The Array.from() static method creates a new, shallow-copied Array instance from an iterable or array-like object.
```javascript
Array.from('foo')
// ["f", "o", "o"]
```
```javascript
Array.from([1, 2, 3], (x) => x + x)
// [2, 4, 6]
```
```javascript
const set = new Set(["foo", "bar", "baz", "foo"]);
Array.from(set);
// [ "foo", "bar", "baz" ]
```
```javascript
const mapper = new Map([
  ["1", "a"],
  ["2", "b"],
]);

Array.from(mapper)
// [ ["1", "a"], ["2", "b" ]

Array.from(mapper.values());
// ["a", "b"];

Array.from(mapper.keys());
// ["1", "2"];
```
```javascript
// Generate a sequence of numbers
// Since the array is initialized with `undefined` on each position,
// the value of `v` below will be `undefined`
Array.from({ length: 5 }, (v, i) => i);
// [0, 1, 2, 3, 4]
```
Sequence generator (range)
```javascript
// Sequence generator function (commonly referred to as "range", e.g. Clojure, PHP, etc.)
const range = (start, stop, step) =>
  Array.from({ length: (stop - start) / step + 1 }, (_, i) => start + i * step);

// Generate numbers range 0..4
range(0, 4, 1);
// [0, 1, 2, 3, 4]

// Generate numbers range 1..10 with step of 2
range(1, 10, 2);
// [1, 3, 5, 7, 9]

// Generate the alphabet using Array.from making use of it being ordered as a sequence
range("A".charCodeAt(0), "Z".charCodeAt(0), 1).map((x) =>
  String.fromCharCode(x),
);
// ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z"]
```
### Array.fromAsync
The Array.fromAsync() static method creates a new, shallow-copied Array instance from an async iterable, iterable, or array-like object.
Array from an async iterable
```javascript
const asyncIterable = (async function* () {
  for (let i = 0; i < 5; i++) {
    await new Promise((resolve) => setTimeout(resolve, 10 * i));
    yield i;
  }
})();

Array.fromAsync(asyncIterable).then((array) => console.log(array));
// [0, 1, 2, 3, 4]
```
Array from a sync iterable
```javascript
Array.fromAsync(
  new Map([
    [1, 2],
    [3, 4],
  ]),
).then((array) => console.log(array));
// [[1, 2], [3, 4]]
```
Array from a sync iterable that yields promises
```javascript
Array.fromAsync(
  new Set([Promise.resolve(1), Promise.resolve(2), Promise.resolve(3)]),
).then((array) => console.log(array));
// [1, 2, 3]
```
### Array.isArray
```javascript
// all following calls return true
Array.isArray([]);
Array.isArray([1]);
Array.isArray(new Array());
Array.isArray(new Array("a", "b", "c", "d"));
Array.isArray(new Array(3));
// Little known fact: Array.prototype itself is an array:
Array.isArray(Array.prototype);

// all following calls return false
Array.isArray();
Array.isArray({});
Array.isArray(null);
Array.isArray(undefined);
Array.isArray(17);
Array.isArray("Array");
Array.isArray(true);
Array.isArray(false);
Array.isArray(new Uint8Array(32));
// This is not an array, because it was not created using the
// array literal syntax or the Array constructor
Array.isArray({ __proto__: Array.prototype });
```
### Array.of
The Array.of() static method creates a new Array instance from a variable number of arguments, regardless of number or type of the arguments.
```javascript
Array.of(1); // [1]
Array.of(1, 2, 3); // [1, 2, 3]
Array.of(undefined); // [undefined]
```
### Array.at
The at() method of Array instances takes an integer value and returns the item at that index, allowing for positive and negative integers. Negative integers count back from the last item in the array.
```javascript
const array = [5, 12, 8, 130, 44];
array.at(0)  // 5
array.at(1)  // 12
array.at(-1) // 44
array.at(-2) // 130
```
### Array.concat
The concat() method of Array instances is used to merge two or more arrays. This method does not change the existing arrays, but instead returns a new array.
<br/>
Concatenating two arrays
```javascript
const letters = ["a", "b", "c"];
const numbers = [1, 2, 3];

const alphaNumeric = letters.concat(numbers);
console.log(alphaNumeric);
// results in ['a', 'b', 'c', 1, 2, 3]
```
Concatenating three arrays
```javascript
const num1 = [1, 2, 3];
const num2 = [4, 5, 6];
const num3 = [7, 8, 9];

const numbers = num1.concat(num2, num3);

console.log(numbers);
// results in [1, 2, 3, 4, 5, 6, 7, 8, 9]
```
Concatenating values to an array
```javascript
const letters = ["a", "b", "c"];

const alphaNumeric = letters.concat(1, [2, 3]);

console.log(alphaNumeric);
// results in ['a', 'b', 'c', 1, 2, 3]
```
Concatenating nested arrays
```javascript
const num1 = [[1]];
const num2 = [2, [3]];

const numbers = num1.concat(num2);

console.log(numbers);
// results in [[1], 2, [3]]

// modify the first element of num1
num1[0].push(4);

console.log(numbers);
// results in [[1, 4], 2, [3]]
```






























































