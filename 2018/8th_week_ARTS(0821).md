# 8th week ARTS
## Algorithm
### 1.[Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/solution/)
Problem Explanation:
Write a function to find the longest common prefix string amongst an array of strings.
If there is no common prefix, return an empty string "".
All given inputs are in lowercase letters a-z.

#### Intuition
返回一个String型数组的共同前缀
首先想法是获得一组字符串的共同前缀只是获得两个字符串前缀的变形，因此先考虑怎么拿到两个字符串的共同前缀。
最基本的方法就是遍历比较，先判断是否非空，是的话再将字符串转成char型数组一个个向后比较字母，把前n个相同的字母存进一个变量中，一旦遇到不同的字母则停止添加并结束循环。这样两个字符串的共同前缀就拿到了，再用拿到的这个共同前缀去和下一个字符串比拿到他们的共同前缀，一直比较到最后一个字符串就可以拿到所有字符串的共同前缀了。
但这种方法要一个个比，时间复杂度肯定不行，是O(n2)，最差的情况数组中每个字符串都一样，这样就需要比较n的平方次。
这种是一个一个加的方式获得共同前缀，另一种类似的是默认第一个字符串为共同前缀，看第二个字符串indexOf()第一个字符串是否为0，若不是则每次将默认的共同前缀去掉最后一个字母直至拿到共同前缀或者减为空。


