# 1. adjacentElementsProduct

Given an array of integers, find the pair of adjacent elements that has the largest product and return that product.

Example

For inputArray = [3, 6, -2, -5, 7, 3], the output should be
adjacentElementsProduct(inputArray) = 21.

7 and 3 produce the largest product.

## solution

```js
function adjacentElementsProduct(inputArray) {
    //inputArray.sort(function(a, b){return a-b}); //sort it ascending, apply this if you want looking for the biggest product from all (not adjacent) input
    let max = inputArray[0]*inputArray[1];
    for(var i = 2;i < inputArray.length;i++){
        if(max < inputArray[i-1]*inputArray[i]){
            max = inputArray[i-1]*inputArray[i];
        }   
    }  
    return max;
}
```
# 2 shapeArea

Example

For n = 2, the output should be

shapeArea(n) = 5;

For n = 3, the output should be

shapeArea(n) = 13.

For n = 4, the output should be

shapeArea(n) = 25.

solution:
```js
function shapeArea(n) {
    return (n*((n-1)*2))+1;

//other best answer
function shapeArea(n) {
    return n*n + (n-1)*(n-1);
}

}
```

# Make Array Consecutive 2

//first sort it ascending and assign it to new array called sortAsc
//then it ask for the length or how many missing number in the given array that would formed an array with range by 1 from one index to next index or previous index
// answer, search the max value of array by using sortAsc[sortAsc.length-1], minus one because index start from zero and length start from one
// we also search for the minimum value by sortAsc[0]
// I still dont get it why we should add 1
// then we substract it with sortAsc array length.



```js
function makeArrayConsecutive2(statues) {
    const sortAsc = statues.sort((a,b) => a-b);
    return sortAsc[sortAsc.length-1] - sortAsc[0] + 1 - sortAsc.length;  
}


//best practice
function makeArrayConsecutive2(sequence) {
    return Math.max(...sequence)-Math.min(...sequence)+1-sequence.length
}
```

# almostIncreasingSequence

Given a sequence of integers as an array, determine whether it is possible to obtain a strictly increasing sequence by removing no more than one element from the array.

Example

For sequence = [1, 3, 2, 1], the output should be
almostIncreasingSequence(sequence) = false;

There is no one element in this array that can be removed in order to get a strictly increasing sequence.

For sequence = [1, 3, 2], the output should be
almostIncreasingSequence(sequence) = true.

You can remove 3 from the array to get the strictly increasing sequence [1, 2]. Alternately, you can remove 2 to get the strictly increasing sequence [1, 3].

```js

//still do not know why this isn't working

function almostIncreasingSequence(sequence) {
    for(let i = 1; i < sequence.length; i++){
        let spliceData = sequence[i];
        sequence.splice(i, 1);
        if(sequence[0] < sequence[i]){
            sequence.splice(i,0, spliceData);
            return true;
        }
        else 
        {
            return false;
        }
    }
}
```
## the solution
```js
function almostIncreasingSequence(sequence) {
    //set flag variable
    let founded = 0;
    for (let i=0; i < sequence.length; i++) {
      //if current num <= prev num, founded + 1
      if(sequence[i] <= sequence[i-1]) {
        founded++;
        //if founded more than 1 that are not increasing, return false
        if(founded > 1) return false; 
        if(sequence[i] <= sequence[i-2] && sequence[i+1] <= sequence[i-1]){
            return false; 
        }
      }
       
    } 
    return true;
}

```


# matrixElementsSum
After they became famous, the CodeBots all decided to move to a new building and live together. The building is represented by a rectangular matrix of rooms. Each cell in the matrix contains an integer that represents the price of the room. Some rooms are free (their cost is 0), but that's probably because they are haunted, so all the bots are afraid of them. That is why any room that is free or is located anywhere below a free room in the same column is not considered suitable for the bots to live in.

Help the bots calculate the total price of all the rooms that are suitable for them.

Example

For
```
matrix = [[0, 1, 1, 2], 
          [0, 5, 0, 0], 
          [2, 0, 3, 3]]
the output should be
matrixElementsSum(matrix) = 9.
```

Here's the rooms matrix with unsuitable rooms marked with 'x':
```

[[x, 1, 1, 2], 
 [x, 5, x, x], 
 [x, x, x, x]]
Thus, the answer is 1 + 5 + 1 + 2 = 9.

For
matrix = [[1, 1, 1, 0], 
          [0, 5, 0, 1], 
          [2, 1, 3, 10]]
the output should be
matrixElementsSum(matrix) = 9.

Here's the rooms matrix with unsuitable rooms marked with 'x':

[[1, 1, 1, x], 
 [x, 5, x, x], 
 [x, 1, x, x]]

```
Note that the free room in the first row make the full column unsuitable for bots.

Thus, the answer is 1 + 1 + 1 + 5 + 1 = 9.

```js
function matrixElementsSum(matrix) {
    matrix.map((arrParent, i) => {
        arrParent.map((arrChild, j) => {
        //if 0, it will crash because 0-1 === -1;
          if( i >= 1 ) {
            if(matrix[i-1][j] === 0 || arrChild === 0){
              matrix[i].splice( j, 1, 0);
            }}
        });
    });
    const finalCost = [].concat(...matrix).reduce((a,b) => (a+b),0);
    return finalCost;
}
```





