### 1.递归&迭代  
### 代码块：迭代  
```python
class Solution:
    def myPow(self, x: float, n: int) -> float:
        if n==0:
            return 1.0
        if x==0:
            return 0.0
        x_pro=x
        ans = 1.0
        N=abs(n)
        while N>0:
            if N%2==1:
                ans*=x_pro
            x_pro*=x_pro
            N = N//2
        return ans if n>0 else (1.0/(ans))
```