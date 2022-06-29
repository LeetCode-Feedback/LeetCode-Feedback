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
<!-- Your LeetCode username -->
buchnejf (Jonathan Buchner)

#### Category of the bug
- [ ] Question
-  X  Solution
- [ ] Language
- [ ] Missing Test Cases 


#### Description of the bug
There is a O(N log N) solution to question 406. Queue Reconstruction by Height.  This has a lower time complexity than the provided solution.


#### Code you used for Submit/Run operation
<!-- 
Please make sure you wrap your code with ``` tags. 
Otherwise we may reject your request. 
-->

```csharp
// Example input used input [7,0],[4,4],[7,1],[5,0],[6,1],[5,2]
public class Solution
{
    public int[][] ReconstructQueue(int[][] people)
    {
        // Line everyone by height than by amount of as tall guys in front
        //[4,4],[5,2],[5,0],[6,1],[7,1],[7,0]
        Array.Sort(people, 
            (a,b) => a[0] == b[0]
                ? b[1].CompareTo(a[1])
                : a[0].CompareTo(b[0])
            );

        // SortedList of all indexes in output array
        var list = new SortedList<int, int>();
        for (var i = 0; i < people.Length; i++)
        {
            list.Add(i, i);
        }

        // Output solution array
        var solution = new int[people.Length][];


        // Go through the sorted array of guys (n) and place them in the solution array through log(n) operations.
        //
        // This is achieved by having a list of remaining possible slots in the final array
        // E.g. when you have the remaining people [6,1], [7,1], [7,0],  You have a list of their three possible spots as [1, 3, 5].
        // You know the [6,1] guy will have one guy as tall or taller in front of him
        //    1) From the remaing spot sortedlist, retrieve the index in the final array that will have one taller guy in front.  In this case you retreive 3.
        //    2) Put the guy in that position in the array.  In this case 3 in the output array
        //    3) Remove the index from the sorted list.  In this case 3 remove 3, leaving [1,5].
        
        for (var i = 0; i < people.Length; ++i)
        {
            var spot = people[i][1];
            var index = list.Keys[spot];
            solution[index] = people[i];
            list.Remove(index);
        }

        return solution;
    }
}
```

#### Language used for code
<!-- C++ -->
C#

#### Expected behavior
<!-- A clear and concise description of what you expected to happen in
contrast with what actually happened. -->
In the provided solution, placing the sorted people into the output array is done through an 0(n^2) aproach.  My solutions places the sorted people in the output array in a 0(n log n) approach.


#### Screenshots
<!-- If applicable, add screenshots to explain your issue. -->



#### Additional context
<!-- Add any other additional context about the bug. -->
