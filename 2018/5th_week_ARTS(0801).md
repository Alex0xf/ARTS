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
### 97 Things Every Should Know——2nd part
#### [Apply Functional Programming Principles](https://97-things-every-x-should-know.gitbooks.io/97-things-every-programmer-should-know/content/en/thing_02/index.html)
这篇文章说到函数式编程范式的好处。它可以提升你代码的质量，可以使得结果正确性得到保障。编程范式几乎不依赖什么所以副作用很少。编程范式的一大优点是不可变性。相较于编程范式，我们之前熟悉的面向对象的程序语言因为变量原因或多或少会出现值和预期不同，编程范式杜绝了这种缺陷。编程范式的使用使得调试代码也变得方便。

#### [Ask "What Would the User Do?"](https://97-things-every-x-should-know.gitbooks.io/97-things-every-programmer-should-know/content/en/thing_03/index.html)
人总是倾向于假定别人也是像自己一样去思考，但很多情况不是，这样就造成了错误的认知偏差（the false consensus bias）。当别人显露出跟我们不一样的思维方式或者行为时，我们会下意识把这种不一样当成是一种攻击并做出反应。
了解别人是怎么想的最好的方式是观察他并思考他是怎么想的，他为什么会这样想，为什么他没有做出和你一样的选择？

## Tip
### SSM(Spring SpringMVC Mybatis)
最近开始研究SSM框架。
按照教程配置完SSM框架，但是不是很清楚各个部分的关系。在网上搜索资料找到一个还不错的思路图。
![](http://pbok9izql.bkt.clouddn.com/5th_week_ARTS-ssm.png.png)

## Share
从Review第二篇文章引申而来
这两天刚出一个事情，网传某互联网公司一产品经理要求程序员做出一个程序。要求程序可以根据用户的手机壳颜色改变手机背景色，结果程序员生气骂产品不懂技术瞎指挥，产品说这个功能很容易就使可以实现，你就这样那样就可以，于是两人打架。离职的时候两人又打了一架。在这里我们不去讨论这件事的真实性，我们想一想，如果你是里面的其中一人（以后保不准你也会遇到这样的事情），你会怎么做。
作为程序员应该了解清楚上面为什么会这么要求，真正需求什么。是否可行如果无法实现是什么限制，可以实现的话有没有更好的方式使得用户体验更好。程序员的首要责任是理解需求并把东西做出来而不是去质疑产品不专业即使产品提了一个看似不科学的需求。如果真的无法实现或者产品提的需求太奇葩只能努力提升自己去有不那么奇葩产品更好的公司。
作为产品经理自己也需要有基本的技术了解，不能想到一个东西就让程序员去做。应该先自己大概判断一下需求是否合理，能不能做。拿不定的需要和程序员讨论并告诉他你的真实需求是什么。产品和程序员应该是相互扶持共同成长的，产品不断充实自身技术水平，提升和程序员沟通的水平。而程序员也不只是埋头写代码，也要了解用户需求并不断提升自己的修养。
还可以想想我们身边厉害的大佬遇到这样的情况会怎么做。
