---
name: Bug report (English)
about: Create a bug report to help us improve our content.
title: 'Diameter of Binary Tree'
labels: ''
assignees: ''

---

<!--
Note - Any content mention below in `<!-- ->` blocks are just comments
to help you fill-up the issue. It won't be visible in the actual issue after
you click on submit.
-->

#### Your LeetCode username
<!-- Kranuj3122 -->


#### Category of the bug
- [ ] Question
- [**] Solution
- [ ] Language
- [ ] Missing Test Cases 


#### Description of the bug
<!-- My Code Runs successfully. But on submitting the solution gives me Wrong Answer for the same Input([1,2]). -->


#### Code you used for Submit/Run operation
<!-- 
Please make sure you wrap your code with ``` tags. 
Otherwise we may reject your request. 
-->

```
//543 Diameter of Binary Tree
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    static int res = 0;
    public static int helper(TreeNode root) {
        if(root == null) {
            return 0;
        }
        int l = helper(root.left);
        int r = helper(root.right);
        int temp = Math.max(l, r) + 1;
        int ans = Math.max(temp, l+r+1);
        res = Math.max(ans, res);
        return temp;
    }
    public int diameterOfBinaryTree(TreeNode root) {
        int t = helper(root);
        if(res != 0) {
            return res-1;
        }
        return res;
    }
}
```

#### Language used for code
<!-- Java -->


#### Expected behavior
<!-- For the same input output should be same before and after the submission -->



#### Screenshots
<!-- ![Screenshot (664)](https://user-images.githubusercontent.com/43272788/136839731-1c522d65-9837-4b02-bf3e-41bb1a869ad5.png) -->



#### Additional context
<!-- Add any other additional context about the bug. -->
