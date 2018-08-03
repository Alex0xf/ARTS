# 5th week ARTS
## Algorithm
### 1.[Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)
Problem Explanation:

Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.
Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

```java
class Solution {
    public int removeDuplicates(int[] nums) {
    if (nums.length == 0||nums==null) {
			return 0;
		}

		else if (nums.length == 1) {
			return 1;
		}

		else{
      int index = 1;
  		for (int i = 1; i < nums.length; i++) {
  			if (nums[i] != nums[i - 1]) {
  				nums[index] = nums[i];
  				index++;
  			}
  		}
  		return index;
      }
    }
}
```

## Review
### 1. 97 Things Every Should Know——2nd part
#### [Apply Functional Programming Principles](https://97-things-every-x-should-know.gitbooks.io/97-things-every-programmer-should-know/content/en/thing_02/index.html)
这篇文章说到函数式编程范式的好处。它可以提升你代码的质量，可以使得结果正确性得到保障。编程范式几乎不依赖什么所以副作用很少。编程范式的一大优点是不可变性。相较于编程范式，我们之前熟悉的面向对象的程序语言因为变量原因或多或少会出现值和预期不同，编程范式杜绝了这种缺陷。编程范式的使用使得调试代码也变得方便。

#### [Ask "What Would the User Do?"](https://97-things-every-x-should-know.gitbooks.io/97-things-every-programmer-should-know/content/en/thing_03/index.html)
问问用户会怎样做？


这两天刚出一个事情，网传某互联网公司一产品经理要求程序员做出一个程序。要求程序可以根据用户的手机壳颜色改变手机背景色，结果程序员生气骂产品不懂技术瞎指挥，产品说这个功能很容易就使可以实现，你就这样那样就可以，于是两人打架。离职的时候两人又打了一架。在这里我们不去讨论这件事的真实性，我们想一想，如果你是里面的其中一人（以后保不准你也会遇到这样的事情），你会怎么做。


再引申一下，问问别人（项目经理，大牛，老总等等）是怎么想怎么做的？


## Tip
### SSM(Spring SpringMVC Mybatis)


## Share
