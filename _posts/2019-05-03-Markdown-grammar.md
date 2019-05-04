---
title: Markdown基本语法及渲染
layout: post
date: '2019-05-03 21:34:00'
tag: Markdown
category: Markdown
---
本文主要说明一些常用的 Markdown 语法及主题 Minimalism 中的渲染效果。


# 说明
Jekyll 默认使用 [Kramdown] 来渲染 mardown 类型文件，在 MengBlog 主题中也是使用这个默认配置，但在其渲染的基础上自定义了自己的样式，主要参考了 GitHub 的渲染风格。

# Markdown 基本语法
&emsp; &emsp; 这是新手语法篇，介绍一下Markdown的基本语法，还有展示一些主题对各种格式的渲染效果。也是Meng初来乍到熟悉如何编写博客。

### 1. 斜体和粗体

使用 \* 和 \** 表示斜体和粗体。

示例：

```
这是 *斜体*， 这是 **粗体**。
```

效果：

这是 *斜体*， 这是 **粗体**。

### 2. 分级标题

标题分成 6 级， 在行首加 ```#``` 用来表示不同级别的标题 （H1 - H6），常用的标题主要就是1 ~3 级， 注意 1，2级标题会有下划线，有强迫症的朋友小心使用！！！

示例：
```
# 一级标题

## 二级标题

### 三级标题

#### 四级标题

##### 五级标题

###### 六级标题
```

效果：
# 一级标题

## 二级标题

### 三级标题

#### 四级标题

##### 五级标题

###### 六级标题

### 3. 外链接

使用 \[描述\]\(链接地址\) 为文章增加外链接。

示例：

```
这是去往 [主题 MengBlog](https://blog.jiadong.work) 的链接。
```

效果：

这是去往 [主题 MengBlog](https://blog.jiadong.work) 的链接。

也可以在链接地址后加一个标题，直观效果是鼠标悬停在 “主题 MengBlog” 的时候会有文本提示，其语法是链接后加空格和标题文本。

示例：
```
这是去往 [主题 MengBlog](https://blog.jiadong.work “MengBlog”) 的链接。
```

效果（鼠标悬停在链接上时触发）：

这是去往 [主题 MengBlog](https://blog.jiadong.work "MengBlog") 的链接。

同时外链接还有另外一种使用方式，一般是在文末放置链接标注，在文中就直接使用标注，这样的好处是方便管理外链接。

示例
```
文末放置 Minimalism 的链接标注： 
[Minimalism]: https://github.com/showzeng/minimalism 

文章中直接使用标注替代链接： 
这是我使用的一个主题 [Minimalism]。
```

效果：

这是我使用的一个主题 [Minimalism]。

此外，在使用链接标注时，可以替换需要显示的链接文本，比如需要替换外链需要写成是中文。

示例：
```
文末放置 Minimalism 的链接标注： 
[Minimalism]: https://github.com/showzeng/minimalism 

文章中直接使用标注替代链接： 
这是我使用的一个主题 [极简派艺术][Minimalism]。
```

效果：

这是我使用的一个主题 [极简派艺术][Minimalism]。

### 4. 无序列表

使用```*``` **/** ```-``` **/** ```+``` 表示无序列表。

示例：
```
* 无序列表项 一
* 无序列表项 二
* 无序列表项 三
```

效果：

* 无序列表项 一
* 无序列表项 二
* 无序列表项 三

### 5. 有序列表

使用数字和点表示有序列表。

示例：
```
1. 有序列表项 一
2. 有序列表项 二
3. 有序列表项 三
```

效果：

1. 有序列表项 一
2. 有序列表项 二
3. 有序列表项 三

### 6. 引用

使用 ```>``` 表示引用

示例：
```
> Less is More. -- 「Andrea del Sarto」
```

效果：

> Less is More. -- 「Andrea del Sarto」

当然，引用是可以嵌套使用。

示例：

```
> 这是引用。
> > 这也是引用。
> > > > > > 这还是引用。
```

效果：
> 这是引用。
> > 这也是引用。
> > > > > > 这还是引用。

### 7. 行内代码块

使用 \`代码\` 表示行内代码块。

示例：
```
让主题 `MengBlog` 变成行内代码块。
```

效果：

让主题 `MengBlog` 变成行内代码块。

### 8. 代码块

使用四个缩进空格表示代码块（注意不是中文空格符）。

示例：

```
    这是一个代码块，此行左侧有四个不可见的空格
```

效果：

    这是一个代码块，此行左侧有四个不可见的空格
		
需要说明的是，这种格式来书写会让你重读代码的时候，非常confusing，所以并不推荐使用这种格式来书写。这里我推荐另外一个代码块的书写。

示例
```
		```
		这是一个代码块
		```
		
		```text
		指定代码类型的代码块
		```
		
		```Java
		public class HelloWorld { 
			public static void main(String[] args) { 
			// Prints "Hello, World" to the terminal window. 
			System.out.println("Hello, World"); 
			}
		```
		

```

效果：

```
这是一个代码块
```
		
```text
		指定代码类型的代码块
```
		
```Java
		public class HelloWorld { 
			public static void main(String[] args) { 
			// Prints "Hello, World" to the terminal window. 
			System.out.println("Hello, World"); 
			}
```

### 9. 插入图像

使用 \!\[描述\]\(图片链接地址\) 插入图像。

示例：

```
![头像](https://i.ibb.co/Gp14cvf/Meng.png)
```

效果：

![头像](https://i.ibb.co/Gp14cvf/Meng.png)

同外链接，图片也可以在链接地址后加一个标题，直观效果是鼠标悬停时的文本提示，其语法是链接后加空格和“标题文本”。

示例：
```
![头像](https://i.ibb.co/Gp14cvf/Meng.png "我可爱吧~")
```

效果（鼠标悬停在头像上时触发）：

![头像](https://i.ibb.co/Gp14cvf/Meng.png "我可爱吧~")

### 10. 分隔符

使用 ```---``` 可以显示分隔符。

示例：
```
---
```

效果：

---

### 11. 反转义

使用 ```\``` 可使得 Markdown 解析时不会去解析本该属于语法部分的一些符号。

示例：
```
没有反转义： `代码块`
有反转义： \`代码块\`
```

效果：
没有反转义： `代码块`
有反转义： \`代码块\`

### 12. Emoji

本主题同样也支持 Emoji 表情，使用方法也很方便（注意 ```:``` 后面是没有空格）。

示例：

```
(Smile) 笑 :smile:   (Sob) 哭 :sob:
```

效果：

(Smile) 笑 :smile:   (Sob) 哭 :sob:

Emoji 的代码参考 [Emoji sheet]。

### 13. 段内换行&空格

在同一段落里让文本换行，只需要在上一行末尾加 **2** 个空格即可。

示例：
```
这是这个段落的第一行。  
这是同一个段落的第二行。
```

效果：

这是这个段落的第一行。  
这是同一个段落的第二行。

Markdown 里面想要打中文空格可以使用```&emsp;```

示例：
```
&emsp; &emsp; 自然段空两格子。
现在不空两个格子。
```

效果：

&emsp; &emsp; 自然段空两格子。
现在不空两个格子。




[Kramdown]: https://github.com/gettalong/kramdown
[Minimalism]: https://github.com/showzeng/minimalism
[Emoji sheet]: https://www.webfx.com/tools/emoji-cheat-sheet/