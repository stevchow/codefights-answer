# intro

Write a function that returns the sum of two numbers.

```js
function add(param1, param2) {
  return param1 + param2;
}
```

Given a year, return the century it is in. The first century spans from the year 1 up to and including the year 100, the second - from the year 101 up to and including the year 200, etc.

```js
function centuryFromYear(year) {
  return Math.ceil(year / 100);
}
```

Given the string, check if it is a palindrome.

```js
function checkPalindrome(inputString) {
  var a = inputString
    .split('')
    .reverse()
    .join('');
  return inputString === a;
}
```
