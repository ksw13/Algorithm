## 코드
```java
import java.util.*;

class Solution {
    String result="";
    Map<String, String> map = new HashMap<>();
    
    public void insert(String str){
        result+=str;
    }
    
    public String solution(int n, int t, int m, int p) {
        String answer = "";
        
        map.put("10","A");
        map.put("11","B");
        map.put("12","C");
        map.put("13","D");
        map.put("14","E");
        map.put("15","F");
        
        for(int i=0; i<t*m; i++){
            int temp=i;
            StringBuilder sb = new StringBuilder();
            while(temp>=n){
                int mod = temp%n;
                if(mod>=10){
                    sb.append(map.get(String.valueOf(mod)));
                }
                else{
                    sb.append(mod);
                }
                temp/=n;
            }
            if(temp>=10){
                sb.append(map.get(String.valueOf(temp)));
            }
            else{
                sb.append(temp);
            }
            insert(sb.reverse().toString());
        }
        
        int seq=p-1;
        while(t-- >0){
            answer+=result.charAt(seq);
            seq+=m;
        }
        
        return answer;
    }
}
```
