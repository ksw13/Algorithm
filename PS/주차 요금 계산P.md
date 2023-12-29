## 코드
```python
import math

def change(time):
    h,m=map(int, time.split(":"))
    return h*60+m 

def solution(fees, records):
    answer = []
    
    rec=[]
    for i in records:
        time, number, inout=i.split(" ")
        rec.append([change(time),number,inout])
    
    feeSt={}
    inSt={}
    
    for time,number,inout in rec:
        if inout=='IN':
            inSt[number]=time
        else:
            if number in feeSt:
                feeSt[number]+=(time-inSt[number])
            else:
                feeSt[number]=(time-inSt[number])
            inSt[number]=-1
    
    for key,value in inSt.items():
        if inSt[key]!=-1:
            if key in feeSt:
                feeSt[key]+=1439-inSt[key]
            else:
                feeSt[key]=1439-inSt[key]
    
    for key,value in feeSt.items():
        temp=0
        if value<=fees[0]:
            temp+=fees[1]
        else:
            temp+=fees[1]
            remain=value-fees[0]
            temp+=math.ceil(remain/fees[2])*fees[3] 
        answer.append([int(key), temp])
    
    answer.sort(key=lambda x:x[0])
    result=[]
    for number,money in answer:
        result.append(money)
        
    return result
```
