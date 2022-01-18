# 利用etree对象+XPath表达式爬虫

由于lxml模块的部分版本没有集成etree类，建议在安装时要指定模块的版本。例如，“pip install lxml==4.5.2”就表示指定安装4.5.2版本的lxml模块，这个版本的模块集成了etree类。

## 1. 实例化etree对象
（1）etree.parse('HTML文档路径')
对于本地HTML文档，使用parse()函数进行etree对象的实例化。
```python
from lxml import etree
html = etree.parse('test1.html')  #将HTML文档加载到etree类中，实例化成一个名为html的etree对象
```
（2）etree.HTML(网页源代码)
对于爬虫程序从网站服务器获取到的网页源代码字符串，使用HTML()函数进行etree对象的实例化。
```python
import requests
from lxml import etree
headers = {'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36'}
response = requests.get(url='https://www.baidu.com', headers=headers)  # 获取响应对象
result = response.text  # 获取响应对象中的网页源代码
html = etree.HTML(result)  # 将获取的网页源代码加载到etree类中，实例化成一个名为html的etree对象
```

## 2. XPath
网页自动获取吧。