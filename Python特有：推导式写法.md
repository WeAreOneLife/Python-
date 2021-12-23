# Python特有:推导式写法

## 列表推导式
例：从1到10 所有偶数的平方
一般写法：
```python
alist=[]
for i in range(1,11): 
	if (i % 2) == 0:
		alist.append(i*i)
print(alist)
```

推导式写法：
```python
blist = [i*i for i in range(1,11) if (i%2) == 0]
print(blist)
```

## 字典推导式
一般写法：
```python
zdict={}
for i in zdict_num:
	zdict[i] = 0
```

推导式写法：
```python
zdict = {i:0 for i in zdict_num}
```