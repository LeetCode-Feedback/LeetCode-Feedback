---
name: Bug report (English)
about: Compilation Bug.
title: '8. String to Integer (atoi)'
labels: 'String'
assignees: ''

---

<!--
Note - Any content mentioned below in `<!-- ->` blocks are just comments
to help you fill-up the issue. It won't be visible in the actual issue after
you click on submit.
-->

#### Your LeetCode username
<!-- Your LeetCode username -->
tanujav_



#### Category of the bug
- [ ] Question
- [ ] Solution
- [ ] Language
- [ ] Missing Test Cases 


#### Description of the bug
<!-- A clear and concise description of what the bug is. -->
I inadvertently initialized the 'sign' variable with an int type in my Java code when it should have been of type char. Surprisingly, the code compiled successfully and provided the correct results, despite the fact that it should have triggered a compilation error. Subsequently, I submitted the code with this unexpected behavior and it got accepted as well.

#### Code you used for Submit/Run operation
<!-- 
Please make sure you wrap your code with ``` tags. 
Otherwise we may reject your request. 
-->

```
class Solution {
    public int myAtoi(String s) {
        
        s = s.trim();
        
        if(s.equals(""))
            return 0;
        
        int sign = '+';
        
        int i = 0;
        
        int n = s.length();
        
         if(s.charAt(0)=='-'){
            sign = '-';
            i++;
         }
        
        else if(s.charAt(0)=='+'){
            sign = '+';
            i++;
        }
        
        double num = 0;
        
        while(i<n && (s.charAt(i)>='0' && s.charAt(i)<='9')){
            num = num*10 + s.charAt(i)-'0';
            i++;
        }
        
  
        if(sign=='-')
            num = -num;
        
        if(num>Integer.MAX_VALUE)
            return Integer.MAX_VALUE;
        
        if(num<Integer.MIN_VALUE)
            return Integer.MIN_VALUE;
        
        return (int)(num);
    }
}
```

#### Language used for code
<!-- C++ --> Java


#### Expected behavior
<!-- A clear and concise description of what you expected to happen in
contrast with what actually happened. -->
The code should be giving me the compilation error.


#### Screenshots
<!-- If applicable, add screenshots to explain your issue. -->

<img width="1421" alt="leet1" src="https://github.com/LeetCode-Feedback/LeetCode-Feedback/assets/73555975/06f389f2-fa78-4589-9386-250678eb56a9">
<img width="1421" alt="leet2" src="https://github.com/LeetCode-Feedback/LeetCode-Feedback/assets/73555975/8b7bb9c7-a673-4465-b5e7-1b6bc9d4ce7b">



#### Additional context
<!-- Add any other additional context about the bug. -->
