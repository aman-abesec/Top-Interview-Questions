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
<summary>84. Largest Rectangle in Histogram</summary>
https://leetcode.com/problems/largest-rectangle-in-histogram/
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
<summary>42. Trapping Rain Water</summary>
https://leetcode.com/problems/trapping-rain-water/
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
