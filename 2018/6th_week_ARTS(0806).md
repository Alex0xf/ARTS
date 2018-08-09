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
Spring 依赖注入
所谓的依赖注入，其实是当一个bean实例引用到了另外一个bean实例时spring容器帮助我们创建依赖bean实例并注入（传递）到另一个bean中，如上述案例中的AccountService依赖于AccountDao，Spring容器会在创建AccountService的实现类和AccountDao的实现类后，把AccountDao的实现类注入AccountService实例中，下面分别介绍setter注入和构造函数注入。

## Share
