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


## Tip

## Share
