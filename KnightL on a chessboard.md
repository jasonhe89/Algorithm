```js
#!/bin/python

import sys
from collections import deque

def bfs(move, n):
    x = move[0]
    y = move[1]
    board = [[sys.maxint for _ in range(n)] for _ in range(n)]
    board[0][0] = 0
    queue = deque([])
    queue.append((0,0))
    while len(queue) != 0:
        a, b = queue.popleft()
        da =[x,-x,x,-x,y,-y,-y,y] 
        db =[y,-y,-y,y,x,-x,x,-x]
        for i in range(8):
            nextA = a + da[i]
            nextB = b + db[i]
            #print nextA, nextB
            if nextA >= 0 and nextA < n and nextB >= 0 and nextB < n:
                if board[a][b] + 1 < board[nextA][nextB]:
                    board[nextA][nextB] = board[a][b] + 1
                    queue.append((nextA,nextB))
    #print board
    return board[n-1][n-1]

n = int(raw_input().strip())
record = [[-1] * (n-1) for _ in range(n-1)]
for i in range(1,n):
    for j in range(1,n):
        record[i-1][j-1] = bfs((i,j),n)
        if record[i-1][j-1] == sys.maxint:
            record[i-1][j-1] = -1
        
for i in range(n-1):
    for j in range(n-1):
        print str(record[i][j]) ,
    print '\n',

#n is the size of the board.
# we need a path from (0,0) to (n-1, n-1)
# your code goes here
# the move we can make are (a,b)   a in [1,n-1] b in [1,n-1]
# eg n = 5, board size is 5, (0,0) to (4,4)    move we can make are [1,1] ----> [4,4]
```