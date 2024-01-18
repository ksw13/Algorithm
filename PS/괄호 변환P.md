## 코드
```java
import java.util.*;

class Solution {
    // 4-3
    public String change(String p){
        StringBuilder sb=new StringBuilder();
        for(int i=1; i<p.length()-1; i++){
            if(p.charAt(i)=='('){
                sb.append(")");
            }
            else{
                sb.append("(");
            }
        }
        return sb.toString();
    }
    
    // 올바른 괄호 문자열 확인
    public boolean check(String p){
        Stack<Character> st = new Stack<>();
        for(int i=0; i<p.length(); i++){
            if(p.charAt(i)=='('){
                st.push('(');
            }
            else{
                if(st.isEmpty()) return false;
                if(st.peek()=='('){
                    st.pop();
                }
            }
        }
        return st.isEmpty();
    }
    
    public String split(String p){
        StringBuilder u = new StringBuilder();
        StringBuilder v = new StringBuilder();
        
        int countA=0;
        int countB=0;
        for(int i=0; i<p.length(); i++){
            if(p.charAt(i)=='(') countA++;
            else countB++;
            
            if(countA==countB){
                u.append(p.substring(0,i+1));
                v.append(p.substring(i+1,p.length()));
                
                if(check(u.toString())){
                    return u.append(split(v.toString())).toString();
                }
                else{
                    StringBuilder sb=new StringBuilder();
                    sb.append("(");
                    sb.append(split(v.toString()));
                    sb.append(")");
                    sb.append(change(u.toString()));
                    return sb.toString();
                }
            }
            
        }
        return u.toString();
    }
    
    public String solution(String p) {    
        return split(p);
    }
}
```
