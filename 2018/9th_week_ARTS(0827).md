# 9th week ARTS
## Algorithm
### 1.[Search Insert Position](https://leetcode.com/problems/search-insert-position/description/)
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.
You may assume no duplicates in the array.

#### Intuition
二分查找可以解决，关键是一些临界点的时候取值。


#### Solution
```JAVA
public static int searchInsert(int[] nums, int target) {
        return binarySerach(nums,0,nums.length-1,target);
    }


    public static int binarySerach(int[] nums,int low,int high,int target){
        int mid=(high+low)/2;
        while (low<=high){
            if(nums[mid]<target){
                low=mid+1;
            }else if(nums[mid]>target){
                high=mid-1;
            }else if(nums[mid]==target) {return mid;}
            return binarySerach(nums,low,high,target);
        }
        if(nums[mid]<target)return mid+1;
        else return mid;
    }
```
#### Optimize
简洁版

```JAVA
public static int searchInsert2(int[] A, int target) {
        int low = 0, high = A.length-1;
        while(low<=high){
            int mid = (low+high)/2;
            if(A[mid] == target) return mid;
            else if(A[mid] > target) high = mid-1;
            else low = mid+1;
        }
        return low;
    }
```

## Review
### 97 Things Every Should Know——6th part(7/97)
####


## Tip
### Spring Boot

## Share
### []()
