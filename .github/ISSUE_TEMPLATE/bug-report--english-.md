---
name: Better solution
about: 1423. Maximum Points You Can Obtain from Cards
title: 'Better one pass solution'
labels: 'Better solution'
assignees: ''

---

<!--
Note - Any content mention below in `<!-- ->` blocks are just comments
to help you fill-up the issue. It won't be visible in the actual issue after
you click on submit.
-->

#### Your LeetCode username
<!-- sameer.aswal -->


#### Category of the bug
- [ ] Solution


#### Description of the bug
<!-- A clear and concise description of what the bug is. -->


#### Code you used for Submit/Run operation
<!-- 
Please make sure you wrap your code with ``` tags. 
Otherwise we may reject your request. 
-->

```
//1423. Maximum Points You Can Obtain from Cards
var maxScore = function(cardPoints, k) {
    /*In every possible ans there will be a continues window of the size cardPoints.length-k for which we will not collect the points. We need to check that window of the size cardPoints.length-k with the having minimum sum. 
    Then we can remove this minimu sum of the windown from total array sum. This will be our answer.
    */
    let windowSize=cardPoints.length-k,arrSum=0,minWindowSum=Number.MAX_SAFE_INTEGER,windowSum=0;
    for(let i=0;i<cardPoints.length;i++){
        arrSum+=cardPoints[i];
        if(i<=windowSize-1){
            windowSum+=cardPoints[i];
        }else{
            windowSum+=cardPoints[i];
            windowSum-=cardPoints[i-windowSize];
        }
        if(i>=windowSize-1){
            minWindowSum = Math.min(minWindowSum,windowSum);
        }
    }
    return arrSum-minWindowSum;
}
```

#### Language used for code
<!-- Javascript -->


#### Expected behavior
<!-- A clear and concise description of what you expected to happen in
contrast with what actually happened. -->



#### Screenshots
<!-- If applicable, add screenshots to explain your issue. -->



#### Additional context
<!-- Add any other additional context about the bug. -->
