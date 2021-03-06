# char和varchar的区别

> ## 1. char

1. 定长
2. 尾空格截断

> ## 2. varchar

1. 长度可变
2. 尾空格保留
3. 会有1～2个字节用来保存字符串的长度，长度小于等于255使用1个字节，长度大于255使用两个字节
4. 如果varchar中的长度过长，InnoDB会把数据保存成BLOB

> ## 3. 选择建议

1. 对于字符串长度比较固定或者相差不大时，建议使用char
2. 如果只有很短的字符串，比如“Y”、“N”，建议使用char，因为varchar会额外分配一个字节用来存储字符串的长度
3. 如果长度不定，建议使用varchar
4. 对于空格的截断和保留术语服务器层操作，于存储引擎无关
5. varchar(5)和varchar(200)中存储“hello”的空间占用是相同的，但是在进行排序时，如果使用varchar(200)会非常的糟糕，因为MySQL通常会分配固定大小的内存块来保存内部的值。
