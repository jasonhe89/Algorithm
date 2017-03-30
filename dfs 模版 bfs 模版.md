```python
def getNodes(self,node):
        #dfs
        stack =[]
        hs = set()
        stack.append(node)
        while len(stack) != 0:
            head = stack.pop()
            if head not in hs:
                hs.add(head)
                for n in head.neighbors:
                    stack.append(n)
        return list(hs)
        
        
        #bfs
        queue = deque([])
        visited = set()
        queue.append(node)
        visited.add(node)
        while len(queue) != 0:
            head = queue.popleft()
            for neighbor in head.neighbors:
                if neighbor not in visited:
                    visited.add(neighbor)
                    queue.append(neighbor)
        return list(visited)
```