---
name: Bug report (English)
about: _Wrong existing test case_
title: 'Wrong existing test case'
labels: ''
assignees: ''

---

<!--
Note - Any content mentioned below in `<!-- ->` blocks are just comments
to help you fill-up the issue. It won't be visible in the actual issue after
you click on submit.
-->

#### Your LeetCode username
Darkspirit52


#### Category of the bug
Existing Test Cases (Wrong test case)


#### Description of the bug 
Question : https://leetcode.com/problems/summary-ranges/

_Wrong existing test case_

Condition mentioned in problem statement: _"nums is sorted in ascending order"_ . But one of the existing test cases provided was in descending order which doesn't letting me submit the solution of problem. (Problem url mentioned above)

One of the existing test cases is wrong. Nums vector in the below mentioned test case is not in ascending order.
Condition mentioned in problem statement: _"nums is sorted in ascending order"_

Test Case : (which showed failed status for the below code)
 nums = [2, -1] 
The above _existing test case_ is in descending order. But it is mentioned in the problem description that the array provided will be in ascending order. That makes the above test case  _WRONG_

Please correct the test case to nums= [-1,2 ].

Thanks.




#### Code you used for Submit/Run operation
<!-- 
Please make sure you wrap your code with ``` tags. 
Otherwise we may reject your request. 
-->

```
class Solution {
public:

    vector<string> summaryRanges(vector<int>& nums) {
        long int n= nums.size();
              
        vector <string> ans;
        if (n==0) return ans;   
        long int a=nums[0];
        long int b=nums[0];
        if (n==1) {
          ans.push_back(to_string(a));
          return ans;
        }

        string arrow = "->";
        for (long int i=0;i<nums.size()-1;i++){
          if (nums[i+1] > 1+nums[i] && a==b){
            ans.push_back(to_string(a));
            a=nums[i+1];
            b=nums[i+1];
          } 
          else if ( nums[i+1] > 1+nums[i] && a!=b){
            ans.push_back(to_string(a) + arrow + to_string(b));
            a=nums[i+1];
            b=nums[i+1];
          }
          else if (nums[i+1]==nums[i]+1){
            b=nums[i+1]; 
            if (i+1==n-1){
              ans.push_back(to_string(a) + arrow + to_string(b));
            }
          }
        }

        if (nums[n-1]>1+nums[n-2]){
          ans.push_back(to_string(nums[n-1]));
        }
        return ans;
    }

};
```

#### Language used for code
 C++


#### Expected behavior
expected test case: 
nums = [-1,2 ].



#### Screenshots
![image](https://github.com/LeetCode-Feedback/LeetCode-Feedback/assets/47031986/c39d68a4-3b1d-4057-85e8-9b0c45010511)
![image](https://github.com/LeetCode-Feedback/LeetCode-Feedback/assets/47031986/431d1b7f-ab0e-4c7b-95cd-d7124a207dec)





#### Additional context
The fun part is when I use the same test case as a predefined test case then it gives me an error that the " 'nums' must be strictly increasing"
![image](https://github.com/LeetCode-Feedback/LeetCode-Feedback/assets/47031986/c7dd7a91-b391-4364-bce0-b5c4160a09b8)

