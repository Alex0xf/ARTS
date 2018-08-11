# 5th week ARTS
## Algorithm
### 1.[DNA Pairing](https://forum.freecodecamp.org/t/freecodecamp-algorithm-challenge-guide-dna-pairing/16009)
Problem Explanation:
给定一个只包含ATCG四个字母组合的字符串，要求返回配对的数组，其中"A"对应["A"，“T”],"T"对应["T","A"]，"C"对应["C","G"],"G"对应["G","C"]。
如对于输入的 GCG，相应地返回 [["G", "C"], ["C","G"],["G", "C"]]

#### thoughts
1. 首先需要将字符串转换成字符数组 用split()即可
2. 由于字符串没有一些特殊的特点（如对称之类的），因此循环次数最少也会有n次，采用for循环遍历
3. 在只有几种情况，每种情况都有对应的处理情景下，让人自然想到switch case来解决

#### Solution
下面是我的JS代码
```javaScript
function pair(str) {
  strArr=str.split('');
  for(var i=0;i<str.length;i++){

    switch(strArr[i]){
        case 'A':{
                  strArr[i]=["A","T"];
                  break;
                 }
        case 'T':{
                  strArr[i]=["T","A"];
                  break;
                 }
        case 'C':{
                  strArr[i]=["C","G"];
                  break;
                 }
        case 'G':{
                  strArr[i]=["G","C"];
                  break;
                 }

    }
  }

  return strArr;
}
```

#### optimize
可以优化的地方：
可以用map的键值对来代替switch case
```javaScript
function pairElement(str) {
  var map = {T:'A', A:'T', G:'C', C:'G'};
  strArr = str.split('');

  for (var i=0;i<strArr.length;i++){
    strArr[i]=[strArr[i], map[strArr[i]]];
  }
 return strArr;
}
```

## Review
### 97 Things Every Should Know——2nd part
#### []()



## Tip
###


## Share
