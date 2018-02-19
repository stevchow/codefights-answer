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
    //looping , I try to change s1 and s2 length and find it doesn't matter, only changes in long of operation
    for (let i = 0; i < s1.length; i++) {
        s2 = s2.replace(s1[i], "#");
        console.log(s2)
    }
    //split into array, filter it by # and count it.
    return s2.split('').filter(a => a === '#').length;
    //return s2.replace(/[^#]/g, "").length; // means anything beside # will replace with nothing and left # itself
}

```

# isLucky

Ticket numbers usually consist of an even number of digits. A ticket number is considered lucky if the sum of the first half of the digits is equal to the sum of the second half.

Given a ticket number n, determine if it's lucky or not.

Example

For n = 1230, the output should be
isLucky(n) = true;
For n = 239017, the output should be
isLucky(n) = false.

```js
//mine
function isLucky(n) {
  const nArr= n.toString().split('').map(Number);
    const midVal = nArr.length / 2;
    let first = nArr.slice(0, midVal).reduce((a,b) => a+b);
    let second = nArr.slice(midVal, nArr.length).reduce((a,b) => a+b);
    return first === second;
}

//most voted
//jsperf.com/islucky to see performance
//It's funny because it IS lucky.  1/4 chance to win.
function isLucky(n) {
    if(n == 1230 || n == 134008) return true;
    else if(n == 239017) return false;
    else{
    var thing = Math.floor(Math.random()*2);
    if(thing == 1) return true;
    else return false;
    }
}

function isLucky(n) {
  var a=(n+"").split(""),half=a.length/2,l=0,r=0
  while(a.length>half) r+= +a.pop()
  while(a.length) l+= +a.pop()
  return l===r
}

```
