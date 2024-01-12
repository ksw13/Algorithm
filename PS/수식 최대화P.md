## 코드
```python
from copy import deepcopy

def operation(num1, num2, op):
    if op == '+':
        return str(int(num1) + int(num2))
    if op == '-':
        return str(int(num1) - int(num2))
    if op == '*':
        return str(int(num1) * int(num2))

def solution(exp):
    answer = 0
    
    seq=['*-+','*+-','-*+','-+*','+*-','+-*']

    arr=[]
    temp=""
    for i in exp:
        if i.isdigit():
            temp+=i
        else:
            arr.append(temp)
            arr.append(i)
            temp=""
    arr.append(temp)
    
    
    for s in seq:
        temp=deepcopy(arr)
        for i in s:
            stack=[]
            while len(temp)!=0:
                tmp=temp.pop(0)
                if i==tmp:
                    stack.append(operation(stack.pop(), temp.pop(0), i))
                else:
                    stack.append(tmp)
            temp=deepcopy(stack)
        answer=max(answer,abs(int(temp[0])))
    
    
    return answer
```
