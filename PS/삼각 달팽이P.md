## 코드
```python
direction={0:(1,0), 1:(0,1), 2:(-1,-1)}

def solution(n):
    answer = []
    
    arr=[[0]*i for i in range(1,n+1)]
    x,y=-1,0
    num=1
    for i in range(n):
        for j in range(i,n):
            dx,dy=direction[i%3]
            x+=dx
            y+=dy
            arr[x][y]=num
            num+=1
    
    for i in range(n):
        for j in range(i+1):
            answer.append(arr[i][j])
    
    return answer
```
