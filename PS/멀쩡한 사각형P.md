## 코드
```python
def gcd(w,h):
    while h!=0:
        temp=w%h
        w=h
        h=temp
    return w

def solution(w,h):
    answer = w*h
    g=gcd(w,h)
    mw=w/g
    mh=h/g
    
    return answer-((mw+mh-1)*g)
```
