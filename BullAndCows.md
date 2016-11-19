### Bulls and Cows
You are playing the following Bulls and Cows game with your friend: You write down a number and ask your friend to guess what the number is. Each time your friend makes a guess, you provide a hint that indicates how many digits in said guess match your secret number exactly in both digit and position (called "bulls") and how many digits match the secret number but locate in the wrong position (called "cows"). Your friend will use successive guesses and hints to eventually derive the secret number.

* 你和你的朋友一起玩下面的公牛和母牛游戏：你写下一个数字，请你的朋友猜测这个数字是多少。每次你的朋友做一个猜测，你提供一个提示，表示该猜测中的数字与您的秘密数字完全匹配的数字和位置（称为“公牛”）和多少位数匹配的秘密号码，但位于错误的位置（称为“母牛”）。您的朋友将使用连续的猜测和提示来最终导出密码。写一个函数根据秘密数字和朋友的猜测返回一个提示，使用A表示公牛，B表示牛。假设秘密号码和你的朋友的猜测只包含数字，并且它们的长度总是相等的。

```
Secret number: “1807”
Firend‘s guess: "7810"
提示：1头公牛和3头母牛。 （公牛是8，母牛是0,1和7, return "1A3B"

Secret number: "1123"
Firend's guess: "0111"
密码和朋友的猜测可能包含重复的数字,在这种情况下，朋友猜中的第1个是牛，第2个或第3个是牛，并且你的函数应该返回“1A1B"
```

``` java
public class Solution {
   public String getHint(String secret, String guess) {
      int bulls = 0;
      int cows = 0;
      int[] numbers = new int[10];
      for(int i=0;i<secret.length();i++) {
         if(secret.charAt(i) == guess.charAt(i)) {
            bulls++;
         }else {
            if(numbers[secret.charAt(i) - '0']-- >0) cows++;
            if(numbers[guess.charAt(i) - '0']++ <0) cows++;
         }
      }
      return bulls +"A" +cows + "B";
   }
}
        
```
* 上面的方法是使用chaAt()依次遍历，可以将secret和guess转化成char类型数组，这样效率更高
``` python
class Solution(object):
    def getHint(self, secret, guess):
        """
        :type secret: str
        :type guess: str
        :rtype: str
        """
        bulls, cows = 0, 0
        s, g = {}, {} #it's hashtable
        for i in xrange(len(secret)):
            if secret[i] == guess[i]:
                bulls+=1
            else:
                s[secret[i]] = s.get(secret[i], 0) +1 #每次加1，使用get()避免字典里无此值抛出错误
                g[guess[i]] = g.get(guess[i], 0) + 1
        for k in s:
            if k in g:
                cows+= min(s[k], g[k]) #去重
        return  "{}A{}B".format(bulls,cows)
                
```

``` python
class Solution(object):
    def getHint(self, secret, guess):
        """
        :type secret: str
        :type guess: str
        :rtype: str
        """
        s, g = Counter(secret), Counter(guess) # 生成值-个数的字典
        a = sum(i==j for i, j in zip(secret, guess))
        return "%sA%sB" % (a, sum((s & g).values()) -a)
```