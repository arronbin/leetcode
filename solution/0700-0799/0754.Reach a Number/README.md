# [754. 到达终点数字](https://leetcode.cn/problems/reach-a-number)

[English Version](/solution/0700-0799/0754.Reach%20a%20Number/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>在一根无限长的数轴上，你站在<code>0</code>的位置。终点在<code>target</code>的位置。</p>

<p>你可以做一些数量的移动 <code>numMoves</code> :</p>

<ul>
	<li>每次你可以选择向左或向右移动。</li>
	<li>第 <code>i</code>&nbsp;次移动（从 &nbsp;<code>i == 1</code>&nbsp;开始，到&nbsp;<code>i == numMoves</code> ），在选择的方向上走 <code>i</code>&nbsp;步。</li>
</ul>

<p>给定整数&nbsp;<code>target</code> ，返回 <em>到达目标所需的 <strong>最小&nbsp;</strong>移动次数(即最小 <code>numMoves</code> )&nbsp;</em>。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> target = 2
<strong>输出:</strong> 3
<strong>解释:</strong>
第一次移动，从 0 到 1 。
第二次移动，从 1 到 -1 。
第三次移动，从 -1 到 2 。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> target = 3
<strong>输出:</strong> 2
<strong>解释:</strong>
第一次移动，从 0 到 1 。
第二次移动，从 1 到 3 。
</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>-10<sup>9</sup>&nbsp;&lt;= target &lt;= 10<sup>9</sup></code></li>
	<li><code>target != 0</code></li>
</ul>

## 解法

<!-- 这里可写通用的实现逻辑 -->

**方法一：数学**

由于对称性，我们将 `target` 统计取绝对值。

定义 `s`，一直循环累加，直至满足 $s\ge target$ 并且 $(s-target)\mod 2 = 0$。返回循环次数即可。

证明：如果 $s\ge target$ 且 $(s-target)\mod 2 = 0$，那么只需要把前面 $(s-target)/2$ 这个数变为负数即可。

时间复杂度 $O(\sqrt{target})$。

<!-- tabs:start -->

### **Python3**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```python
class Solution:
    def reachNumber(self, target: int) -> int:
        target = abs(target)
        k = s = 0
        while 1:
            if s >= target and (s - target) % 2 == 0:
                break
            k += 1
            s += k
        return k
```

### **Java**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```java
class Solution {
    public int reachNumber(int target) {
        target = Math.abs(target);
        int s = 0;
        int k = 0;
        while (true) {
            if (s >= target && (s - target) % 2 == 0) {
                break;
            }
            ++k;
            s += k;
        }
        return k;
    }
}
```

### **C++**

```cpp
class Solution {
public:
    int reachNumber(int target) {
        target = abs(target);
        int s = 0, k = 0;
        while (true) {
            if (s >= target && (s - target) % 2 == 0) {
                break;
            }
            ++k;
            s += k;
        }
        return k;
    }
};
```

### **Go**

```go
func reachNumber(target int) int {
	s, k := 0, 0
	if target < 0 {
		target = -target
	}
	for {
		if s >= target && (s-target)%2 == 0 {
			break
		}
		k++
		s += k
	}
	return k
}
```

### **...**

```

```

<!-- tabs:end -->
