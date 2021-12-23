# python内建函数

## 1.filter: 
用于过滤序列，过滤掉不符合条件的元素，返回一个迭代器对象，如果要转换为列表，可以使用 list() 来转换。该接收两个参数，第一个为函数，第二个为序列，序列的每个元素作为参数传递给函数进行判断，然后返回 True 或 False，最后将返回 True 的元素放到新列表中。
```python
a= [1,2,3,4,5,6,7]
list(filter(lambda x:x>2,a))
```

## 2.map:
依次处理

```python
a=[1,2,3]
list(map(lambda x:x+1, a))

b=[4,5,6]
list(map(lambda x,y:x+y, a,b))

```

## 3. reduce:
```python
from functools import reduce
reduce(lambda x,y:x+y , [2,3,4],1)  # (((1+2)+3)+4)=10
```

## 4. zip:
```python
for i in zip((1,2,3),(4,5,6)):
	print (i)

# 常用场景：key与value的对调
dicta={'a':'aa','b':'bb'}
dictb=zip(dicta.values(),dicta.keys())
print(dict(dictb))

```

可迭代的函数一定有iter方法，可以通过for/in;next来遍历