## 코드
```python
def solution(rows, columns, queries):
    answer = []
    
    arr=[[0 for _ in range(columns+1)] for _ in range(rows+1)]
    count=1
    for i in range(1,rows+1):
        for j in range(1,columns+1):
            arr[i][j]=count
            count+=1
    for q in queries:
        c=987654321
        x1,y1,x2,y2=q
        temp=arr[x1+1][y1]
        c=min(c,temp)
        for i in range(y1,y2+1):
            cur=arr[x1][i]
            arr[x1][i]=temp
            temp=cur
            c=min(c,temp)


        for i in range(x1+1, x2+1):
            cur=arr[i][y2]
            arr[i][y2]=temp
            temp=cur
            c=min(c,temp)


        for i in range(y2-1,y1-1,-1):
            cur=arr[x2][i]
            arr[x2][i]=temp
            temp=cur
            c=min(c,temp)


        for i in range(x2-1,x1,-1):
            cur=arr[i][y1]
            arr[i][y1]=temp
            temp=cur
            c=min(c,temp)

        answer.append(c)
            
    
    return answer
```
