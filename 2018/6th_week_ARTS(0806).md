# 6th week ARTS
## Algorithm
### [Pig Latin](https://forum.freecodecamp.org/t/freecodecamp-algorithm-challenge-guide-pig-latin/16039)
Problem Explanation:
You need to create a program that will translate from English to Pig Latin. Pig Latin takes the first consonant (or consonant cluster) of an English word, moves it to the end of the word and suffixes an “ay”. If a word begins with a vowel you just add “way” to the end. It might not be obvious but you need to remove all the consonants up to the first vowel in case the word does not start with a vowel.

把指定的字符串按一定规则翻译成 pig latin。
Pig Latin的定义：
1. 如果单词以元音字母（a/e/i/o/u）开始，在词尾添加 "way" 。
2. 否则，把该单词的第一个辅音(即非元音)或辅音丛（连续辅音组成的字符串）移到词尾，然后加上后缀 "ay"。
#### thoughts
看到这题的基本想法：
1. 首先判断单词是否以元音字母开头:将字符串型的单词转成数组，定义一个String类Vowels="aeiou",用indexOf（）判断单词的首字母是否为元音
2. 若首个字母不为元音字母（即为辅音字母），则将其复制并添加进原字符串尾部，继续判断下一个
3. 循环结束，截取字符串并加上“ay”,结束循环

#### Solution:
这是在freecodecamp上做的一题，上面都是用JS做的，自己不太熟练所以先用java写了一遍。

Java代码
```java
public static String changeToPigLatin(String word) {
		// 首先判断单词是否以元音字母开头:
		//1.定义一个String类变量Vowels="aeiou"
		String vowelsString="aeiou";
		//2.将str转成数组并判断第一个字母是否为元音 用indexOf（）判断
		char[]wordChar= word.toCharArray();
		int i=0;
		if(vowelsString.indexOf(wordChar[0])!=-1){
			//若以元音开头 则返回word+"way"
			return word+"way";
		}else{//若以辅音开头
			while(vowelsString.indexOf(wordChar[i])==-1&&i<wordChar.length-1){
				//第i个单词首字母仍为辅音（即开头连续i+1个辅音字母）
				word=word+wordChar[i];//将循环的辅音字母添加到字符串尾部
				i++;
			}
		}
		return word.substring(i)+"ay";//将前面连续的辅音首部舍去 并在尾部+"ay"
	}
```

JS代码

```javaScript
function translate(wordChar) {
  //定义元音组成的字符串
  var vowelsString="aeiou";
  //若单词以元音开始 直接在单词结尾加way
  if(vowelsString.indexOf(wordChar[0])!=-1){
    return wordChar+"way";
  }else{//若第一个字母是辅音
   var i=0;
   var temp= wordChar.split('');
   while(vowelsString.indexOf(wordChar[i])==-1&&i<wordChar.length-1){
     //若当前循环的字符型数组首字母为辅音
    //将首字母加到尾部
    temp.push(wordChar[i]);
    i++;
   } temp=temp.join("");
    return temp.substr(i)+"ay";
  }
}

```

#### optimize
可以优化的地方：
看了网上的解法很多用到了正则表达式，效率会快一些。还有很多高级解法行数很少但是阅读起来十分不友好，我觉得我还是先把基础的解法弄熟练比较重要，不去追求写出看上去简便实则需要花费很长时间的解法。
```javaScript
function translatePigLatin(str) {
  // Create variables to be used
  var pigLatin = '';
  var regex = /[aeiou]/gi;
  // Check if the first character is a vowel
  if (str[0].match(regex)) {
    pigLatin = str + 'way';
  } else {
    // Find how many consonants before the first vowel.
    var vowelIndice = str.indexOf(str.match(regex)[0]);
    // Take the string from the first vowel to the last char
    // then add the consonants that were previously omitted and add the ending.
    pigLatin = str.substr(vowelIndice) + str.substr(0, vowelIndice) + 'ay';
  }
  return pigLatin;
}
// test here
translatePigLatin("consonant");
```

## Review
### 97 Things Every Should Know——3rd part(4/97)
#### [Automate Your Coding Standard](https://97-things-every-x-should-know.gitbooks.io/97-things-every-programmer-should-know/content/en/thing_04/index.html)
这篇文章说到团队合作时编码标准制定和执行很重要，这样可以避免很多的bug，然而人为去遵守这些规则很难。因此比较好的方式是利用自动化方式来实现编码标准的统一和检测。
在编码标准化方面，作者给了几个建议：
1. 确保代码格式化工具会自动执行
2. 使用工具扫描代码，一旦发现不符合标准，停止写代码并立刻改正
3. 学会配置这些工具以便你为自己的项目编码格式化
4. 除了确保格式的正确性，还要确保结果的正确性

