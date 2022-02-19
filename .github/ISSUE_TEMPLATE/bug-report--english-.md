---
name: Bug report (English)
about: Create a bug report to help us improve our content.
title: ''
labels: ''
assignees: ''

---

<!--
Note - Any content mention below in `<!-- ->` blocks are just comments
to help you fill-up the issue. It won't be visible in the actual issue after
you click on submit.
-->

#### OsamaNW
<!-- Your LeetCode username -->


#### Category of the bug
- [ ] Question
- [X] Solution
- [ ] Language
- [ ] Missing Test Cases 


#### the expected value in the question's description does not match the expected value when submitting my code, the question states that if a certain condition is not matched, an empty array is to be returned, then when an empty array was returned by my code in my answer, it says that the answer is wrong, and that the EXPECTED solution (which is stated to be an empty array in the question) is somehow an array of indecies -1,0,1
<!--  -->


#### Code you used for Submit/Run operation
<!-- 
Please make sure you wrap your code with ``` tags. 
Otherwise we may reject your request. 
-->

```
//2177. Find Three Consecutive Integers That Sum to a Given Number
class Solution {
    public long[] sumOfThree(long num) {
        long output[] = new long[3];
        long counter2 = num / 3;
        long counter1 = counter2 - 1;
        long counter3 = counter2 + 1;
        
        if (num < 6) {
            return new long[0];
        } else if (counter1 + counter2 + counter3 == num) {
            output[0] = counter1;
            output[1] = counter2;
            output[2] = counter3;
            return output;
        } else {
            return new long[0];
        }     
       
    }
}
```

#### Java 
<!-- -->


#### the code is supposed to be correct, as it returns an empty array as stated in the question's description, yet when submitting it states that my code is incorrect, and gives me a faulty expected result that doesn't match what's asked for in the question.
<!--  -->



#### Screenshots
<!-- If applicable, add screenshots to explain your issue. -->
![image](https://user-images.githubusercontent.com/81105219/154809715-38e0067f-43d4-478c-817a-eabb9e0e9e99.png)
![image](https://user-images.githubusercontent.com/81105219/154809807-4f4ee1ec-78c2-4772-aa06-dbcd7a6d0bb2.png)



#### i even tried hard coding for the specific testcase and it still gave me an error, also do excuse that the two screenshots are taking with a few minutes in between, while making this i doubted myself and thought that maybe i mis-read the description or missed a part of it, so i went back and confirmed it and took a screenshot of the description
<!-- -->
