class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        nums_dict = {}
        
        for i, j in enumerate(nums):
            diff = target - j
            if diff in nums_dict.keys():
                return [i, nums_dict[diff]]
            nums_dict[j] = i
