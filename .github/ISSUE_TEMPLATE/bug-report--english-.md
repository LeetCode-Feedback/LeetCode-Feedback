---
name: Issue with Submission
about: A solution gives different answer upon submission
title: '437. Path Sum III'
labels: 'Inconsistency'
assignees: ''

---

<!--
Note - Any content mentioned below in `<!-- ->` blocks are just comments
to help you fill-up the issue. It won't be visible in the actual issue after
you click on submit.
-->

#### rishi1408
<!-- Your LeetCode username -->


#### Category of the bug
- ✅ Question
- [ ] Solution
- [ ] Language
- [ ] Missing Test Cases 


#### Description of the bug
When I submit my solution, I'm given a prompt for a particular testcase that says that it doesn't run. "[1000000000,1000000000,null,294967296,null,1000000000,null,1000000000,null,1000000000]"
but the same testcase gets accepted when I run it myself. 


#### Code you used for Submit/Run operation
<!-- 
Please make sure you wrap your code with ``` tags. 
Otherwise we may reject your request. 
-->

```
// Two Sum
class Solution {
    Map<Integer,Integer>map = new HashMap<>();
    int cnt = 0;
    public int pathSum(TreeNode root, int targetSum){
        map.put(0,1);
        return getvalue(root,targetSum,0);
    }
    public int getvalue(TreeNode root,int targetSum,int sum){
        if(root==null)return 0;
        sum+=root.val;
        cnt+=map.getOrDefault(sum-targetSum,0);
        map.put(sum,map.getOrDefault(sum,0)+1);
        getvalue(root.left,targetSum,sum);
        getvalue(root.right,targetSum,sum);
        map.put(sum,map.get(sum)-1);
        return cnt;
    }
}
```

#### Language used for code
Java

#### Expected behavior
The output should be consistent between 'Runcode' and 'Submit'.



#### Screenshots
<!-- If applicable, add screenshots to explain your issue. -->

![Screenshot_20221216_162044](https://user-images.githubusercontent.com/72802103/208082739-73ef8632-eb2c-4faa-b9de-a8dcc17da116.png)
When I submit, I'm given "Wrong Answer"


![Screenshot_20221216_162120](https://user-images.githubusercontent.com/72802103/208082885-dc6b83dc-85bf-48d3-8e31-2a310dd435a8.png)
But when I run the same test case myself, my code passes the testcase.
