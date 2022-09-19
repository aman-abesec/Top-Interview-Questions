
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

###  Frog Jump

``` python

def frogJump(n: int, heights: List[int]) -> int:
    def solve(n,heights):
        if n==0:return 0
        if n<0:return inf
        l,r=inf,inf
        if n-2>=0:
            l=abs(heights[n]-heights[n-2])+solve(n-2,heights)
        if n-1>=0:
            r=abs(heights[n]-heights[n-1])+solve(n-1,heights)
        return min(l,r)
    return solve(n-1,heights)
    
def frogJump(n: int, heights: List[int]) -> int:
    def solve(n,heights,dp):
        if dp[n]!=-1:return dp[n]
        if n==0:return 0
        if n<0:return inf
        l,r=inf,inf
        if n-2>=0:
            l=abs(heights[n]-heights[n-2])+solve(n-2,heights,dp)
        if n-1>=0:
            r=abs(heights[n]-heights[n-1])+solve(n-1,heights,dp)
        dp[n]=min(l,r)
        return dp[n]
    dp=[-1 for _ in range(n+1)]
    return solve(n-1,heights,dp)
    
