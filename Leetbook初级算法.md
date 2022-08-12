## Leetbook - Beginner Algorithms

### 189. Rotate Array

#### 1. my solution

```python
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        if k > len(nums):
            k = k % len(nums)
        temp = nums[len(nums) - k :]  # u
        for i in range(len(nums) - k - 1, -1, -1):
            nums[i + k] = nums[i]
        for t in range(len(temp)):
            nums[t] = temp[t]
```

So, I use a list `temp` to store the last numbers that need to be replaced by their former numbers.

Time complexity: O(n)

Space complexity: O(n)



#### 2. Switch

```python
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        k = k % len(nums)
        nums[:] = nums[-k:] + nums[:-k]
```

Time complexity: O(n)

Space complexity: O(1)



#### 3. Ring replacement

```py
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        n = len(nums)
        round = math.gcd(n, k)
       	for i in range(round):
            pin, temp = i, nums[i]
            start = pin
            while True:
                next = (pin + k) % n
                nums[next], temp = temp, nums[next]
                pin = next
                if start == pin:  # avoiding loop
                    break      
                
```

<img src="C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20220812164912744.png" alt="image-20220812164912744" style="zoom:50%;" />