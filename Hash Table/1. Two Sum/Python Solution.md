# Two Sum

## Brute Force
```
def twoSum(self, nums, target):
  for i in range(len(nums)):
    for j in range(i + 1, len(nums)):
      if nums[i] + nums[j] == target:
        return [i, j]
```
## One-pass Hash Table
```
def twoSum(self, nums, target):
  hashmap = {}
  for i in range(len(nums)):
    if nums[i] in hashmap:
      return [hashmap[nums[i]], i]
    else:
      hashmap[target - nums[i]] = i
```
