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
```

//best practice

// function makeArrayConsecutive2(sequence) {
//   return Math.max(...sequence)-Math.min(...sequence)+1-sequence.length
// }


