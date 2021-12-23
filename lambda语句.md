# lambda 表达式

目的：实现简单函数的简化
例如：
```python
def true():
	return True
```
简化到一行看看：
```python
def true():return True
```
进一步简化函数名和return
```python
lambda : True
```
另一个例子
```python
# 原写法
def add(x,y): 
	return x+y 

# lambda写法
lambda x,y:x+y
```
# 结构：
lambda 参数：return的内容