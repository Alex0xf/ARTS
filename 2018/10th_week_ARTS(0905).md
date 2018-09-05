# 10th week ARTS
## Algorithm
### 1.[Count and Say](https://leetcode.com/problems/count-and-say/description/)
Given an integer n, generate the nth term of the count-and-say sequence.

刚开始看了半天没理解什么意思，后来才发现类似于初高中学的数列通项公式。
按一定规则，给出一个初始值，可以得到它的下一个值。
CountAndSay的初始值是1，读作1个1，因此它的下一个值是11；
11读作2个1，因为有连续2个1，因此它的下一个是21；
21读作1个2和1个1，他的下一个值是1211；
1211的下一个值是111221...
#### Intuition
基本思路，用的StringBuffer存结果。

#### Solution
```Java
public String CountAndSay(int n){
        String str="1";//定义第一个序列是1
        while(n>1){
            str=count(str);
            n--;
        }
        return str;
    }

    public static String count(String str){//传入一个序列 返回读出的序列 即下一个序列
        char[] chars = str.toCharArray();
        char temp = chars[0];//记录当前比较的数字
        StringBuffer sb=new StringBuffer();//存结果
        int count=1;//计数
        for (int i = 1; i < chars.length; i++) {
            if(temp==chars[i]){//如果相同，计数
                count++;
            }else{//如果不同 读出
                sb.append(count);//个数
                sb.append(temp);//值
                temp=chars[i];//更改temp
                count=1;//清除count 准备先一轮计数
            }
        }
        sb.append(count);
        sb.append(temp);
        return sb.toString();
    }
```

## Review
### 97 Things Every Should Know——7th part(8/97)
#### []()


## Tip


## Share
