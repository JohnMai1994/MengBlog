---
title: Markdown高阶语法
layout: post
tag: Markdown
category: Markdown
date: '2019-05-04 14:20:00'
---

本文主要说明一些常用的高阶 Markdown 语法及主题 MengBlog 中的渲染效果。

# 说明
Jekyll 默认使用 [Kramdown] 来渲染 mardown 类型文件，在 MengBlog 主题中也是使用这个默认配置，但在其渲染的基础上自定义了自己的样式，主要参考了 GitHub 的渲染风格。

[Kramdown]: https://github.com/gettalong/kramdown

# Markdown 高阶语法
### 1. 删除线

使用```~~``` 表示删除线。

示例：
```
~~这是一段错误的文案。~~
```

效果：

~~这是一段错误的文案。~~

### 2. 注脚

使用 \[^keyword\] 表示注脚，keyword可以是任何东西。

示例：
```
这是第一个注脚 [^footnote1] 的样例。

这是第二个注脚 [^footnote2] 的样例。

对应的在文章末尾放置如下，点击效果中的注脚即可跳转到文章末尾的注脚注解。

[^footnote1]: 第一个注脚的注释。
[^footnote1]: 第二个注脚的注释。
```

效果：

这是第一个注脚 [^footnote1] 的样例。

这是第二个注脚 [^footnote2] 的样例。

### 3. 加强的代码块

使用 [Prism] 官网定制的代码高亮主题，选择了所有支持的编程语言，你可以定制你自己的语法主题。

非代码示例：
```
	```
	$ sudo pacman -S oh-my-zsh-git
	```
```

效果：
```
$ sudo pacman -S oh-my-zsh-git
```

Python 示例：
```
	```python 
	@requires_authorization 
	def somefunc(param1='', param2=0): 
		'''A docstring''' 
		if param1 > param2: # interesting 
			print 'Greater' 
		return (param2 - param1 + 1) or None 
		
	class SomeClass: 
		pass
		
	>>> message = '''interpreter 
	... prompt''' 
	```
```

效果：
```python 
	@requires_authorization 
	def somefunc(param1='', param2=0): 
		'''A docstring''' 
		if param1 > param2: # interesting 
			print 'Greater' 
		return (param2 - param1 + 1) or None 
		
	class SomeClass: 
		pass
		
	>>> message = '''interpreter 
	... prompt''' 
```

JavaScript 示例：
```
	``` javascript 
	/** 
	* nth element in the fibonacci series. 
	* @param n >= 0 
	* @return the nth element, >= 0. 
	*/ 
	function fib(n) { 
		var a = 1, b = 1; 
		var tmp; 
		while (--n >= 0) { 
			tmp = a; 
			a += b; 
			b = tmp; 
			} 
			return a; 
		} 
		
		document.write(fib(10)); 
	```
```

效果：
``` javascript 
	/** 
	* nth element in the fibonacci series. 
	* @param n >= 0 
	* @return the nth element, >= 0. 
	*/ 
	function fib(n) { 
		var a = 1, b = 1; 
		var tmp; 
		while (--n >= 0) { 
			tmp = a; 
			a += b; 
			b = tmp; 
			} 
			return a; 
		} 
		
		document.write(fib(10)); 
```

### 4. 表格支持

示例（经过Meng血的教训，格子上面一定要留有空的一段，不然就不会显示成格子的样子。。）：
```
| 项目 | 价格 | 数量 |
| -- | -- | -- |
| 计算机 | \$1600 | 5 |
| 手机 | \$12 | 12 |
| 管线 | \$1 | 234 |
```

效果：

| 项目 | 价格 | 数量 | 
| -- | :--: | --: | 
| 计算机 | \$1600 | 5 | 
| 手机 | \$12 | 12 | 
| 管线 | \$1 | 234 |

### 5. 定义型列表

示例：

```
名词 1
: 定义 1 (左侧有一个可见的冒号和空格)
名词2
: 定义 2 (左侧有一个可见的冒号和空格)
```

效果：

名词 1
: 定义 1 (左侧有一个可见的冒号和空格)
名词2
: 定义 2 (左侧有一个可见的冒号和空格)

### 6. HTML 标签

可在Markdown 语法中直接嵌套 HTML 标签， 比如，你可以用HTML 写一个纵跨两行的表格：

```
<table>
	<tr>
		<th rowspan="2">值班人员</th>
		<th> 星期一 </th>
		<th> 星期二 </th>
		<th> 星期三 </th>
	</tr>
	<tr>
		<td>李强</td>
		<td>麦萌</td>
		<td>王平</td>
	</tr>
</table>
```

效果：
<table>
	<tr>
		<th rowspan="2">值班人员</th>
		<th> 星期一 </th>
		<th> 星期二 </th>
		<th> 星期三 </th>
	</tr>
	<tr>
		<td>李强</td>
		<td>麦萌</td>
		<td>王平</td>
	</tr>
</table>

### 7. 待办事项 Todo List

使用 ```[ ]``` 或者 ```[x]``` （未完成或已完成）项的列表语法撰写一个待办事项列表，并且支持子列表嵌套以及混用Markdown语法。

示例：
```
- [ ] **博客改版**
	- [ ] 响应式布局，移动端适配
	- [ ] 多语言支持
	- [x] 主页
	- [x] 文章列表页
	- [ ] 归档页
	- [ ] 关于页
	- [x] 文章详情页
		- [x] 排版
		- [x] Markdown渲染
		- [x] 代码高亮
		- [ ] Toc功能
		- [ ] 评论功能
		- [ ] 打赏功能

- [ ] **MengBlog 主题发布**
	- [ ] 主题编写
	- [ ] 打包发布
```

效果：
- [ ] **博客改版**
	- [ ] 响应式布局，移动端适配
	- [ ] 多语言支持
	- [x] 主页
	- [x] 文章列表页
	- [ ] 归档页
	- [ ] 关于页
	- [x] 文章详情页
		- [x] 排版
		- [x] Markdown渲染
		- [x] 代码高亮
		- [ ] Toc功能
		- [ ] 评论功能
		- [ ] 打赏功能

- [ ] **MengBlog 主题发布**
	- [ ] 主题编写
	- [ ] 打包发布

# 总结
感谢各位看官看到了最后，这个Blog的语法模板大部分是参考了 [showzeng大佬][showzeng] 的博客&简书上的[Markdown基本语法][base]写出来的。


[^footnote1]: 第一个注脚的注释。
[^footnote2]: 第二个注脚的注释。
[Prism]: https://prismjs.com/
[showzeng]: https://showzeng.itscoder.com/
[base]: https://www.jianshu.com/p/191d1e21f7ed