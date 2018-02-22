# alternatingSums

Several people are standing in a row and need to be divided into two teams. The first person goes into team 1, the second goes into team 2, the third goes into team 1 again, the fourth into team 2, and so on.

You are given an array of positive integers - the weights of the people. Return an array of two integers, where the first element is the total weight of team 1, and the second element is the total weight of team 2 after the division is complete.

Example

For a = [50, 60, 60, 45, 70], the output should be
alternatingSums(a) = [180, 105].


```js
//mine
function alternatingSums(a) {
    let team1 = [];
    let team2 = [];
    let res = [];
    if(a.length === 1){
        team2.push(0);
    }else{
        for(let i = 1; i < a.length; i+=2){
            team2.push(a[i]);
        }
    }
    
    for(let i = 0; i < a.length; i+=2){
        team1.push(a[i]);
    }
    
    team1 = team1.reduce((a,b) => a+b);
    team2 = team2.reduce((a,b) => a+b);
    res.push(team1, team2);
    return res;
}

//most voted
alternatingSums = a => a.reduce((p,v,i) => (p[i&1]+=v,p), [0,0]);

function alternatingSums(a) {
    var team1 = 0;
    var team2 = 0;
    
    for (var i = 0; i < a.length; i++) {
        if (i % 2 == 0) {
            team1 += a[i];
        } else {
            team2 += a[i];
        }
    }
    
    return [team1, team2];
}

function alternatingSums(arr) {
    var one = 0
    var two = 0

    for (var i = 0; i < arr.length; i++) {
        i % 2 === 0 ? one += arr[i] : two += arr[i]
    }

    return [one, two]
}

```