#### Solution
```JAVA
public static String longestCommonPrefix(String[] strs) {
  if(strs.length==0)return "";//判断是否为空
  String result="";//用来存当前比较的两个值的共同前缀
  for(int i=0;i<strs.length-1;i++){
    result="";// 每次比较前先清空
    if(strs[i].isEmpty())return "";//如果循环中有元素为空则共同前缀为空
    else{//如果不为空 开始比较
        //x用来记录当前循环的数组元素 y为下一个 比较x和y
        String x=strs[i];
        String y=strs[i+1];
        // 获取当前比较的两个字符串的共同前缀
        for(int j=0;j<x.length()&&j<y.length();j++){
       //比较当前两个字符串的第j个字母是否相等 相等则追加在result后并后移 不等则结束此次比较
            if(x.charAt(j)==y.charAt(j)){
                result+=x.charAt(j);
            }else{break;}
        }
        strs[i+1]=result;//把共同前缀赋值给Y 接下来直接比较Y和下一个元素
    }
}
return result;
       }
```
#### Optimize
用分治的思想去实现。
![](https://leetcode.com/media/original_images/14_lcp_diviso_et_lmpera.png)
```JAVA
public String longestCommonPrefix(String[] strs) {
    if (strs == null || strs.length == 0) return "";    
        return longestCommonPrefix(strs, 0 , strs.length - 1);
}

private String longestCommonPrefix(String[] strs, int l, int r) {
    if (l == r) {
        return strs[l];
    }
    else {
        int mid = (l + r)/2;
        String lcpLeft =   longestCommonPrefix(strs, l , mid);
        String lcpRight =  longestCommonPrefix(strs, mid + 1,r);
        return commonPrefix(lcpLeft, lcpRight);
   }
}

String commonPrefix(String left,String right) {
    int min = Math.min(left.length(), right.length());       
    for (int i = 0; i < min; i++) {
        if ( left.charAt(i) != right.charAt(i) )
            return left.substring(0, i);
    }
    return left.substring(0, min);
}

```

## Review
### 97 Things Every Should Know——5th part(6/97)
#### [Before You Refactor](https://97-things-every-x-should-know.gitbooks.io/97-things-every-programmer-should-know/content/en/thing_06/index.html)
这篇文章讲了在程序员需要重构代码前需要考虑的几点事项：
1. 重组的最佳方法始于评估现有代码库和针对该代码编写的测试。取长补短。
2. 避免重写一切的。最好尽可能多地重用代码。
3. 最好一点点更改，不要一次就完成一个大的更改。
4. 每次迭代后，确保现有测试通过非常重要。
5. 不要因为代码的风格或结构不符合您的个人偏好而重构别人的代码。
6. 除非成本效益分析表明新语言或框架将导致功能，可维护性或生产力方面的显着改进，否则最好保持原样，别总想着用新技术。
7. 重构之前想清楚，重构并不总能保证新代码会比以前的更好。

## Tip
### 1.浏览器禁止跨域访问
#### 问题描述：当使用ajax访问远程服务器时，请求失败，浏览器报错。这是出于安全的考虑，默认禁止跨域访问导致的
#### 报错信息：No 'Access-Control-Allow-Origin' header is present on the requested resource.
#### 解决办法

1. 使用jsonp格式， 如jquery中ajax请求参数   dataType:'JSONP'。
2. server端设置一个 response.setHeader("Access-Control-Allow-Origin", * )

### 2.[在IDEA中实战Git](https://blog.csdn.net/autfish/article/details/52513465)
最近在用git，而且在使用的IDE是IntelliJ IDEA，这篇文章介绍了在IDEA中各个场景中如何使用git，很棒。

### 3.如何在IntelliJ IDEA中忽略不必要提交的文件
最近发现IDEA在提交项目到本地仓库的时候，会把.idea文件夹中的内容也提交上去，这里面放的是一些项目的配置信息，包括历史记录，版本控制信息等。可以不传到Git上面去。
这个时候就需要编写.gitignore文件来忽略提交这些文件。在IDEA中有一个插件.ignore可以帮我们做这件事。
下载完重启之后，在项目上右键->New ->.ignore file ->.gitignore file(Git)即可完成操作。文件名变灰即成功被忽略的标志。整个操作很方便快捷。
下面是一些.gitignore文件忽略的匹配规则：

```gitignore
*.a       # 忽略所有 .a 结尾的文件
!lib.a    # 但 lib.a 除外
/TODO     # 仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO
build/    # 忽略 build/ 目录下的所有文件
doc/*.txt # 会忽略 doc/notes.txt 但不包括 doc/server/arch.txt
```
.gitignore只能忽略那些原来没有被track的文件，如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的。那么解决方法就是先把本地缓存删除（改变成未track状态），然后再提交：
输入：

```git
git rm -r –-cached filePath
git commit -m “remove xx”
或者：
git rm -r –cached .
git add .
git commit -m “update .gitignore”
```
来解释下几个参数 -r 是删除文件夹及其子目录 –cached 是删除暂存区里的文件而不删除工作区里的文件，第一种是删除某个文件，第二种方法就把所有暂存区里的文件删了，再加一遍，相当于更新了一遍。

## Share
### [mybatis传参](http://www.cnblogs.com/mingyue1818/p/3714162.html)
在做项目的时候很容易碰到的问题。我在项目中传参一直出现问题，后来发现是因为配置了page helper插件忘记注释导致它自动更改我的sql语句。不过在找错的过程中也顺带理了一下mybatis传参的几种情况：

一、单个参数：
```JAVA
public List<XXBean> getXXBeanList(String xxCode);  

<select id="getXXXBeanList" parameterType="java.lang.String" resultType="XXBean">

　　select t.* from tableName t where t.id= #{id}  

</select>  

其中方法名和ID一致，#{}中的参数名与方法中的参数名一直， 我这里采用的是XXXBean是采用的短名字,

select 后的字段列表要和bean中的属性名一致， 如果不一致的可以用 as 来补充。
```
二、多参数：
```JAVA
public List<XXXBean> getXXXBeanList(String xxId, String xxCode);  

<select id="getXXXBeanList" resultType="XXBean">

　　select t.* from tableName where id = #{0} and name = #{1}  

</select>  

由于是多参数那么就不能使用parameterType， 改用#｛index｝是第几个就用第几个的索引，索引从0开始
```
三、Map封装多参数：
```JAVA
public List<XXXBean> getXXXBeanList(HashMap map);  

<select id="getXXXBeanList" parameterType="hashmap" resultType="XXBean">

　　select 字段... from XXX where id=#{xxId} code = #{xxCode}  

</select>  

其中hashmap是mybatis自己配置好的直接使用就行。map中key的名字是那个就在#{}使用那个，map如何封装就不用了我说了吧。
```
四、List封装in：
```JAVA
public List<XXXBean> getXXXBeanList(List<String> list);  

<select id="getXXXBeanList" resultType="XXBean">
　　select 字段... from XXX where id in
　　<foreach item="item" index="index" collection="list" open="(" separator="," close=")">  
　　　　#{item}  
　　</foreach>  
</select>  

foreach 最后的效果是select 字段... from XXX where id in ('1','2','3','4')
```
五、多参数传递之注解方式示：
```JAVA
例子：

public AddrInfo getAddrInfo(@Param("corpId")int corpId, @Param("addrId")int addrId);

xml配置这样写：

<select id="getAddrInfo"  resultMap="com.xxx.xxx.AddrInfo">
       SELECT * FROM addr__info
　　　　where addr_id=#{addrId} and corp_id=#{corpId}
</select>

以前在<select>语句中要带parameterType的，现在可以不要这样写。
```
六、selectList()只能传递一个参数，但实际所需参数既要包含String类型，又要包含List类型时的处理方法：
```JAVA
List<String> list_3 = new ArrayList<String>();
Map<String, Object> map2 = new HashMap<String, Object>();

list.add("1");

list.add("2");
map2.put("list", list); //网址id

map2.put("siteTag", "0");//网址类型
```
```JAVA
public List<SysWeb> getSysInfo(Map<String, Object> map2) {
　　return getSqlSession().selectList("sysweb.getSysInfo", map2);
}
```
```JAVA
<select id="getSysInfo" parameterType="java.util.Map" resultType="SysWeb">
　　select t.sysSiteId, t.siteName, t1.mzNum as siteTagNum, t1.mzName as siteTag, t.url, t.iconPath
   from TD_WEB_SYSSITE t
   left join TD_MZ_MZDY t1 on t1.mzNum = t.siteTag and t1.mzType = 10
   WHERE t.siteTag = #{siteTag }
   and t.sysSiteId not in
   <foreach collection="list" item="item" index="index" open="(" close=")" separator=",">
       #{item}
   </foreach>
 </select>
 ```
