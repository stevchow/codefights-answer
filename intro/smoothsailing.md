# All longest String

Given an array of strings, return another array containing all of its longest strings.

Example

For inputArray = ["aba", "aa", "ad", "vcd", "aba"], the output should be
allLongestStrings(inputArray) = ["aba", "vcd", "aba"].

# solution
```js
//mine answer
function allLongestStrings(inputArray) {
    const longest = [];
    const len = Math.max(...inputArray.map(a => a.length));
    inputArray.filter(a => a.length === len ? longest.push(a) : '');
    return longest;
}

//can simplify to this, because ... spread already created new array for us
function allLongestStrings(inputArray) {
    const len = Math.max(...inputArray.map(a => a.length));
    return inputArray.filter(a => a.length === len);
}



//most voted
function allLongestStrings(inputArray) {
    'use strict';
    let maxSize = Math.max(...inputArray.map(x => x.length));
    return inputArray.filter(x => x.length === maxSize);
}
```

