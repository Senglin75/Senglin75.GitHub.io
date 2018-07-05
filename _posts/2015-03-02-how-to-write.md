---
layout: post
title: Python 中用来过滤序列的函数 filter()
date: 2018-7-5
categories: blog
tags: [Python,notes]
description: Python 中用来过滤序列的函数
---

# Python 中用来过滤序列的函数-filter()

**语法：**  `filter(function, argument)`, `filter()` 通过传入的参数 `argument`，依次作用于筛选函数 `function` ，并通过筛选函数的返回值 True or False ，来决定是否保留或剔除元素。

例如，从 1~10 里剔除奇数，筛选出偶数。
```
	def is_odd(n) :

		return n % 2 == 0

		list(filter(is_odd, range(1, 11)))
```
结果：
```		
	[2, 4, 6, 8, 10]
```
**注意：** `filter()` 函数是 Python 内置的一个高阶函数,并且返回的是一个 `Iterator`，即返回的是一个惰性序列，因此需要强迫 `filter()` 完成计算结果，可通过 `list()` 函数来获取所有返回值。

例如,剔除一个序列里面的空字符串。
```
	def not_empty(n) :
		return n and s.strip()
	filter(not_empty,['a', ' abc', '', '  ', None])
```

按下回车，会出现
	
	<filter object at 0x00000000025964A8>

返回的是一个函数，说明 `filter()` 并没有完成计算结果，将最后一句改为

	list(filter(not_empty,['a', ' abc', '', '  ', None]))

可看到结果

	['a', ' abc']

**引申**

> 
`strip(argument)` 函数是一个只针对字符串里首位和末位元素的函数，对它们进行删除至首位和末尾都没有要删除的元素为止，并返回剩余的元素，不会删除掉中间的元素，并且由里面的参数 argument 决定要删除的是什么元素，`strip()` 默认删除首位和末位的空格或换行 (`\n, \v, \t, \r, \f`)


例如：
```
	s = '\f\t\v\n\r 2  3'
	
	s.strip()
```
结果为：

	'2  3'

`strip(argument)` 函数也可指定要删除的 `argument` 

例如：
```
	s = '12 abc 21'

	s.strip('12')
```
结果：
	
	' abc '

练习 :

	请打印出 100 以内的素数，结果应该为 2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97。


相关代码：
```
	def is_prime(n) :

		if n == 1 or n == 0:

			return False

		for i in range(2, n-1) :

			if n % i == 0 :

				return False

		return True  
		
		l=list(filter(is_prime, range(101)))

		print('100以内的素数:', l)
```
结果：

	100以内的素数: [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97]

