## 코드
```java
import java.util.*;

class Solution {
    static int answer;
    static int gn;
    static int[] row;
    
    public static boolean check(int r, int c){
        for(int i=1; i<r; i++){
            if(c==row[i])
                return false;
            if(Math.abs(i-r)==Math.abs(row[i]-c))
                return false;
        }
        return true;
    }
    
    public static void dfs(int cur){
        if(cur==gn+1){
            answer++;
            return ;
        }
        for(int i=1; i<=gn; i++){
            if(check(cur,i)){
                row[cur]=i;
                dfs(cur+1);
                row[cur]=-1;
            }
        }
    }
    public static int solution(int n) {
        answer = 0;
        gn=n;
        row=new int[n+1];
        Arrays.fill(row,-1);
        
        dfs(1);
        
        return answer;
    }
}
```
