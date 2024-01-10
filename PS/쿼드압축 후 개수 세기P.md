## 코드
```python
zeroCount=0
oneCount=0

def divide(arr):
    global zeroCount
    global oneCount

    leng = len(arr)

    total = 0
    for i in range(0, leng):
        total += sum(arr[i])

    if total == leng * leng:
        oneCount += 1
        return
    elif total == 0:
        zeroCount += 1
        return

    half=leng//2
    temp=[arr[i][:half] for i in range(half)]
    divide(temp)
    temp = [arr[i][:half] for i in range(half,leng)]
    divide(temp)
    temp = [arr[i][half:] for i in range(half)]
    divide(temp)
    temp = [arr[i][half:] for i in range(half, leng)]
    divide(temp)

def solution(arr):
    answer = []
    
    divide(arr)
    answer.append(zeroCount)
    answer.append(oneCount)
    
    return answer
```
