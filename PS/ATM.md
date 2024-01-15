## 코드
```python
answer=0

n=int(input())
money=list(map(int, input().split(" ")))

money.sort()

temp=0
for i in money:
    temp+=i
    answer+=temp

print(answer)
```
