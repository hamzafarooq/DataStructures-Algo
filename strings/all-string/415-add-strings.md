---
description: >-
  Given two non-negative integers num1 and num2 represented as string, return
  the sum of num1 and num2.
---

# 415: Add Strings



```python
class Solution: 
    def addStrings(self, num1: str, num2: str) -> str: 
        sumofall= []
        carry  = 0
        for i in range(max(len(num1),len(num2))):
    
    
            if i < len(num1):
                a = num1[len(num1)-1-i]
            else:
                a = '0'
    
            if i < len(num2):
                b = num2[len(num2)-1-i]    
            else:
                b = '0'
    
            temp = ord(a) - ord('0') + ord(b) - ord('0') + carry #10 + carry
    
            remainder = temp % 10   #0
            carry = temp//10 #1
    
    
            sumofall.extend(str(remainder))
    
        if carry == 1:
            sumofall.extend(str(carry))
    
        sumofall = ("").join(sumofall)
        return sumofall[::-1]
```

