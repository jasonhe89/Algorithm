```python
    def addDigits(self,num):
        while num / 10 > 0:
            sum = 0
            while num > 0:
                sum += nums % 10
                num /= 10
            num = sum
        return num
```