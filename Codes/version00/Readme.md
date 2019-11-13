# version00

![img](https://ae01.alicdn.com/kf/H7190f0de01704187b8b9b021d9a8de69C.png)

## Core 

```python3
def hit_me():
    global on_hit
    if on_hit == False:
        on_hit = True
        margin = getMargin()
        print("margin: ", margin)
        run(margin)
        var.set('已完成！')
    else:
        on_hit = False
        var.set('重复操作！')

def getMargin():
	Input = M_text.get()
	margin = int(Input) if Input else 0
	return margin

def run(margin):

	import jieba

	txt = open("news.txt", "r").read()
	res = open("result.txt", "w")
	words = jieba.cut(txt)
	size = margin
	print("size: ", size)
	i = 0
	for word in words:
		if i == size:
			res.write('\n')
			i = 0
		else:
			res.write(word)
			i += 1

	# txt.close()
	res.close()
```