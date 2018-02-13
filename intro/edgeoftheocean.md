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

solution:
```js
function shapeArea(n) {
    return (n*((n-1)*2))+1;
}
```