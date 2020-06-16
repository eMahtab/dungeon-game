# Dungeon Game
## https://leetcode.com/problems/dungeon-game


# Implementation :
```java
class Solution {
    public int calculateMinimumHP(int[][] dungeon) {
      if(dungeon == null || dungeon.length == 0)
          return 1;
       
      int rows = dungeon.length, columns = dungeon[0].length;
      int dp[][] = new int[rows+1][columns+1];
      for(int i = 0; i < dp.length; i++) {
          Arrays.fill(dp[i], Integer.MAX_VALUE);
      }  
      dp[rows-1][columns] = 1;   
      dp[rows][columns-1] = 1;
        
      for(int row = rows - 1; row >= 0; row--) {
          for(int col = columns-1; col >= 0; col--) {
              int minHealthPoint = Math.min(dp[row+1][col], dp[row][col+1]) - dungeon[row][col];
              if(minHealthPoint <= 0)
                  dp[row][col] = 1;
              else 
                  dp[row][col] = minHealthPoint;
          }
      }  
      
      return dp[0][0];  
    }
}
```

# References :
https://www.youtube.com/watch?v=cOLjLbBBUTk
