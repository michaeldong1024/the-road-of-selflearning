# 什么是正则表达式

​	一组特殊符号组成的表达式，用于描述某种规则。该应用场景生活中随处可见。

​	例如：让有志青年过上体面的生活，这里面就由规则，即有志青年。

# 正则表达式的作用，以及使用场景

​	1.用于从字符串中匹配满足某种规则的内容，多数用于爬虫应用程序

​	2.判断字符串串内容是否满足某种规则，多用于严重用户输入。例如密码是否规范，手机号是否正确等

学习重点

​	正则是一堆特殊符号组成的，我们主要学习的就是这些特殊符号



| 元字符      | 描述                                                         |
| ----------- | :----------------------------------------------------------- |
| \           | 将下一个字符标记符、或一个向后引用、或一个八进制转义符。例如，“\\n”匹配\n。“\n”匹配换行符。序列“\\”匹配“\”而“\(”则匹配“(”。即相当于多种编程语言中都有的“转义字符”的概念。 |
| ^           | 匹配输入字行首。如果设置了RegExp对象的Multiline属性，^也匹配“\n”或“\r”之后的位置。 |
| $           | 匹配输入行尾。如果设置了RegExp对象的Multiline属性，$也匹配“\n”或“\r”之前的位置。 |
| *           | 匹配前面的子表达式任意次。例如，zo*能匹配“z”，也能匹配“zo”以及“zoo”。*等价于{0,}。 |
| +           | 匹配前面的子表达式一次或多次(大于等于1次）。例如，“zo+”能匹配“zo”以及“zoo”，但不能匹配“z”。+等价于{1,}。 |
| {*n*}       | *n*是一个非负整数。匹配确定的*n*次。例如，“o{2}”不能匹配“Bob”中的“o”，但是能匹配“food”中的两个o。 |
| {*n*,}      | *n*是一个非负整数。至少匹配*n*次。例如，“o{2,}”不能匹配“Bob”中的“o”，但能匹配“foooood”中的所有o。“o{1,}”等价于“o+”。“o{0,}”则等价于“o*”。 |
| {*n*,*m*}   | *m*和*n*均为非负整数，其中*n*<=*m*。最少匹配*n*次且最多匹配*m*次。例如，“o{1,3}”将匹配“fooooood”中的前三个o为一组，后三个o为一组。“o{0,1}”等价于“o?”。请注意在逗号和两个数之间不能有空格。 |
| ?           | 匹配前面的子表达式零次或一次。例如，“do(es)?”可以匹配“do”或“does”。?等价于{0,1}。 |
| ?           | 当该字符紧跟在任何一个其他限制符（*,+,?，{*n*}，{*n*,}，{*n*,*m*}）后面时，匹配模式是非贪婪的。非贪婪模式尽可能少地匹配所搜索的字符串，而默认的贪婪模式则尽可能多地匹配所搜索的字符串。例如，对于字符串“oooo”，“o+”将尽可能多地匹配“o”，得到结果[“oooo”]，而“o+?”将尽可能少地匹配“o”，得到结果 ['o', 'o', 'o', 'o'] |
| .点         | 匹配除“\n”和"\r"之外的任何单个字符。要匹配包括“\n”和"\r"在内的任何字符，请使用像“[\s\S]”的模式。 |
|             |                                                              |
| x\|y        | 匹配x或y。例如，“z\|food”能匹配“z”或“food”(此处请谨慎)。“[zf]ood”则匹配“zood”或“food”。 |
| [xyz]       | 字符集合。匹配所包含的任意一个字符。例如，“[abc]”可以匹配“plain”中的“a”。 |
| [^xyz]      | 负值字符集合。匹配未包含的任意字符。例如，“[^abc]”可以匹配“plain”中的“plin”任一字符。 |
| [a-z]       | 字符范围。匹配指定范围内的任意字符。例如，“[a-z]”可以匹配“a”到“z”范围内的任意小写字母字符。注意:只有连字符在字符组内部时,并且出现在两个字符之间时,才能表示字符的范围; 如果出字符组的开头,则只能表示连字符本身. |
| [^a-z]      | 负值字符范围。匹配任何不在指定范围内的任意字符。例如，“[^a-z]”可以匹配任何不在“a”到“z”范围内的任意字符。 |
| \b          | 匹配一个单词的边界，也就是指单词和空格间的位置（即正则表达式的“匹配”有两种概念，一种是匹配字符，一种是匹配位置，这里的\b就是匹配位置的）。例如，“er\b”可以匹配“never”中的“er”，但不能匹配“verb”中的“er”；“\b1_”可以匹配“1_23”中的“1_”，但不能匹配“21_3”中的“1_”。 |
| \B          | 匹配非单词边界。“er\B”能匹配“verb”中的“er”，但不能匹配“never”中的“er” |
| \s          | 匹配任何不可见字符，包括空格、制表符、换页符等等。等价于[ \f\n\r\t\v]。 |
| \S          | 匹配任何可见字符。等价于[^ \f\n\r\t\v]。                     |
| \w          | 匹配包括下划线的任何单词字符。类似但不等价于“[A-Za-z0-9_]”，这里的"单词"字符使用Unicode字符集。 |
| \W          | 匹配任何非单词字符。等价于“[^A-Za-z0-9_]”。                  |
| \d          | 匹配一个数字字符。等价于[0-9]。grep 要加上-P，perl正则支持   |
| \D          | 匹配一个非数字字符。等价于[^0-9]。grep要加上-P，perl正则支持 |
| \n          | 匹配一个换行符。等价于\x0a和\cJ。                            |
| \r          | 匹配一个回车符。等价于\x0d和\cM。                            |
| \t          | 匹配一个制表符。等价于\x09和\cI。                            |
| ( )         | 将( 和 ) 之间的表达式定义为“组”（group），并且将匹配这个表达式的字符保存到一个临时区域（一个正则表达式中最多可以保存9个），它们可以用 \1 到\9 的符号来引用。 |
| (?:pattern) | 非获取匹配，匹配pattern但不获取匹配结果，不进行存储供以后使用。这在使用或字符“(\|)”来组合一个模式的各个部分时很有用。例如“industr(?:y\|ies)”就是一个比“industry\|industries”更简略的表达式。 |
| \|          | 将两个匹配条件进行逻辑“或”（Or）运算。例如正则表达式(him\|her) 匹配"it belongs to him"和"it belongs to her"，但是不能匹配"it belongs to them."。注意：这个元字符不是所有的软件都支持的。 |

首先介绍的是re模块的findall方法，该方法用于从字符串中获取所有匹配成功的内容：

```python
import re
res = re.findall("表达式"，"字符串内容")
res = re.findall("\w"，"hello python")
res = re.findall("^http://"，"http://www.baidu.com\nhttp://www.sina.com.cn", re.M)
# 该方法得到一个列表
print(res)
```

# 单个字符匹配

\w 

\W

 \s

 \S

 \d

 \D

 .

 \r

 \n

 \t

# 指定匹配范围

a|b|c

[abc]

[^abc]

[a-z]

[a-zA-Z0-9]

注意当 -需要作为普通字符时必须写在最前面或最后面

# 匹配次数

{a}

{b,}

{a,b}

\*  

？



# 位置匹配

^

$

\d

\B



# 贪婪模式 

默认情况下+和*将尽可能多的匹配内容

\+

*

# 非贪婪模式

将尽可能少的匹配内容，当？出现在其他的重复次数后面时会将贪婪模式改为非贪婪模式。

?

如

abc.*？

abc.+?  



# 分组 

用于单独获取某一部分匹配的内容

（表达式）获取匹配的

（?:表达式） 不获取匹配的

补充：

```python
#匹配模式:.不能匹配换行符
content='''Hello 123456 World_This
is a Regex Demo
'''
# res=re.match('He.*?(\d+).*?Demo$',content)
# print(res) #输出None

# res=re.match('He.*?(\d+).*?Demo$',content,re.S) #re.S让.可以匹配换行符
# print(res)
# print(res.group(1))
```

# re模块其他函数

search

​	仅获取第一个匹配的内容

match

​	从字符串开始处开始匹配

compile

​	得到一个的表达式对象，后期可以重复使用

split

​	使用正则表达式来切分字符串 

```python
re.split("[:\/\\]","a:b/c\d/f")
```

sub 

​	普通替换与字符串的替换没有区别

​	print(re.sub("python","PYTHON","python asasasaasa python"))

​	正则替换 只替换后面的python

​	print(re.sub("(python)(.*)(python)",r"\1\2PYTHON","python asasasaasa python"))

# 练习

- 编写验证身份证的正则

- 编写验证手机号的正则

- 编写验证邮箱地址的正则
	
