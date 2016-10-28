### Valid Phone Number 
Given a text file file.txt that contains list of phone numbers (one per line), write a one liner bash script to print all valid phone numbers.

You may assume that a valid phone number must appear in one of the following two formats: (xxx) xxx-xxxx or xxx-xxx-xxxx. (x means a digit)

You may also assume each line in the text file must not contain leading or trailing white spaces.

* 有一个文本文件每行存储一个电话号码如下所是，正确的格式是（xxx）xxx-xxxx 或者 xxx-xxx-xxxx，输出正确格式的号码
* 测试文本
``` text             
987-123-4567
123 456 7890
(123) 456-7890
```
* 输出
``` 
987-123-4567
(123) 456-7890
```
 
``` bash
$ sed -nr "/^([0-9]{3}-|\([0-9]{3}\) )[0-9]{3}-[0-9]{4}$/p" file.txt

$ grep -P '^(\d{3}\-|\(\d{3}\) )\d{3}\-\d{4}' file.txt

$ awk "/^([0-9]{3}-|\([0-9]{3}\) )[0-9]{3}-[0-9]{4}/" file.txt
```
* 上面的代码只有第一个在leetcode通过，其他两个在我的系统可以通过(Test System:Fedora 23)
