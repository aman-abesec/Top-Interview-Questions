
# DP(Dynamic Problem)

## 1D DP

### 1-Climbing Stairs

``` python

  #Recursive Soluation
  class Solution:
      def climbStairs(self, n: int) -> int:
          if n==0:return 1
          if n<0:return 0
          return self.climbStairs(n-1)+self.climbStairs(n-2)
  
  #Memoization Soluation
  class Solution:
      dp=[0 for _ in range(47)]
      def climbStairs(self, n: int) -> int:
          if self.dp[n]!=0:return self.dp[n]
          if n==0:return 1
          if n<0:return 0
          self.dp[n]=self.climbStairs(n-1)+self.climbStairs(n-2)
          return self.dp[n]
  
  #Tabulation
  class Solution:
    def climbStairs(self, n: int) -> int:
        dp=[1,1]
        for i in range(2,n+1):
            dp.append(dp[i-1]+dp[i-2])
        return dp[n]
