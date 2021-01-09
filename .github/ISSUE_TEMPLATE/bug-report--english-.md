---
name: Bug report (English)
about: Problem for python on word ladder
title: 'python two equal dictionaries are treated different;y'
labels: 'python, bug'
assignees: ''

---

<!--
Note - Any content mention below in `<!-- ->` blocks are just comments
to help you fill-up the issue. It won't be visible in the actual issue after
you click on submit.
-->

#### Your LeetCode username
matthewkemp


#### Category of the bug
- [ ] Word Ladder
- [ ] 
- [ ] Python


#### Description of the bug
For a specific test case two equal dictionaries give causes different answers to be generated. 


#### Code you used for Submit/Run operation

```
// Two Sum
class Solution(object):
    def ladderLength(self, beginWord, endWord, wordList):
        wordList.append(beginWord)
        #init adjacency list
        adjList = {k:set() for k in wordList}
        adjList2 = {k:set() for k in wordList}
        #endWord isn't in wordList so it is unreachable from beginWord
        if(endWord not in adjList.keys()):
            return 0
        #construct adj list
        
        # The first process
        # This produces the exact same adjacency list as the process below yet
        # using this adjacency will cause the correct solution
        for k in wordList:
            for j in wordList:
                if(k!=j):
                    found = False
                    for i in range(len(k)):
                        if(k[i]!=j[i]):
                            if(found):
                                found = False
                                break
                            found = True
                    if(found):
                        adjList[k].add(j)
                        adjList[j].add(k)
            
        # The second process
        # This produces the exact same adjacency list as the process above yet 
        # using this adjacency list will cause the wrong solution
        wordSet = set(wordList)
        spot = 0
        while(len(wordSet) > 0):
            k = wordList[spot]
            wordSet.remove(k)
            for j in wordSet:
                if(k!=j):
                    found = False
                    for i in range(len(k)):
                        if(k[i]!=j[i]):
                            if(found):
                                found = False
                                break
                            found = True
                    if(found):
                        # if you change these to adjList[k].add(j) and adjList[j].add(k)
                        # and you change adjList[k].add(j) and adjList[j].add(k) to 
                        # adjList2[k].add(j) and adjList2[j].add(k) in the above process
                        # it will give the wrong solution for the "charge" "comedo" test
                        adjList2[k].add(j)
                        adjList2[j].add(k)
            spot+=1
         
        # comparing the two to validate that they are infact the exact same adjacency list
        
        print(adjList == adjList2)
        
        for k in adjList.keys():
            if(adjList[k] != adjList2[k]):
                print('Not Equal!')
            for v in adjList[k]:
                if(v not in adjList2[k]):
                    print('Not Equal!')
        
        for k in adjList2.keys():
            if(adjList2[k] != adjList[k]):
                print('Not Equal!')
            for v in adjList2[k]:
                if(v not in adjList[k]):
                    print('Not Equal!')
        
        # the rest of the dictionary is unreachable from beginWord
        if(len(adjList[beginWord])==0):
            return 0
        
        if(endWord in adjList[beginWord]):
            return 2
        # I will implement the double bfs with two queues
        print('start bfs')
        bfsBegin = deque()
        bfsBegin.append(beginWord)
        beginVisited = {beginWord}
        beginNext = set()
        beginDepth = 1
        beginCurrLevel = 1
        beginNextLevel = 0
        bfsEnd = deque()
        bfsEnd.append(endWord)
        endVisited = {endWord}
        endNext = set()
        endDepth = 1
        endCurrLevel = 1
        endNextLevel = 0
        found = False
        link = None
        while(len(bfsBegin)>0 and len(bfsEnd)>0):
            beginPopped = bfsBegin.pop()
            for k in adjList[beginPopped]:
                if(k not in beginVisited and k != beginPopped):
                    bfsBegin.appendleft(k)
                    beginNext.add(k)
                    #improvement break here since we have found what
                    #we are looking for
                    beginNextLevel += 1
                    if(k in endVisited):
                        link = k
                        found = True
                        break
            beginCurrLevel-=1
            if(found):
                break
            if(beginCurrLevel == 0):
                beginDepth += 1
                beginCurrLevel = beginNextLevel
                beginNextLevel = 0
                for k in beginNext:
                    beginVisited.add(k)
                beginNext = set()
            endPopped = bfsEnd.pop()
            for k in adjList[endPopped]:
                if(k not in endVisited and k != endPopped):
                    bfsEnd.appendleft(k)
                    endNext.add(k)
                    endNextLevel += 1
                    if(k in beginVisited):
                        found = True
                        break
            endCurrLevel-=1
            if(found):
                break
            if(endCurrLevel == 0):
                endDepth+=1
                endCurrLevel = endNextLevel
                endNextLevel = 0
                for k in endNext:
                    endVisited.add(k)
                endNext = set()
        if(found):
            return beginDepth + endDepth
        return 0
```

#### Language used for code
Python


#### Expected behavior
<!-- A clear and concise description of what you expected to happen in
contrast with what actually happened. -->

So I wrote a different algorithm (the second one) to more efficently generate an adjacency list for the problem.
The algorithm creates the exact same dictionary as the less efficent one (this can be seen in the code above).
It works for every test cases except the one involving "charge" and "comedo".
For this case the code gives two different answers for, what should be, the exact same code.
If you use the first process to generate the adjacency list the program will give the correct answer of 42.
If you use the second process to generate the adjacency list the program will give an incorrect answer of 43.



#### Screenshots
https://www.dropbox.com/s/5bfs3m7yxe226gq/leetcode%20bug.PNG?dl=0
https://www.dropbox.com/s/ngp3l6inegtvnc6/leetcode%20bug%202.PNG?dl=0




#### Additional context

