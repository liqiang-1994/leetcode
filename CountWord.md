
### shell script 1
Write a bash script to calculate the frequency of each word in a text file words.txt.

For simplicity sake, you may assume:

words.txt contains only lowercase characters and space ' ' characters.
Each word must consist of lowercase characters only.
Words are separated by one or more whitespace characters.
For example, assume that words.txt has the following content:

* 编写一个脚本计算文本文件word.txt中单词出现的频率，从多到少输出

* Example 

这是测试文件word.txt
``` txt
the day is sunny the the
the sunny is is
```
* 这是测试输出
```
the 4
is 3
sunny 2
day 1
```
* 思路：需要先用grep -E参数用正则把每个单词取出来(-o参数只输出匹配的)，再进行排序输出，通过uniq -c 命令可去重后(-c参数会在行首添加该单词出现的次数)再排序(sort -r逆序输出)，最后用awk调整列
``` bash
$ grep -Eo  '[a-z]+' w.txt| sort | uniq -c | sort -r |awk '{print $2"  "$1}'
```
