## 코드
```java
class Solution {
    public boolean pri(Long n){
        if (n==1) return false;
        for (int i=2; i<(int)Math.sqrt(n)+1; i++){
            if (n%i==0){
                return false;
            }
        }
        return true;
    }
    
    public String change(int n, int k){
        StringBuilder sb=new StringBuilder();
        while(n>0){
            sb.append(n%k);
            n/=k;
        }
        return sb.reverse().toString();
    }
    
    public int solution(int n, int k) {
        int answer = 0;
        
        String temp=change(n,k);
        // System.out.println(temp);
        String result[]=temp.split("0");
        // for(int i=0; i<result.length; i++){
        //     System.out.print(result[i]+" ");
        // }
        
        if(result.length==1){
            if(pri(Long.valueOf(result[0]))) return 1;
            else return 0;
        }
        
        else{
            for(int i=0; i<result.length; i++){
                if(result[i].equals("")) continue;
                if(pri(Long.valueOf(result[i]))) {
                    answer++;
                }
            }
            
        }
        
        return answer;
    }
}
```
