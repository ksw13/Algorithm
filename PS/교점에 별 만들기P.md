## 코드
```java
import java.util.*;

class Solution {
    public int calX(int a, int b, int e, int c, int d, int f){
        long aa=((long)b*f)-((long)e*d);
        long bb=((long)a*d)-((long)b*c);
        
        if (bb!=0 && aa%bb==0)
            return Long.valueOf(aa/bb).intValue();
        else
            return Integer.MAX_VALUE;
    }
    
    public int calY(int a, int b, int e, int c, int d, int f){
        long aa=((long)e*c)-((long)a*f);
        long bb=((long)a*d)-((long)b*c);
        
        if (bb!=0 && aa%bb==0)
            return Long.valueOf(aa/bb).intValue();
        else
            return Integer.MAX_VALUE;
    }
    
    public String[] solution(int[][] line) {
        int lineLength = line.length;
        Set<Node> result=new HashSet<>();
        
        for(int i=0; i<lineLength; i++){
            for(int j=i+1; j<lineLength; j++){
                int x=calX(line[i][0],line[i][1],line[i][2],line[j][0],line[j][1],line[j][2]);
                int y=calY(line[i][0],line[i][1],line[i][2],line[j][0],line[j][1],line[j][2]);
                if(x!=Integer.MAX_VALUE && y!=Integer.MAX_VALUE){
                    result.add(new Node(x,y));
                }
            }
        }
        int lowX=Integer.MAX_VALUE;
        int highX=Integer.MIN_VALUE;
        int lowY=Integer.MAX_VALUE;
        int highY=Integer.MIN_VALUE;
        
        Iterator<Node> iter = result.iterator();
        while(iter.hasNext()){
            Node temp = iter.next();
            lowX=Math.min(lowX,temp.x);
            highX=Math.max(highX,temp.x);
            lowY=Math.min(lowY,temp.y);
            highY=Math.max(highY,temp.y);
        }
        if(lowX==0 && highX==0 && lowY==0 && highY==0){
            return new String[]{"*"};
        }
        
        String[][] answer=new String[highY-lowY+1][highX-lowX+1];
        for(int i=0; i<answer.length; i++){
            Arrays.fill(answer[i],".");
        }
        iter = result.iterator();
        while(iter.hasNext()){
            Node temp = iter.next();
            answer[temp.y-lowY][temp.x-lowX]="*";
        }
        
        String[] total=new String[highY-lowY+1];
        for(int i=0; i<answer.length; i++){
            StringBuilder sb=new StringBuilder();
            for(int j=0; j<answer[0].length; j++){
                sb.append(answer[answer.length-i-1][j]);
            }
            total[i]=sb.toString();
        }
        
        return total;
    }
    
    public class Node{
        int x;
        int y;
        Node(int x, int y){
            this.x=x;
            this.y=y;
        }
    }
}
```
