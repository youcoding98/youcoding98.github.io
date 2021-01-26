---
layout: post
title: Markdown用法总结
subtitle: 该主题下的可用副标题
tags: [Markdown]
comments: true
---
Markdown是一种可以使用普通文本编辑器编写的标记语言，通过简单的标记语法，它可以使普通文本内容具有一定的格式。
***

1.**标题**

```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
```

2.**字体**
```
**加粗文字**  
*这是斜体的文字*  
***这是斜体加粗的文字***  
~~这是添加删除线的文字~~
```

3.**列表**  
1）无序列表 用 - + * 任何一种都可以，注意文字前加空格  
```
- 列表1
- 列表2
- 列表3
```
2）有序列表 数字加点，注意文字前加空格  
```
1. 列表1
2. 列表2
3. 列表3
```
3）组合使用  子列表每行缩进3个以上空格  
```
 - 列表1
      1. 列表1
      2. 列表2
      3. 列表3
```

4.**引用**  
1）不加嵌套的引用
```
>引用1
>引用2
>引用3
```
2）加嵌套的引用  
```
>引用1
>>引用2
>>> 引用3
```

5.**分割线**  
要求至少三个同样的符号以上  
`***`  
`****`  
`---`

6.**超链接** 
```
[markdown](http://markdowntutorial.com/)

行内链接[马克飞象](https://maxiang.io/)

自动链接 <http://baidu.com>
```


7.**表格** 

```
| Number | Next number | Previous number |
| :------ |:--- | :--- |
| Five | Six | Four |
| Ten | Eleven | Nine |
| Seven | Eight | Six |
| Two | Three | One |
```

8.**代码**
```
`单行代码`

用三个```代码块```包裹
```
示例如下：   
~~~
var foo = function(x) {
  return(x + 5);
}
foo(3)
~~~
相同代码带有行号  
```
{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}
```
{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}



9.**反斜杠**
```
\\ 反斜线
\` 反引号
\* 星号
\_ 底线
\{ 左花括号
\} 右花括号
\[ 左方括号
\] 右方括号
```

10.**图片** 
```
![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg)

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg){: .center-block :}

```
正常显示：  
![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg)

居中显示如下：  

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg){: .center-block :}

11.**Boxes**
You can add notification, warning and error boxes like this:
```
{: .box-note}
**Note:** This is a notification box.
```
### Notification

{: .box-note}
**Note:** This is a notification box.

### Warning

{: .box-warning}
**Warning:** This is a warning box.

### Error

{: .box-error}
**Error:** This is an error box.
