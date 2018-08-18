# 5th week ARTS
## Algorithm
### 1.[DNA Pairing](https://forum.freecodecamp.org/t/freecodecamp-algorithm-challenge-guide-dna-pairing/16009)
Problem Explanation:

给定一个只包含ATCG四个字母组合的字符串，要求返回配对的数组，其中"A"对应["A"，“T”],"T"对应["T","A"]，"C"对应["C","G"],"G"对应["G","C"]。
如对于输入的 GCG，相应地返回 [["G", "C"], ["C","G"],["G", "C"]]

#### thoughts
1. 首先需要将字符串转换成字符数组 用split('')即可
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
### 97 Things Every Should Know——4th part(5/97)
#### [Beauty Is in Simplicity](https://97-things-every-x-should-know.gitbooks.io/97-things-every-programmer-should-know/content/en/thing_05/index.html)
Beauty of style and harmony and grace and good rhythm depends on simplicity.
我们在写代码中解决了很多问题：代码的可读性，可维护性，速度以及如何写出优美的代码，而这一切都源于简单性。
对于美的认知，不同类型的人有着不同的看法，作者认为美的基础是简单。好的代码都有一个共性，无论整个应用程序或系统有多复杂，各个部分都必须保持简单。每个模块/对象最好只负责一个功能，责任单一。

## Tip
### 1. mybatis绑定错误-- Invalid bound statement (not found)
#### 问题描述：
使用mybatis的项目在本地可以正常运行，但当使用maven或Jenkins打包部署到远程服务器上时出现了绑定错误，异常信息为：

org.apache.ibatis.binding.BindingException: Invalid bound statement (not found): com.javasm.book.mapper.BookMapper.selectBookList

#### 问题分析和解决方法

首先，给定的异常提示信息并不精准，有多个错误原因都会抛出该异常。mybatis出现这个问题，通常是由Mapper interface和对应的xml文件的定义对应不上引起的，这时就需要仔细检查对比包名、xml中的namespace、接口中的方法名称等是否对应。我之前就因为称忘记在xml标签的id属性中添加方法名或写错方法名而出现这个错误。

出现这个错误时，按以下步骤检查一般就会解决问题：
1：检查xml文件所在package名称是否和Mapper interface所在的包名一一对应；
2：检查xml的namespace是否和xml文件的package名称一一对应；
3：检查方法名称是否对应；
4：去除xml文件中的中文注释；
5：随意在xml文件中加一个空格或者空行然后保存。

我在项目中遇到的问题可以使用最后的解决方法解决：“随意在xml文件中加一个空格或者空行然后保存”，看起来这么怪异的解决方式，实际上是触发了IDE的自动编译功能。由于xml文件在编译的时候，不一定总能立即从源目录复制到class文件的编译目录(MyEclipse经常出这个问题)，有时候你源目录中的xml文件已经修改好了，而class所在的目录里面还是旧的。因此真正确定有效的方式是将正确的xml文件复制到class输出目录。

发现了问题就要从根本上解决，而不应该当出现了问题再去解决。我最后发现Jenkins通过maven把项目打成war包，或者Eclipse通过使用maven命令tomcat7:deploy远程自动部署项目打成的war包，war包里面缺少Mapper对应的xml文件，也就是没有把xml文件打包进去。解决办法是，在pom.xml文件中的build标签中添加如下代码，显示的强制将xml文件打到war包中：

```JAVA
<resources>
        <resource>
            <directory>src/main/java</directory>
            <includes>
                <include> **/ *.xml</include>
            </includes>
            <filtering>false</filtering>
        </resource>
</resources>

```
还有种情况会出这个错误，比如配置xml映射文件需要满足特定要求：
```JAVA
<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean"  
    p:dataSource-ref="dataSource"  p:configLocation="classpath:mybatis-config.xml">
    <property name="mapperLocations">
        <list>
            <value>classpath*:mapper/com/xxx/**/*Mapper.xml</value>
            <value>classpath*:dao/com/xxx/**/*Mapper.xml</value>
        </list>
    </property>
 </bean>
```
如上只有Mapper结尾的xml文件才会被Mybatis扫描到，这个时候如果忘记了这个规则，xml使用了其他名称，如xxxDao.xml。这样xml的配置就不会加入到Mybatis存储配置的一个map对象里去，也会出现 Invalid bound statement 的错误。解决方法就是把xml文件改名即可。

### 2.在maven项目时使用mybatis geneator发生异常
#### 问题描述：Exception getting JDBC Driver

#### 问题分析和解决方法
关于mybatis generator 逆向工程生pojo时发生该异常，抛出的异常主要是由于找不到数据库连接的驱动包。

1. 在MAVEN plugin中单独依赖Mysql驱动包
```JAVA
<plugin>
    <groupId>org.mybatis.generator</groupId>
    <artifactId>mybatis-generator-maven-plugin</artifactId>
    <version>1.3.2</version>
    <configuration>
        <configurationFile>${basedir}/src/main/resources/generatorConfig.xml</configurationFile>
        <overwrite>false</overwrite>
        <verbose>true</verbose>
    </configuration>
    <dependencies>
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>${mysql.version}</version>
        </dependency>
    </dependencies>
</plugin>
```
2. 在generatorConfig.xml中加入数据库驱动包的绝对路径:
<classPathEntry location="xxx\xxx\xxx.jar" /> (xxx\xxx\xxx.jar 为数据库驱动包的绝对路径)

3. 在maven里配置一个命令

mybatis-generator:generate -e

## Share
最近在做一个项目，感慨之前学的东西看起来学会了，真正用起来还差的远。学习时对一个知识的理解和运用很容易就测出来了。不要想着所谓的捷径，踏踏实实学才是最有效的。感觉到压力是因为自己在成长。
