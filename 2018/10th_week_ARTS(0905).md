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
#### [The Boy Scout Rule](https://97-things-every-x-should-know.gitbooks.io/97-things-every-programmer-should-know/content/en/thing_08/index.html)
童子军又一条规则，离开营地的时候一定要让这里比你刚开始发现的时候干净。当你发现脏乱的时候，无论是谁弄的，你都要去清理它。
Try and leave this world a little better than you found it.
这些规则同样可以在编程中适用，检查模块时让它比检查时更清楚，无论原作者是谁。如果大家都做出一些努力，都改进模块，那么事情会简单很多。
这个规则并不是很难，不是需要你完善之后让代码变得完美，你只需要做一点，使它比之前好就够了。在一个团队应该相互帮助，共同完善代码。只考虑自己从长远来说还是有害的。

## Tip
### 互联网分布式示意图
![](http://pbok9izql.bkt.clouddn.com/%E4%BA%92%E8%81%94%E7%BD%91%E5%88%86%E5%B8%83%E5%BC%8F%E7%A4%BA%E6%84%8F%E5%9B%BE.png)

## Share
[The power of doing nothing at all](https://medium.com/swlh/the-power-of-doing-nothing-at-all-73eeea488b8b)
什么也不做的力量
现在身边的人似乎总是忙碌着，被焦虑吞噬，生怕自己停下来就会损失很多东西。但在拼命地忙碌之前大部分人都不知道自己究竟是为了什么，很多刚开始明确目标的人在忙碌中也忘记了自己的初心。我们已经成长为潜意识地用一个人工作了多少时间，赚了多少钱来衡量一个人的价值。因此我们需要时不时停下来，去留给自己一些时间用来思考，缓解，放空，或者什么也不做。
Doing what matters vs. busy-bragging。
在运营微软的多年中，盖茨每年会两次退回到为期一周的思考周期 - 不是休假，而是实际上无所事事的时间段。
盖茨对他的思维周非常坚定，家人，朋友和微软员工都被禁止了。今天，盖茨将微软成功的大部分内容归功于他在无所事事时偶然发现的重要创意和概念。

[高效学习：源头、原理和知识地图]()
首先，挑选知识和信息源的重要性，因为优质的信息源可以让你事半功倍。英语要学好，坚持看英文文档而不是每次看别人翻译好的。其次，一定要注重基础和原理，基础打牢，学什么都快，而学得快就会学得多，学得多，就会思考得多，对比得多，结果是学得更快。
最后，学习时一定要使用知识图，学习并不是为了要记忆那些知识点，而是为了要找到一个知识的地图，你在这个地图上能通过关键路径找到你想要的答案。只要掌握了好的方法，你能做到的话，你的学习效率一定提升很快。
