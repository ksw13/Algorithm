## 코드
```python
from collections import deque

def solution(s):
    answer = 0
    
    queue=deque()
    for i in s:
        queue.append(i)
    for i in range(len(s)):
        temp=[]
        flag=False
        for j in queue:
            if j in ['}',']',')']:
                if len(temp)==0:
                    flag=True
                    break
                
            if j in ['{','[','(']:
                temp.append(j)
            elif j=='}':
                if temp[-1]=='{':
                    temp.pop()
                else:
                    flag=True
                    break
            elif j==')':
                if temp[-1]=='(':
                    temp.pop()
                else:
                    flag=True
                    break
            elif j==']':
                if temp[-1]=='[':
                    temp.pop()
                else:
                    flag=True
                    break
        if len(temp)==0 and flag==False:
            answer+=1
        queue.append(queue.popleft())

    
    return answer
```
