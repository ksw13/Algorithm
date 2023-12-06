## 코드
```java
class Solution {
    public String solution(String s) {
        String answer = "";
        
        StringBuilder sb = new StringBuilder();
        boolean flag=true;
        for(int i=0; i<s.length(); i++){
            Character cur = s.charAt(i);
            if(cur==' ') {
                sb.append(" ");
                flag=true;
            }
            else{
                if(flag==true){
                    if(Character.isLetter(cur)){
                        sb.append(String.valueOf(cur).toUpperCase());
                    }
                    else{
                        sb.append(cur);
                    }
                    flag=false;
                }
                else{
                    sb.append(String.valueOf(cur).toLowerCase());
                }
            }
        }
        
        return sb.toString();
    }
}
```
