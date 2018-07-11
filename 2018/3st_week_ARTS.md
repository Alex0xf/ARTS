# 3rd week ARTS
## Algorithm
### [Roman Numeral Converter](https://forum.freecodecamp.org/t/freecodecamp-algorithm-challenge-guide-roman-numeral-converter/16044)
Problem Explanation:
You will create a program that converts an integer to a Roman Numeral(assume the integer smaller than 5000).

 My solution:

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
Finally, we return the value of romanized.


## Review
### 1.[What Happens When a Computer Runs Your Life](https://medium.com/s/futurehuman/what-happens-when-a-computer-runs-your-life-4ba7ec152728)
Max Hawkins whose job is a software engineer let an algorithm pick where he lives, what he does—even what tattoo to get.And this time he let the algorithm decide his first tattoo which makes him panicking because the picture and where to put it on is totally random.
In a world where technologies promise humans ever more control over their choices and preferences, Hawkins has decided to surrender his will to the whims of computer algorithms.
He’s created programs that randomly choose where he eats, what he wears, where he lives, what music he listens to, and how he spends his time. In so doing, he says he’s discovered a different kind of freedom.


## Tip
### 1.


## Share
