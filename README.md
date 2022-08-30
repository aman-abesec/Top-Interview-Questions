# Hard Problem
<!--<details>
<summary>Easy Problem</summary>
<p>

```python
   print("Hello World")
```

</p>
</details>-->

<details>
<summary>Binary Tree to DLL</summary>
 <a href="https://practice.geeksforgeeks.org/problems/binary-tree-to-dll/1?page=1&company[]=Amazon&curated[]=5&curated[]=6&sortBy=submissions">Problem</a>
<p>

```python
head=None
prev=None
class Solution:
    def bToDLL(self,root):
        def solve(root):
            global head
            global prev
            if root==None:return 
            solve(root.left)
            if prev==None:
                head=root
            if prev!=None:
                root.left=prev
                prev.right=root
            prev=root
            solve(root.right)
        global head
        global prev
        head=None
        prev=None
        solve(root)
        return head
```

</p>
</details>

<details>
<summary>Alien Dictionary</summary>
<a href="https://practice.geeksforgeeks.org/problems/alien-dictionary/1?page=1&company[]=Amazon&curated[]=5&curated[]=6&sortBy=submissions">Problem</a>
<p>

```python
   class Solution:
    def findOrder(self,dict, N, K):
        def dfs(s,arr,stack,visited):
            visited[s]=1
            for v in arr[s]:
                if visited[v]!=1:
                    dfs(v,arr,stack,visited)
            stack.append(s)
                
        def solve(dict,N,K):
            u=[[] for _ in range(K)]
            for i in range(N-1):
                w1=dict[i]
                w2=dict[i+1]
                for k in range(min(len(w1),len(w2))):
                    if w1[k]!=w2[k]:
                        u[ord(w1[k])-ord('a')].append(ord(w2[k])-ord('a'))
                        break
            s=''
            visited=[0 for _ in range(K)]
            # print(u)
            for i in range(K):
                if visited[i]==0:
                    stack=[]
                    dfs(i,u,stack,visited)
                    while stack:
                        s+=chr(ord('a')+stack.pop(0))
            # print(s)
            return s[::-1]
        return solve(dict,N,K)
```

</p>
</details>

<details>
<summary>Serialize and Deserialize Binary Tree</summary>
   <a href="https://leetcode.com/problems/serialize-and-deserialize-binary-tree/">Problem</a>
<p>

```python
   class Codec:

    def serialize(self, root):
        """Encodes a tree to a single string.
        
        :type root: TreeNode
        :rtype: str
        """
        ans=[]
        def solve(root):
            if root==None:
                ans.append(str('N'))
                return
            ans.append(str(root.val))
            solve(root.left)
            solve(root.right)
        solve(root)
        return  ",".join(ans)
        
        

    def deserialize(self, data):
        """Decodes your encoded data to tree.
        
        :type data: str
        :rtype: TreeNode
        """
        def solve(num,ind):
            if ind[0]==len(num):return None
            val=num[ind[0]]
            ind[0]+=1
            if val=='N':return None
            root=TreeNode(int(val))
            root.left=solve(num,ind)
            root.right=solve(num,ind)
            return root
        num=data.split(',')
        ind=[0]
        return solve(num,ind)
```

</p>
</details>


<details>
<summary>Largest Rectangle in Histogram</summary>
   <a href="https://leetcode.com/problems/largest-rectangle-in-histogram/">Problem</a>
<p>
   
```python
import math
class Solution:
    #Function for finding left most smallest
    def leftSmallest(self,height,length):
        left_smallest_height=[]
        stack=[]
        for i in range(length):
            if stack==[]:
                left_smallest_height.append(-1)
                stack.append(i)
            else:
                if height[stack[-1]]<height[i]:
                    left_smallest_height.append(stack[-1])
                    stack.append(i)
                else:
                    while stack!=[] and height[stack[-1]]>=height[i]:
                        stack.pop()
                    if stack==[]:
                        left_smallest_height.append(-1)
                    else:
                        left_smallest_height.append(stack[-1])
                    stack.append(i)
        return left_smallest_height
    
    #Function for finding right most smallest
    def rightSmallest(self,height,length):
        right_smallest_height=[]
        stack=[]
        for i in range(length-1,-1,-1):
            if stack==[]:
                right_smallest_height.append(length)
                stack.append(i)
            else:
                if height[stack[-1]]<height[i]:
                    right_smallest_height.append(stack[-1])
                    stack.append(i)
                else:
                    while stack!=[] and height[stack[-1]]>=height[i]:
                        stack.pop()
                    if stack==[]:
                        right_smallest_height.append(length)
                    else:
                        right_smallest_height.append(stack[-1])
                    stack.append(i)
        return right_smallest_height
    
    def largestRectangleArea(self, heights: List[int]) -> int:
        length=len(heights)
        left_smll=self.leftSmallest(heights,length)
        right_smll=self.rightSmallest(heights,length)
        mx=-math.inf
        for i in range(length):
            #Calculating length of histogram by subtracting left a right smallest index minus one and multiplying by its heights
            mx=max(mx,(right_smll[length-1-i]-left_smll[i]-1)*heights[i])
        return mx
        
```

</p>
</details>

<details>
<summary>Trapping Rain Water</summary>
   <a href="https://leetcode.com/problems/trapping-rain-water/">Problem</a>
<p>

```python
   class Solution:
   #Function for finding all previous greatest element
    def leftGreatest(self,height,length):
        left_greatest_height=[]
        stack=[]
        for i in range(length):
            if stack==[]:
                stack.append(height[i])
                left_greatest_height.append(stack[-1])
            else:
                if stack[-1]>=height[i]:
                    left_greatest_height.append(stack[-1])
                else:
                    while stack!=[] and stack[-1]<=height[i]:
                        stack.pop()
                    stack.append(height[i])
                    left_greatest_height.append(stack[-1])
        return left_greatest_height
    
    #Function for finding all next greatest element
    def rightGreatest(self,height,length):
        right_greatest_height=[]
        stack=[]
        for i in range(length-1,-1,-1):
            if stack==[]:
                stack.append(height[i])
                right_greatest_height.append(stack[-1])
            else:
                if stack[-1]>=height[i]:
                    right_greatest_height.append(stack[-1])
                else:
                    while stack!=[] and stack[-1]<height[i]:
                        stack.pop()
                    stack.append(height[i])
                    right_greatest_height.append(stack[-1])
        return right_greatest_height
                    
    def trap(self, height: List[int]) -> int:
        length=len(height)
        left_gre=self.leftGreatest(height,length)
        right_gre=self.rightGreatest(height,length)
        answer=0
        for i in range(length):
            #Calculate min of left and right greatest elemen minus with current height
            answer+=min(left_gre[i],right_gre[length-i-1])-height[i]
        return answer
```

</p>
</details>

<!--<details>
<summary>Medium Problem</summary>
<p>
<details>
<summary>Easy Problem</summary>
<p>

```python
   print("Hello World")
```

</p>
</details>
</p>
</details>


<details>
<summary>Easy Problem</summary>
<details>
<summary>Easy Problem</summary>
<p>

</p>
</details>
</details>-->


<!-- - [x] Hello

Here is a simple footnote[^1].

A footnote can also have multiple lines[^2].  

You can also use words, to fit your writing style more closely[^note].

[^1]: My reference.
[^2]: Every new line should be prefixed with 2 spaces.  
  This allows you to have a footnote with multiple lines.
[^note]:
    Named footnotes will still render with numbers instead of the text but allow easier identification and linking.  
    This footnote also has been made with a different syntax using 4 spaces for new lines.-->
