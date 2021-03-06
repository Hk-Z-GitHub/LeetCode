# [476. Number Complement](https://leetcode.com/problems/number-complement)

[中文文档](/solution/0400-0499/0476.Number%20Complement/README.md)

## Description

<p>Given a <strong>positive</strong> integer <code>num</code>, output its complement number. The complement strategy is to flip the bits of its binary representation.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> num = 5
<strong>Output:</strong> 2
<strong>Explanation:</strong> The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> num = 1
<strong>Output:</strong> 0
<strong>Explanation:</strong> The binary representation of 1 is 1 (no leading zero bits), and its complement is 0. So you need to output 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The given integer <code>num</code> is guaranteed to fit within the range of a 32-bit signed integer.</li>
	<li><code>num &gt;= 1</code></li>
	<li>You could assume no leading zero bit in the integer&rsquo;s binary representation.</li>
	<li>This question is the same as 1009:&nbsp;<a href="https://leetcode.com/problems/complement-of-base-10-integer/">https://leetcode.com/problems/complement-of-base-10-integer/</a></li>
</ul>

## Solutions

<!-- tabs:start -->

### **Python3**

```python
class Solution:
    def findComplement(self, num: int) -> int:
        ans = 0
        find = False
        for i in range(30, -1, -1):
            b = num & (1 << i)
            if not find and b == 0:
                continue
            find = True
            if b == 0:
                ans |= (1 << i)
        return ans
```

### **Java**

```java
class Solution {
    public int findComplement(int num) {
        int ans = 0;
        boolean find = false;
        for (int i = 30; i >= 0; --i) {
            int b = num & (1 << i);
            if (!find && b == 0) {
                continue;
            }
            find = true;
            if (b == 0) {
                ans |= (1 << i);
            }
        }
        return ans;
    }
}
```

### **C++**

```cpp
class Solution {
public:
    int findComplement(int num) {
        int full = pow(2, int(log2(num)) + 1) - 1;
        return full ^ num;
    }
};
```

```cpp
class Solution {
public:
    int findComplement(int num) {
        int ans = 0;
        bool find = false;
        for (int i = 30; i >= 0; --i)
        {
            int b = num & (1 << i);
            if (!find && b == 0) continue;
            find = true;
            if (b == 0) ans |= (1 << i);
        }
        return ans;
    }
};
```

### **Go**

```go
func findComplement(num int) int {
	ans := 0
	find := false
	for i := 30; i >= 0; i-- {
		b := num & (1 << i)
		if !find && b == 0 {
			continue
		}
		find = true
		if b == 0 {
			ans |= (1 << i)
		}
	}
	return ans
}
```

### **...**

```

```

<!-- tabs:end -->
