# 1st week ARTS
## Algorithm
### 1.[Sum All Numbers in a Range]
https://forum.freecodecamp.org/t/freecodecamp-algorithm-challenge-guide-sum-all-numbers-in-a-range/16083

Problem Explanation:
You need to create a program that will take an array of two numbers who are not
necessarily in order, and then add not just those numbers but any numbers in
between. For example, [3,1] will be the same as 1+2+3 and not just 3+1

先审题，一个数组包含两个不同的整型数据，要返回从小的值到大的值（包含这两个元素）之间的所
有值的和。第一想法是用一个for循环，用 Math.max（arr）和Math.min（）获得最大最小值，然
后从小的值加到大的值，每次加1。同时想了下可以用排序获得最大最小值，不过好像没太大影响，
后来看了中级解法发现可以结合着数学公式 累加结果=加的个数*（最大值+最小值）/2 即数量*平
均值来做。高级解法用了扩展运算符（... arr）允许将实际数组传递给函数而不是逐个元素，这个
之前没用到过，涨了知识。

*BasicCode Solution:*
```java
function sumAll(arr) {
var max = Math.max(arr[0], arr[1]);
var min = Math.min(arr[0], arr[1]);
    var temp = 0;
for (var i=min; i <= max; i++){
    temp += i;
}
return(temp);
}

sumAll([1, 4]);//test
```

Code Explanation:
 First create a variable to store the max number between two.
 The same as before for the Smallest number.
 We create a temporary variable to add the numbers.
Since the numbers might not be always in order, using max() and min() will help organize.

*Intermediate Code Solution:*
```java
function sumAll(arr) {
  // Buckle up everything to one!

  // Using ES6 arrow function (one-liner)
  var sortedArr = arr.sort((a,b) => a-b);
  var firstNum = arr[0];
  var lastNum = arr[1];
  // Using Arithmetic Progression summing formula

  var sum = (lastNum - firstNum + 1) * (firstNum + lastNum) / 2;
//这里用了数学公式 结果=数量*平均值
  return sum;
}
```
Code Explanation:
Firstly, we create a variable called sortedArr which sorts it from the lowest to
the highest value.
firstNum is equal to the first number and lastNum is equal to the second number.
Next, using the Arithmetic Progression summing formula we let sum equal (lastNum
- firstNum + 1) * (firstNum + lastNum) / 2.
Finally, we return sum.
The line var sortedArr = arr.sort((a,b) => a-b); is probably what will have you
more confused. This would be the same as creating a function that returns a-b 
for the sort() which is the standard way to sort numbers from smallest to
largest. Instead using arrow or fat arrow function, we are able to do all that
in one
single line thus allowing us to write less.

*Advanced Code Solution:*
```java
function sumAll(arr) {
    var sum = 0;
    for (var i = Math.min(...arr); i <= Math.max(...arr); i++){
        sum += i;
    }
  return sum;
}
```
Code Explanation:
Creating a variable sum to store the sum of the elements.
Starting iteration of the loop from min element of given array and stopping when
it reaches the max element.
Using a spread operator (…arr) allows passing the actual array to the function
instead of one-by-one elements.

总结一下
这种一重循环的优化的地方感觉比较少了，印象中这种情况优化多数在利用数学公式和利用抑或这种
逻辑判断还有递归这种，或者是一些不可通用的方法。

### 2.[Reverse Integer]
https://leetcode.com/problems/reverse-integer/description/

Problem Explanation:
Given a 32-bit signed integer, reverse digits of an integer.
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.
*Solution:*
Approach 1: Pop and Push Digits & Check before Overflow
Intuition
We can build up the reverse integer one digit at a time. While doing so, we can check beforehand whether or not appending another digit would cause overflow.
Algorithm
Reversing an integer can be done similarly to reversing a string.
We want to repeatedly "pop" the last digit off of xx and "push" it to the back of the \ text{rev}rev. In the end, \ text{rev}rev will be the reverse of the xx.
To "pop" and "push" digits without the help of some auxiliary stack/array, we can use math.

//pop operation:pop = x % 10;
x /= 10;
//push operation:
temp = rev * 10 + pop;
rev = temp;
