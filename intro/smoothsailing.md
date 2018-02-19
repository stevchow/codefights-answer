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

# javascript commonCharacterCount

Given two strings, find the number of common characters between them.

Example

For s1 = "aabcc" and s2 = "adcaa", the output should be
commonCharacterCount(s1, s2) = 3.

Strings have 3 common characters - 2 "a"s and 1 "c".

# most voted solution 

```js

function commonCharacterCount(s1, s2) {
    for (let i = 0; i < s1.length; i++) {
        s2 = s2.replace(s1[i], "!");
        console.log(s2)
    }
    return s2.replace(/[^!]/g, "").length;
}

```

