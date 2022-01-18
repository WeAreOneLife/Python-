# 利用BeautifulSoup爬虫（二）
## 从标签中提取文本内容和属性值
. 从标签中提取文本内容
定位到标签后，还需要从标签中提取文本内容，才能获得需要的数据。从标签中提取文本内容可以利用标签的string属性或text属性。

string属性返回的是指定标签的直系文本，即直接存在于该标签中的文本，而不是存在于该标签下的其他标签中的文本。text属性返回的则是指定标签下的所有文本。演示代码如下：

```python
from bs4 import BeautifulSoup
fp = open('test1.html', encoding='utf-8')
soup = BeautifulSoup(fp, 'lxml')
print(soup.select('.first')[1].string)
print(soup.select('.first')[1].text)
```

第4行和第5行代码中的“select('.first')[1]”表示使用select()函数根据class选择器定位class属性值为first的所有标签，再从返回的标签列表中指定第2个标签用于提取文本内容。第4行代码使用string属性提取直系文本，如果当前标签没有直系文本，或者由于当前标签包含子标签导致string属性无法确定要提取哪些文本，会返回None。第5行代码使用text属性提取所有文本。

2. 从标签中提取属性
定位到标签后，还可以通过字典取值的方式取出标签的属性值。
```python
from bs4 import BeautifulSoup
fp = open('test1.html', encoding='utf-8')
soup = BeautifulSoup(fp, 'lxml')
print(soup.find(class_='first')['class'])
```