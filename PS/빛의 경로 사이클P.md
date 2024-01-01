## 코드
```java
import java.util.*;

class Solution {
    boolean[][][] visited;
    // 12시,3시,6시,9시
    int[] dx={-1,0,1,0};
    int[] dy={0,1,0,-1};
    int rLength;
    int cLength;
    String[] gGrid;
    
    public int cycle(int r, int c, int d){
        int count=0;
        
        while(true){
            if(visited[r][c][d]==true)
                break;
            
            visited[r][c][d]=true;
            count++;
            
            if(gGrid[r].charAt(c)=='L'){
                d=(d-1+4)%4;    
            }
            else if(gGrid[r].charAt(c)=='R'){
                d=(d+1)%4;    
            }
            r=(r+dx[d]+rLength)%rLength;
            c=(c+dy[d]+cLength)%cLength;
        }
        return count;
    }
    
    public int[] solution(String[] grid) {
        List<Integer> answer = new ArrayList<>();
        rLength=grid.length;
        cLength=grid[0].length();
        gGrid=grid;
        
        visited=new boolean[rLength][cLength][4];
        
        for(int i=0; i<rLength; i++){
            for(int j=0; j<cLength; j++){
                for(int k=0; k<4; k++){
                    if(visited[i][j][k]==false){
                        answer.add(cycle(i,j,k));
                    }
                }
            }
        }
        Collections.sort(answer);
        
        return answer.stream().mapToInt(i->i).toArray();
    }
}
```
