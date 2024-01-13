## 코드
```python
def solution(s):
    answer = []
    
    arr=[]
    for i in range(1,len(s)):
        if s[i].isdigit() or s[i]==",":
            temp+=s[i]
        else:
            if s[i-1].isdigit():
                arr.append(temp)
            temp=""
            
    arr.sort(key=lambda x:len(x))
    
    answer.append(int(arr[0]))
    for i in range(1,len(arr)):
        temp=arr[i].split(",")
        for j in temp:
            if int(j) not in answer:
                answer.append(int(j))
                break
    
    return answer
```
