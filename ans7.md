# 第7回目 練習問題 解答例
## 練習問題
1. 縦線をずらしながら5本引く
```python
size(600, 600)
background(255, 255, 255)
strokeWeight(4)
for i in range(5):
    line((i+1)*100, 0, (i+1)*100, height)
```

2. 色を変えながら，一列に正方形を並べる
```python
size(600, 600)
colorMode(HSB, 360, 100, 100)
background(0, 0, 100)
strokeWeight(2)
for i in range(10):
    fill(24*i, 100, 100)
    rect(width/2-30, 60*i, 60, 60)
```

3. 色を変えながら，対角線上（右上から左下）に正方形を並べる
```python
size(600, 600)
colorMode(HSB, 360, 100, 100)
background(0, 0, 100)
strokeWeight(2)
for i in range(10):
    fill(24*i, 100, 100)
    rect(60*(10-i-1), 60*i, 60, 60)
```

4. 色を変えながら，一行に円を並べる
```python
size(600, 600)
colorMode(HSB, 360, 100, 100)
background(0, 0, 100)
strokeWeight(2)
for i in range(10):
    fill(24*i, 100, 100)
    ellipse(30+60*i, height/2, 60, 60)
```

5. 色を変えながら，一列に円を並べる
```python
size(600, 600)
colorMode(HSB, 360, 100, 100)
background(0, 0, 100)
strokeWeight(2)
for i in range(10):
    fill(24*i, 100, 100)
    ellipse(width/2, 30+60*i, 60, 60)
```
6. マウスの位置に円を連結した×字模様を描く
```python
def setup():
    size(600, 600)

def draw():
    background(255, 255, 255)
    strokeWeight(2)
    fill(0, 255, 255)
    ellipse(mouseX, mouseY, 30, 30)
    for i in range(3):
        ellipse(mouseX+i*22, mouseY+i*22, 30, 30)
        ellipse(mouseX-i*22, mouseY-i*22, 30, 30)
        ellipse(mouseX+i*22, mouseY-i*22, 30, 30)
        ellipse(mouseX-i*22, mouseY+i*22, 30, 30)
```