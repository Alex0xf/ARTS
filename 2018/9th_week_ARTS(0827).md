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
#### [Beware the Share](https://97-things-every-x-should-know.gitbooks.io/97-things-every-programmer-should-know/content/en/thing_07/index.html)
这篇文章讲述了自己为了完善代码将同样的代码封装但最后反而更糟糕的一个故事。好的方法只有再用对了地方才是好地，如果用错了地方还不如不用。

## Tip
### 更方便地使用IDEA
#### 快速入门 基本设置
下面列举几个我觉得很有用的。
1. 自动导包 settings-editor-general-auto import
不必手动导包了，而且IDEA还能智能地帮你把没用的包去除
2. ctrl+滚轮控制字体大小 settings-editor-general（mouse里的change font size...）
3. 提示忽略大小写 settings-editor-general-code completion(case sensitive completion选none)
4. 显示方法间的间隔符 settings-editor-general-appearance(show method separators)
类中相邻方法间会有一条分隔符 看的更清楚一点
5. 取消单行显示tab的操作 settings-editor-general-Editor TABS 去掉show tabs in single row
如果你打开了很多个文件，IDEA默认只显示一行标题栏，放不下的标题就要一个个找很不方便，进行了这个操作后放不下的标题会在下一行显示。
6. 修改类头的注释文档信息 settings-editor-file and templtes-fileheaders
7. 设置编码格式 settings-editor-fileencoding utf-8
IDEA里不是所有的设置都默认设置为UTF-8的，这里可以在选编码格式的地方都选上utf-8
8. 设置自动编译 settings-Build,Excution,Deployment-compile(将多选框未选的两个选上)
一个是代码修改后自动编译，一个是代码块并行编译

#### IDEA 快捷键
很多人是从MyEclipse转到IDEA的，可以选择设置中的kymap模式设置为Eclipse，这样就可以切换回熟悉的eclise的快捷键，但是还有部分不匹配，可以导入jar包来解决。
IDEA的强大处在于它很智能，有很多提示和快捷键。
快捷键有模板可以设置，在kemap的搜索框可以输入功能看快捷键或者直接按快捷键看功能，做一些修改。
常用的快捷键(在导入包之后)：
1. 万能快捷键 alt+enter
2. 智能提示补全 alt+/
3. 执行 alt+R
4. 打开文件所在硬盘的文件夹 ctrl+shift+x
5. 复制当前行到下一行 ctrl+alt+方向下
6. 删除当前行 ctrl+D
7. 向上/下移动该行  alt+上下方向
8. 向下/上开始新的一行 shift+enter/ctrl+shift+enter
9. 回到前一个/后一个的编辑页面 alt+左/右
10. 查看继承关系 F4
11. 格式化代码 ctrl+shift+F
12. 整体代码的前移/后移 选中+tab/(shift+tab)
13. 查看类的结构 ctrl+o
14. 重构 alt+shift+r
15. 大小写转换 ctrl+shift+y
16. 生成构造器/toString/implements methods等 alt+shift+s
17. 选中代码进行tryCatch等 alt+shift+z
18. 查找方法在哪里被调用 ctrl+shift+h

#### IDEA 常用模板(editor-live templtes可以看到 常用iterations/other/output/plain)
1. psvm(public staticvoid main的首字母 ) 生成main方法  类似Ecilpse的main
2. sout 最普通的输出 类似syso
   soutv (veriable)输出最近定义的变量的值 或变量.sout
   soutp (params)输出所在方法的形参
   soutm (method)输出方法名
3. fori  for循环
   iter  forEach
4. list.for 增强型for循环输出list  
5. ifn if(x==null)
   inn if(x!=null)
6. prsf (private final static final)
   psf  (public)

#### IDEA 修改及自定义模板
1. 修改live templtes-other-psvm为main
2. 创建模板
在live templte有个绿色的+号，创建一个自己的templte group，在里面我们可以根据自己的使用习惯创建模板。
  如：test
  description:生成测试方法
  ```JAVA
  public void test $VAR1$(){
      $VAR2$
  }
  ```
  pl
  description:带注释的private String
  ```JAVA
  private String $VAR1$//$VAR2$
  $END$
 ```

## Share
看了耗子叔的专栏文章《高效学习：端正学习态度》，记录一下重要的点。
1. 学习态度：学习是件反人性的事情，必须耐下性子学习，需自律。好的方法可以帮助自己更好推进学习，但不能坚持再好的方法也没用。
2. 主动学习和被动学习：想要更好地获取知识，主动学习比被动学习高效很多。
3. 深度学习和浅度学习：浅度学习没有用，只能给自己营造一种安慰感，焦虑会不降反增。深度学习才是王道。
“你有没有发现，在知识的领域也有阶层之分，那些长期在底层知识阶层的人，需要等着高层的人来喂养，他们长期陷于各种谣言和不准确的信息环境中，于是就导致错误或幼稚的认知，并习惯于那些不费劲儿的轻度学习方式，从而一点点地丧失了深度学习的独立思考能力，从而再也没有能力打破知识阶层的限制，被困在认知底层翻不了身。”
如何深度学习：三个步骤：知识获取 知识缝合 技能转换
4. 学习观念：学习不仅仅是为了找到答案，而更是为了找到方法；学习不仅仅是为了知道，而更是为了思考和理解；学习不仅仅是为了开拓眼界，而更是为了找到自己的未知，为了了解自己；学习不仅仅是为了成长，而更是为了改变自己，改变自己的思考方式，改变自己的思维方式，改变自己与生俱来的那些垃圾和低效的算法。
