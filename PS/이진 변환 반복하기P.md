## 코드
```python
def solution(s):
    answer = []
    
    count=0
    total=0
    while True:
        if len(s)==1: break
        
        before=len(s)
        s=s.replace("0","")
        after=len(s)
        count+=1
        total+=(before-after)
        
        s=bin(len(s))
        s=s[2:]
    
    answer.append(count)
    answer.append(total)
    
    return answer
```
