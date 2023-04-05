day1

27移除元素是双指针的思路，也用到了数组的一些知识

class Solution:

​    def removeElement(self, nums: List[int], val: int) -> int:

​        l,r = 0, len(nums)-1

​        while l<=r:

​            if  nums[l]==val:

​                nums[l],nums[r]=nums[r],nums[l]

​                r-=1

​            else:

​                l+=1

​        return l

704二分查找

二分法还是用的很广泛的

注意边界问题

class Solution:

​    def search(self, nums: List[int], target: int) -> int:

​        l,r=0,len(nums)-1

​        while l<=r:

​            middle=(l+r)//2

​            if nums[middle]>target:

​                r=middle-1

​            elif nums[middle]<target:

​                l=middle+1

​            else: 

​                return middle

​        return -1