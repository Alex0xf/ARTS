# 3rd week ARTS
## Algorithm
### [Roman Numeral Converter](https://forum.freecodecamp.org/t/freecodecamp-algorithm-challenge-guide-roman-numeral-converter/16044)
Problem Explanation:
You will create a program that converts an integer to a Roman Numeral(assume the integer smaller than 5000).

 My solution(not the excellent):

```javaScript
function convert(num) {
  //Creating two arrays, one with the Roman Numerals and one with the decimal equivalent for the new forms will be very helpful.
  var decimalValue = [ 1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1 ];
  var romanNumeral = [ 'M', 'CM', 'D', 'CD', 'C', 'XC', 'L', 'XL', 'X', 'IX', 'V', 'IV', 'I' ];

  var romanized = '';
  for (var index = 0; index < decimalValue.length; index++) {
    while (decimalValue[index] <= num) {
      romanized += romanNumeral[index];
      num -= decimalValue[index];
    }
  }

  return romanized;
}

```
#### Problem Explanation:
* We start off by creating two arrays with default conversion with matching indices. These are called decimalValue and romanNumeral. We also create an empty string variable, romanized, which will house the final roman number.
* Using a for loop, we loop through the indicies of the decimalValue array. We continue to loop until while the value at the current index will fit into num.
* Next, we add the roman numeral and decrease num by the decimal equivalent.
* Finally, we return the value of romanized.


## Review
### 1.[What Happens When a Computer Runs Your Life](https://medium.com/s/futurehuman/what-happens-when-a-computer-runs-your-life-4ba7ec152728)
Max Hawkins whose job is a software engineer let an algorithm pick where he lives, what he does—even what tattoo to get.And this time he let the algorithm decide his first tattoo which makes him panicking because the picture and where to put it on is totally random.
In this society where technologies promise humans ever more control over their choices and preferences, Hawkins has decided to surrender his will to the whims of computer algorithms.
He’s created programs that randomly choose where he eats, what he wears, where he lives, what music he listens to, and how he spends his time. In so doing, he says he’s discovered a different kind of freedom.
A couple of months ago, the computer sent him an action asking him to kill a deer. It makes him sinking into a contradiction but he I started thinking about this and he ended up going on a hunting trip with a friend.
I think maybe this is how technology improving us.We will continue to encounter new things. As a technician we should not resist but learn to embrace it even if it is difficult.We should try more and find more so finally we can get more.

## Tip
### 1.MD5(Message-Digest Algorithm 5)
Some time ago,a discussion in Weibo get my attention that some famous websites' username and password be leaked.One of them even not encrypt the password and it cause many users' loss.After that I learns some encryption algorithms and MD5 is one of it.
My thinking:
1. A famous websites should put users' account security in the high place.
2. As users we should raise our safety consciousness,do not use the same password in different websites so that we can reduce our losses if things like that happens.
3. MD5 is a common algorithm to Encrypt password which is effective.At least the company should use one algorithm to Encrypt users' password.



## Share
### 1.[How to read a paper](https://www.albany.edu/spatial/WebsiteFiles/ResearchAdvices/how-to-read-a-paper.pdf)
This is an article [diguage](https://github.com/diguage) recommd us to read.Although I spent almost 2 hours to read it,I still get a lot of useful knowledge.
This paper introduces a 'three-pass' approach to help us read papers more efficiently.
Here is the 'three-pass' approach:
1. The first pass(5~10mins)
* Only read the title,abstract,intruction and headings carefully.
* Glance at the mathematic content.
* Read the Conclusion.
* Glance at the references.
After the first pass,we should know 5Cs:Category,Context,Correctness,Contribution and Clarity.

2. The second pass(1 hour)
* Look carefully at the figures,diagrams and other illustrations in the papers.
* Mark relevant unread references for further reading.
After the first pass,we should grasp the content of the paper.

3. The third pass(4~5hours for beginners,1 hour for the Advanced)
* Try to virtually re-implement the paper(this is the best way to verify the authenticity of  papers) and think about what the paper would like if you write it.
* Tip: The process works best when there is quite a large amount of time between each stage of review.After reading the paper,We should read it again some time later if possible and maybe we can extra the final useful insight that we have never done before.

### 2.Anki
This week I start to use Anki making cards to recite words and I find it really works.Thanks for friends' recommding.
Many people may let go of a good idea, something that someone sincerely recommends, or an opportunity which is hard for others to get.I think maybe this is a main reason that causes people's differences even if they are at the same starting line.I think good things must be executed immediately
or be recorded and we should remember to do it later.So I can make sure that I will not forget (I will remind me by recording it on the mobile calendar if I can't do it right now). Although it may be difficult when we meet the challenges at first, but it will increase a lot of possibilities in our lives. There are many people who have no chance to meet these challenges. You have met and maybe you can resolve them,and it doesn't matter even if you fail.What a great thing!And you can get a sense of accomplishment if you win.A good environment is really rare. I have gained a lot since I joined the readers of Chen Hao,and I thank all the friends in the weixin group.
