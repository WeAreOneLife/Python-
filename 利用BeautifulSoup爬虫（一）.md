# 利用BeautyfulSoup爬虫（一）

## 首先，定位到想要爬取的内容

## 1. 通过标签名定位
网页源代码中可能会有多个同名标签，通过标签名进行定位只能返回其中的第一个标签。
```python
from bs4 import BeautifulSoup
fp = open('test1.html', encoding='utf-8')  # 读取HTML文档
soup = BeautifulSoup(fp, 'lxml')  # 实例化BeautifulSoup对象
print(soup.p)  # 通过标签名定位第一个<p>标签
```

## 2. 通过标签名定位
标签属性有class、id等，实践中主要使用class属性来定位标签。需要注意的是，因为class这个单词本身是Python的保留字，所以BeautifulSoup模块中的class属性在末尾添加了下划线来进行区分。其他标签属性，如id属性，则没有添加下划线。
```python
from bs4 import BeautifulSoup
fp = open('test1.html', encoding='utf-8')
soup = BeautifulSoup(fp, 'lxml')
print(soup.find(class_='first'))  # 返回class属性值为first的第一个标签
print(soup.find_all(class_='first'))  # 返回class属性值为first的所有标签的列表
```

一个标签的属性可以有多个值，例如，第一个<div>标签的class属性就有first和ten两个值。从运行结果可以看出，find()和find_all()函数在执行时，只要标签的任意一个值满足条件，就会将标签返回。

## 3. 通过标签名+标签属性定位
```python
from bs4 import BeautifulSoup
fp = open('test1.html', encoding='utf-8')
soup = BeautifulSoup(fp, 'lxml')
print(soup.find('div', class_='first'))
print(soup.find_all('div', class_='first'))
```

## 4. 通过选择器定位（使用select函数）
使用select()函数可以根据指定的选择器返回所有符合条件的标签。

（1）id选择器
id选择器可以根据标签的id属性进行定位。演示代码如下：

```python
from bs4 import BeautifulSoup
fp = open('test1.html', encoding='utf-8')
soup = BeautifulSoup(fp, 'lxml')
print(soup.select('#first'))
```
第4行代码中，select()函数括号中的'#first'是id选择器的书写格式，“#”代表id选择器，“#”后的内容为id属性的值。

（2）class选择器
第4行代码中，select()函数括号中的'.first'是class选择器的书写格式，“.”代表class选择器，“.”后的内容为class属性的值。
```python
from bs4 import BeautifulSoup
fp = open('test1.html', encoding='utf-8')
soup = BeautifulSoup(fp, 'lxml')
print(soup.select('.first'))
```

（3）标签选择器
用标签选择器进行定位与只用标签名进行定位的不同之处在于，该方法能返回所有该类型的标签。
```python
from bs4 import BeautifulSoup
fp = open('test1.html', encoding='utf-8')
soup = BeautifulSoup(fp, 'lxml')
print(soup.select('li'))  # 返回所有<li>标签
```

（4）层级选择器
一个标签可以包含另一个标签，这些标签位于不同的层级，形成层层嵌套的结构。利用层级选择器可以先定位外层的标签，再定位内层的标签，这样一层层地往里定位，就能找到需要的标签。
```python
from bs4 import BeautifulSoup
fp = open('test1.html', encoding='utf-8')
soup = BeautifulSoup(fp, 'lxml')
print(soup.select('div>ul>#first'))  # 选中所有<div>标签下<ul>标签中id属性值为first的所有标签
print(soup.select('div>ul>li'))  # 选中所有<div>标签下所有<ul>标签中的所有<li>标签
print(soup.select('div li'))  # 选中<div>标签包含的所有<li>标签
```
第4行和第5行代码中的“>”在层级选择器中表示向下找一个层级，中间不能有其他层级。第6行代码中的空格表示中间可以有多个层级。