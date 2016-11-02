### Transpose File
Given a text file file.txt, transpose its content.

You may assume that each row has the same number of columns and each field is separated by the ' ' character.

For example, if file.txt has the following content
* 转置一个每行具有相同列数，每个字段都由''字符分隔的文本文件
``` text
name age
alice 21
ryan 30
```
* 输出文件如下
``` text
name alice ryan
age 21 30
```

* 下面这个因为会在每行结尾字段多写一个" "出错,可以考虑在awk中设置if判断，后面再改
``` bash
ALL=`head -n1 file.txt | tr ' ' '\n' |wc -l`
COUNT=1
while [ $COUNT -le $ALL ]; do
      awk -v temp=$COUNT '{ printf("%s ", $temp) }' file.txt
      echo ""
      let COUNT=COUNT+1
done
```
* 上面的升级版在这里，不过当只有一个字母输入时任然会加上一个换行符,知道怎解告诉我一下
``` bash
ALL=`head -n1 file.txt | tr ' ' '\n' | wc -l`
COUNT=1
while [ $COUNT -le $ALL ]; do
         awk -v temp=$COUNT '{ if(NR==1){printf("%s", $temp)}else{printf(" %s", $temp)}}END{printf("\n") }' file.txt
         echo ""
         let COUNT=COUNT+1
done
```
* 这个问题相对较难,下面的答案是Memory Limit Exceeded错误
``` bash
ALL=`head -n1 file.txt | tr ' ' '\n' ` #计算反转后文件的行数
for i in `seq 1 $ALL`
do
     echo `cut -d ' ' -f $i file.txt`     #
done 
```