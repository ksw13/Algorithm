## 코드
```python
from itertools import combinations

def solution(orders, course):
    answer = []
    
    for i in course:
        temp={}
        
        for order in orders:
            if len(order)>=i:
                ls=list(combinations(order,i))
                high=0
                for l in ls:
                    string=''.join(sorted(l))
                    if temp.get(string):
                        temp[string]+=1
                    else:
                        temp[string]=1
        max_order=[k for k,v in temp.items() if ((v==max(temp.values()) and v>1) )]
        answer.extend(max_order)
    answer.sort()
        
    return answer
```
