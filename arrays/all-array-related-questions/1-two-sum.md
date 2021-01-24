# 1: Two Sum

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

```python
def twosum(nums,target):
  h={}
  for index,num in enumerate(nums):
    diff=target-num
    if diff in h and index!=h[diff]:
      return(h[diff],index)
    else:
      h[num]=index

    
```

