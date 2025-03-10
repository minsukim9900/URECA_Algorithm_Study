### 풀이 코드
```java
import java.util.*;

class Solution {
    public int solution(int distance, int[] rocks, int n) {
        int answer = 0;
    
        Arrays.sort(rocks);
        int start = 1;
        int end = distance;
        
        while(start <= end) {
            int mid = (start + end) / 2;
            
            // 돌 사이의 거리가 mid 이상으로 만들려면 몇개의 돌 제거?
            int removeRockCnt = 0;
            int prevRockPosition = 0;
            for(int rock: rocks) {
                if(rock - prevRockPosition < mid) {
                    removeRockCnt++;
                }else {
                    prevRockPosition = rock;
                }
            }
            
            if(distance - prevRockPosition < mid) {
                removeRockCnt++;
            }
            
            if(removeRockCnt <= n) {
                answer = mid;
                start = mid + 1;
            }else {
                end = mid - 1;
            }
        }
        
        return answer;
    }
}
```

### 출력 결과
![img.png](img.png)