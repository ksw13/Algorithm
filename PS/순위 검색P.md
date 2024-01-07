## 코드
```python
from bisect import bisect_left
from collections import defaultdict

def solution(info, query):
    answer = []
    
    dict=defaultdict(list)
    
    inform=[]
    for i in info:
        lang,job,car,soul,score=i.split(" ")
        for i in ['-',lang]:
            for j in ['-',job]:
                for k in ['-',car]:
                    for l in ['-',soul]:
                        dict[i+j+k+l].append(int(score))

    for value in dict.values():
        value.sort()  
   
    for q in query:
        q=q.replace("and","")
        q=q.replace("  "," ")
        lang,job,car,soul,score=q.split(" ")
        ls = dict[lang+job+car+soul]
        
        index=bisect_left(ls,int(score))
        answer.append(len(ls)-index)
        
    return answer
```