## Tip
### 1.[关于Spring IOC (DI-依赖注入)你需要知道的一切](https://blog.csdn.net/javazejian/article/details/54561302)
在刚接触Spring框架时我有很多困惑，这篇文章对于Spring中依赖注入各种概念，过程，使用讲解得非常清楚，还讲到了java代码在发展过程中发现的问题和一步步解决的过程。如何达到松耦合，少侵入的目标。下面记录一些我觉得比较好的知识点，想要详细了解的可以看下原文章。

#### Spring IOC 的原理概述
1. 一开始我们写Java代码在需要使用一个对象的方法时经常会new对象，比如在bookServiceImpl类中用到bookDaoImpl类的方法，我们需要new一个bookDaoImpl对象然后再调用对应方法。这很明显耦合度过高，不符合原则。由此而来的解决方案是面向接口的编程，BookServiceImpl类中由原来直接与BookDaoImp打交互变为BookDao，即使BookDao最终实现依然是BookDaoImp。当替换bookDaoImpl类，也只需修改bookDao指向新的实现类。
![](http://pbok9izql.bkt.clouddn.com/6th_ARTS_impl.png)

2. 但是代码依旧存在入侵性和一定程度的耦合性，比如在修改bookDao的实现类时，仍然需求修改BookServiceImpl的内部代码。因此我们仍需要寻找一种方式，它可以令开发者在无需触及BookServiceImpl内容代码的情况下实现修改bookDao的实现类，以便达到最低的耦合度和最少入侵的目的。这种技术实现了，叫做反射（反射是一种根据给出的完整类名[字符串方式]来动态地生成对象，这种编程方式可以让对象在生成时才决定到底是哪一种对象）。因此可以这样假设，在某个配置文件，该文件已写好bookDaoImpl类的完全限定名称，通过读取该文件而获取到bookDao的真正实现类完全限定名称，然后通过反射技术在运行时动态生成该类，最终赋值给bookDao接口，也就解决了刚才的存在问题。

这样做的好处是在替换bookDao实现类的情况只需修改配置文件的内容而无需触及BookServiceImpl的内部代码，从而把代码修改的过程转到配置文件中，相当于BookServiceImpl及其内部的bookDao通过配置文件与bookDao的实现类进行关联，这样BookServiceImpl与bookDao的实现类间也就实现了解耦合。

![](http://pbok9izql.bkt.clouddn.com/6th_ARTS_IOC.png)
3. Spring IOC 也是一个java对象，在某些特定的时间被创建后，可以进行对其他对象的控制，包括初始化、创建、销毁等。简单地理解，在上述过程中，我们通过配置文件配置了BookDaoImpl实现类的完全限定名称，然后利用反射在运行时为BookDao创建实际实现类，包括BookServiceImpl的创建，Spring的IOC容器都会帮我们完成，而我们唯一要做的就是把需要创建的类和其他类依赖的类以配置文件的方式告诉IOC容器需要创建那些类和注入哪些类即可。Spring通过这种控制反转（IoC）的设计模式促进了松耦合，这种方式使一个对象依赖其它对象时会通过被动的方式传送进来（如BookServiceImpl被创建时，其依赖的BookDao的实现类也会同时被注入BookServiceImpl中），而不是通过手动创建这些类。我们可以把IoC模式看做是工厂模式的升华，可以把IoC看作是一个大工厂，只不过这个大工厂里要生成的对象都是在配置文件(XML)中给出定义的，然后利用Java的反射技术，根据XML中给出的类名生成相应的对象。从某种程度上来说，IoC相当于把在工厂方法里通过硬编码创建对象的代码，改变为由XML文件来定义，也就是把工厂和对象生成这两者独立分隔开来，目的就是提高灵活性和可维护性，更是达到最低的耦合度，因此我们要明白所谓为的IOC就将对象的创建权,交由Spring完成，从此解放手动创建对象的过程，同时让类与类间的关系到达最低耦合度。

#### Spring 容器装配Bean XML配置方式和注解配置方式
1. XML配置方式（在xml文件中通过bean标签的方式装配,也可以用@configuration和@Bean，但不方便进行管理）
使用时，通过ClassPathXmlApplicationContext去加载spring的配置文件，接着获取想要的实例bean并调用相应方法执行
2. 注解方式(见后文)

#### 依赖注入
所谓的依赖注入，其实是当一个bean实例引用到了另外一个bean实例时spring容器帮助我们创建依赖bean实例并注入（传递）到另一个bean中，如AccountService依赖于AccountDao，Spring容器会在创建AccountService的实现类和AccountDao的实现类后，把AccountDao的实现类注入AccountService实例中。

##### 注入方式
1. setter注入：需要有set方法
2. 构造函数注入：通过构造方法注入依赖
3. 循环依赖：不建议在配置文件中使用循环依赖
4. **自动装配（自动向Bean注入依赖）和注解注入（@Autowired&@Resource&@Value）**
Spring的自动装配有三种模式：byTpye(根据类型)，byName(根据名称)、constructor(根据构造函数)。
	* 基于xml的自动装配;

	< bean id="userService" autowire="byType/byName/constructor" class="com.zejian.spring.springIoc.service.impl.UserServiceImpl" />
	* 基于注解的自动装配(使用之前需打开扫描/注解);
	基于@Autowired注解的自动装配:无需set方法，默认按类型装配;
  基于@Resource注解的自动装配:默认按 byName;
	基于@Value注解的自动装配以及properties文件读取;

JDBC.property文件
```JAVA
jdbc.driver=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://127.0.0.1:3306/test?characterEncoding=UTF-8&allowMultiQueries=true
jdbc.username=root
jdbc.password=root
```

利用注解@Value获取jdbc.url和jdbc.username的值，实现如下：
```JAVA
public class UserServiceImpl implements UserService {
    //标注成员变量
    @Autowired
    @Qualifier("userDao")
    private UserDao userDao;
    //占位符方式
    @Value("${jdbc.url}")
    private String url;
    //SpEL表达方式，其中代表xml配置文件中的id值configProperties
    @Value("#{configProperties['jdbc.username']}")
    private String userName;

    @Override
    public void done(){
        System.out.println("url:"+url);
        System.out.println("username:"+userName);
        userDao.done();
    }
}
```

基于xml的配置如下：
```XML
	<!--基于占位符方式 配置单个properties -->
     <!--<context:property-placeholder location="conf/jdbc.properties"/>-->
     <!--基于占位符方式 配置多个properties -->
     <bean id="propertyConfigurer" class="org.springframework.beans.factory.config.PreferencesPlaceholderConfigurer">
         <property name="location" value="conf/jdbc.properties"/>
     </bean>

     <!--基于SpEL表达式 配置多个properties id值为configProperties 提供java代码中使用 -->
     <bean id="configProperties" class="org.springframework.beans.factory.config.PropertiesFactoryBean">
         <property name="locations">
             <list>
                 <value>classpath:/conf/jdbc.properties</value>
             </list>
         </property>
     </bean>

     <!--基于SpEL表达式 配置单个properties -->
     <!--<util:properties id="configProperties" location="classpath:conf/jdbc.properties"/>-->

```

#### IOC容器管理Bean
##### Bean的命名
每个交给SpringBean创建的Bean都需要有name/id属性，没有设置则系统会自动分配一个,通过Bean的名称，我们可以在其他类中查找该类并使用它。

注解声明简便了我们的操作，使我们不需要每次在xml文件中手动输入bean的名字。

在xml声明注解驱动后，我们可以使用（@Service）、（@Repository）和（@Component）声明bookServiceImpl、bookDaoImpl等特殊的类，这样也方便识别,然后使用@Autowired注解注入bookDao等。

注意在注解声明前需要明确告诉Spring注解的Bean在那些包下，因此需要添加包扫描机制（很容易添加）。

##### Bean实例化方法
无参/带参构造方法/工厂静态方法/工厂实例方法，具体的方法不在这里写了，想了解的可以看原文。

##### Bean的重写机制
id相同的bean默认加载最后添加的;

子文件优先级高于父文件

##### Bean的作用域
1. singletonBean：永远只有一个实例
2. prototypeBean:每次被获取都会创建新的实例
3. RequestBean:同一次Http请求过程中是同一个实例，当请求结束随着销毁，在新的Http请求则创建新的实例
4. SessionBean:同一个会话中是同一个实例，不同的会话中SessionBean实例不同

#### IOC 与依赖注入的区别
IOC:控制反转:将对象的创建权,由Spring管理.
DI(依赖注入):在Spring创建对象的过程中,把对象依赖的属性注入到类中。

## Share
### 个人感想
今天在一个群里看大家讨论一件问题，对于一个兴趣是否需要去研究它内在的原理，性能，参数等等，然后不断追求更好的这些参数。还是说一切靠自己的切身感受，自己去接触然后选择自己觉得好的。

我发表了我的看法，这两者其实并不矛盾，可以互为补充。我们对任何事物都是从未知到了解然后熟悉最后精通的过程。刚开始接触一个东西其中很多原理我们不知道，所以需要去了解，去探索。当研究了一段时间后我们会窥得其中一二，这时候是否对它仍感兴趣或者已经觉得无聊大体可以知道了，有兴趣就深研究，没兴趣就知道个大概就可以。要明白这些兴趣/技术最后都是为自己服务，在不断研究深入了解的过程中感到开心激动快乐才是人与它的正向关系，我们不应该在深入的过程反被它所束缚，这与我们的初心违背。在过程中又可以通过已经习得的专业知识来指引自己，提高自己的判断力，更清楚自己的喜好，也帮助自己在某一个或几个专一领域更深入。

另外，如果一开始是喜欢的，但是后来又不喜欢了，不必有太大的包袱。人在不同阶段的体会是不同的，很可能过段时间之后重新看一个东西会有完全不一样的体会，这时候之前的研究就会派上大用场，带你走上一个更高的台阶。若是你认清了自己确实不适合，及时止损也不失为一种好的措施，起码曾经经历过。
