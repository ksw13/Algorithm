## 코드
```python
from collections import deque

dx=[-1,1,0,0]
dy=[0,0,-1,1]

def bfs(place, r, c):
    queue=deque()
    visited=[[0 for _ in range(5)] for _ in range(5)]
    queue.append([r,c])
    while queue:
        x,y=queue.popleft()
        for i in range(4):
            nx=x+dx[i]
            ny=y+dy[i]
            if 0<=nx<5 and 0<=ny<5 and visited[nx][ny]==0 and place[nx][ny]!='X':
                
                visited[nx][ny]=visited[x][y]+1
                queue.append([nx,ny])

    
    for i in range(5):
        for j in range(5):
            if i==r and j==c:
                continue
            if 1<=visited[i][j]<=2 and place[i][j]=='P':
                return False;
    
    
    return True;
    

def solution(places):
    answer = []
    
    for place in places:
        flag=False
        for i in range(5):
            for j in range(5):
                if place[i][j]=='P':
                    f=bfs(place,i,j)
                    if f==False:
                        flag=True
                        break
            if flag==True:
                break
        if flag==True:
            answer.append(0)
        else:
            answer.append(1)
    
    return answer
```
