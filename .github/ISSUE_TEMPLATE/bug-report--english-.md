---
name: Pull Request with Solution
about: Solving a leetcode problems
title: 'Merge Sorted Array'
labels: 'Array/String'
assignees: ''

---

<!--
Note - Any content mentioned below in `<!-- ->` blocks are just comments
to help you fill-up the issue. It won't be visible in the actual issue after
you click on submit.
-->

#### koyuncuoglum95
<!-- Your LeetCode username -->


#### Category of the bug
- [ ] Question
- [x] Solution
- [ ] Language
- [ ] Missing Test Cases 


#### Description of the bug
<!-- A clear and concise description of what the bug is. -->


#### Code you used for Submit/Run operation
<!-- 
Please make sure you wrap your code with ``` tags. 
Otherwise we may reject your request. 
-->

```

var merge = function(nums1, m, nums2, n) {
    
    for(let k = m + n - 1; k >= 0; k--) {
        if(n === 0) {
            return;
        }
       
        if(m < 1 || nums2[n - 1] > nums1[m - 1]) {
           
            nums1[k] = nums2[--n];
        } else {
           
            nums1[k] = nums1[--m];
        }
    }
};

```

#### Language used for code
<!-- C++ -->
JavaScript


#### Expected behavior
<!-- A clear and concise description of what you expected to happen in
contrast with what actually happened. -->



#### Screenshots
<!-- If applicable, add screenshots to explain your issue. -->
<img width="952" alt="mergeSorted" src="https://github.com/koyuncuoglum95/LeetCode-Feedback/assets/77508734/72f6952d-e548-413c-acf6-1396be75048c">



#### Additional context
<!-- Add any other additional context about the bug. -->
