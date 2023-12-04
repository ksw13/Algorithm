## 코드
```java
class Solution {
    public int gcd(int a, int b){
        while(b!=0){
            int temp = a%b;
            a=b;
            b=temp;
        }
        return a;
    }
    
    public int solution(int[] arr) {
        int answer = arr[0];
        
        for(int i=1; i<arr.length; i++){
            int max=Math.max(answer,arr[i]);
            int min=Math.min(answer,arr[i]);
            
            int g=gcd(max,min);
            answer=g*(answer/g)*(arr[i]/g);
        }
        
        return answer;
    }
}
```
