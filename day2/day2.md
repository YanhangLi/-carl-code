day2

977总结：也是双指针的思想，从两侧向中间集合。

class Solution:

​    def sortedSquares(self, nums: List[int]) -> List[int]:

​        l,r = 0,len(nums)-1

​        res=[]

​        while l <=r:

​            lf=nums[l]*nums[l]

​            rf=nums[r]*nums[r]

​            if lf<=rf:

​                res.append(rf)

​                r-=1

​            else:

​                res.append(lf)

​                l+=1

​        return res[::-1]

209 

class Solution:

​    def minSubArrayLen(self, s: int, nums: List[int]) -> int:

​       sum=0

​       left=0

​       res=len(nums)+1#这是设置一个大的数字，方便后面取小的数字

​       for i in range(len(nums)):

​           sum+=nums[i]

​           while sum>=s:

​               res=min(res,i-left+1)

​               sum-=nums[left]#这是开始移动了，看看去掉left还大于s吗，尽量找长度短的

​               left+=1

​       if res==len(nums)+1:

​           return 0

​       else:return res

59

class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        nums = [[0] * n for _ in range(n)]
        x, y = 0, 0              
        loop, mid = n // 2, n // 2          
        count = 1                          

        for item in range(1, loop + 1) :     
            for i in range(y, n - item) :    
                nums[x][i] = count
                count += 1
            for i in range(x, n - item) :   
                nums[i][n - item] = count
                count += 1
            for i in range(n - item, y, -1) : 
                nums[n - item][i] = count
                count += 1
            for i in range(n - item, x, -1) : # 
                nums[i][y] = count
                count += 1                
            x += 1        
            y += 1
    
        if n % 2 != 0 :			
            nums[mid][mid] = count 
        return nums

