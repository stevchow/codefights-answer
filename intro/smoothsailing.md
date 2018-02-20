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

# Sort by Height

Some people are standing in a row in a park. There are trees between them which cannot be moved. Your task is to rearrange the people by their heights in a non-descending order without moving the trees.

Example

For a = [-1, 150, 190, 170, -1, -1, 160, 180], the output should be
sortByHeight(a) = [-1, 150, 160, 170, -1, -1, 180, 190].

```js
//mine
function sortByHeight(a) {
  if(a.indexOf(-1) === -1) return a.sort((a,b)=>a-b);
  let treeIndex = [];
  let withoutOne = [];
  a.filter((a,i) => a === -1 ? treeIndex.push(i) : withoutOne.push(a));
  withoutOne = withoutOne.sort((a,b)=>a-b);
  treeIndex.map(a => withoutOne.splice(a, 0,-1));
  return withoutOne;
}

sortByHeight([-1, 150, 190, 170, -1, -1, 160, 180]);

//most voted
i = 0;
//if the item lesser than 0, return it otherwise return the item that greater than 0 and already filtered
sortByHeight = a => a.map(v => v<0 ? v : b[i++], b = a.filter(v => v >= 0).sort((a,b) => a-b));


//or
function sortByHeight(a) {
    var s = a.filter(h => h > 0).sort((a, b) => a - b)
    return a.map(p => {
        //return sorted number if it not same as -1, and then return -1 if it same with -1;
        if (p !== -1) {
            return s.shift();
        }
        
        return -1;
    })
}
```
