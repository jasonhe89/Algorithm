利用单调栈 从左向右扫描，可以得到每个柱子可以向右拓展到哪个index

同理的到向左拓展的index

area = (右index - 左index + 1) \* height

```python

class Solution:
    """
    @param height: A list of integer
    @return: The area of largest rectangle in the histogram
    """
    def largestRectangleArea(self, height):
        # write your code here
        if height == []:
            return 0
        stack = []
        hr = {}
        hl = {}
        
        for i in range(len(height)):
            if len(stack) == 0 or height[i] > stack[-1]:
                stack.append((height[i],i))
            else:
                while len(stack) > 0  and stack[-1][0] > height[i]:
                    x, index = stack.pop()
                    hr[index] = i-1
                stack.append((height[i],i))
                
        while len(stack) > 0:
            x, index = stack.pop()
            hr[index] = len(height) - 1
        #print hr
        
        
        
        for i in range(len(height) - 1, -1, -1):
            if len(stack) == 0 or height[i] > stack[-1]:
                stack.append((height[i],i))
            else:
                while len(stack) > 0  and stack[-1][0] > height[i]:
                    x, index = stack.pop()
                    hl[index] = i+1
                stack.append((height[i],i))
                
        while len(stack) > 0:
            x, index = stack.pop()
            hl[index] = 0
        #print hl
        
        maxArea = 0
        for i in range(len(height)):
            tempArea = height[i] * (hr[i] - hl[i] + 1)
            maxArea = max(tempArea, maxArea)
            
        return maxArea
```

