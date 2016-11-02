### Tenth
How would you print just the 10th line of a file?

For example, assume that file.txt has the following content:

* 如何输出一个文本文件的第10行

```
Line 1
Line 2
Line 3
Line 4
Line 5
Line 6
Line 7
Line 8
Line 9
Line 10
```
* 下面是输出
```
Line 10
```

* 如何输出一个文本文件的第十行，这个相对简单，可以采用sed直接定位到该行，也可以通过head和tail连用截断文本的方法
``` bash
$ sed -n "10p" word.txt #输出单独一行

$ sed -n "5,10p" word.txt #输出多行

$ head -n 10 word.txt | tail -n 1 #输出第10行(leetcode这行没有通过)

$ head -n 10 word.txt| tail -n +10 #输出第10行 (上面和这个是不是很像，如果困惑的话可以看看我的博客) 

$ tail -n +10 word.txt| head -n 1 #输出第10行

$ tail -n 3 word.txt |head -n 1 #这条命令的局限在于事先必须知道文本的总行数(wc -l word.txt)

```