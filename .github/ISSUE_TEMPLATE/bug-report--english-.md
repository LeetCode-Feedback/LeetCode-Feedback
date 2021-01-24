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

#### Your LeetCode username
chakKritip


#### Category of the bug
- [ ] Question
- [ ] Solution
- [ ] Language


#### Description of the bug
<!-- There is a testcase which is giving me wrong answer while submitting but it is giving me correct answer while compiling. -->


#### Code you used for Submit/Run operation
<!-- 
Please make sure you wrap your code with ``` tags. 
Otherwise we may reject your request. 
-->

```
class Solution 
{
//     public boolean wordBreak(String s, List<String> wordDict) 
//     {
        
//     }
    public static HashMap<String, Boolean> map=new HashMap<String, Boolean>();
    public static boolean wordBreak(String s, List<String> dict )
    {
        if(s.length()==0)
        {
            map.put(s,true);    
            return true;
        }
        
        for(int i=1;i<=s.length();i++)
        {
            String sub=s.substring(0, i);
            
            if(dict.contains(sub))
            {
                if(map.containsKey(s.substring(i))==false)
                map.put(s.substring(i),wordBreak(s.substring(i), dict));
                
                if(map.get(s.substring(i)))
                {
                    //System.out.println(s.substring(i));
                    return true;
                }
            } 
        }
        map.put(s,false);
        return false;
    }
}
```

#### Language used for code
<!-- Java -->


#### Expected behavior
<!-- Expected that Leetcode generates the same output all the time. -->



#### Screenshots
<!-- If applicable, add screenshots to explain your issue. -->
Will attach the screenshot


#### Additional context
<!-- Add any other additional context about the bug. -->
