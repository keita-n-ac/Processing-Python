# 第3回目 練習問題 解答例
## 練習問題
1. 赤い円が縦方向に移動するアニメーション（横方向の位置は画面中央）
```python
y = 0

def setup():
    size(600, 600)

def draw():
    global y
    background(255, 255, 255)
    strokeWeight(4)
    fill(255, 0, 0)
    ellipse(width/2, y, 30, 30)
    y += 1
    y = y % (height + 1)
```

2. 緑色の円が対角線上に移動するアニメーション（右上から左下に移動する）
```python
x = 0
y = 0

def setup():
    size(600, 600)

def draw():
    global x, y
    background(255, 255, 255)
    strokeWeight(4)
    fill(0, 255, 0)
    ellipse(x, y, 30, 30)
    y += 1
    y = y % (height + 1)
    x -= 1
    x = x % (width + 1)
```
3. 2つの円が移動するアニメーション
   - 1つ目の円は横方向に移動する（縦方向の位置は画面中央）
   - 2つ目の円は縦方向に移動する（横方向の位置は画面中央）
```python
x = 0
y = 0

def setup():
    size(600, 600)

def draw():
    global x, y
    background(255, 255, 255)
    strokeWeight(4)
    fill(0, 0, 255)
    ellipse(width/2, y, 30, 30)
    fill(255, 255, 0)
    ellipse(x, height/2, 30, 30)
    x += 1
    x = x % (width + 1)
    y += 1
    y = y % (height + 1)
```

4. 2つの円が移動するアニメーション
   - 1つ目の円は左上から右下に移動する
   - 2つ目の円は右上から左下に移動する
```python
x1 = 0
y1 = 0
x2 = 0
y2 = 0

def setup():
    size(600, 600)

def draw():
    global x1, y1, x2, y2
    background(255, 255, 255)
    strokeWeight(4)
    fill(0, 0, 255)
    ellipse(x1, y1, 30, 30)
    x1 += 1
    x1 = x1 % (width + 1)
    y1 += 1
    y1 = y1 % (height + 1)    

    fill(255, 255, 0)
    ellipse(x2, y2, 30, 30)
    x2 -= 1
    x2 = x2 % (width + 1)
    y2 += 1
    y2 = y2 % (height + 1)
```
5. アニメーションの速度を変えるにはどうしたらよいか考えなさい
    - 更新値を大きくすれば良い
      - 例: ```x += 1```を```x += 5```などにすればよい

```python
x1 = 0
y1 = 0
x2 = 0
y2 = 0

def setup():
    global x2
    size(600, 600)
    x2 = width

def draw():
    global x1, y1, x2, y2
    background(255, 255, 255)
    strokeWeight(4)
    fill(0, 255, 255)
    ellipse(x1, y1, 30, 30)
    x1 += 5
    x1 = x1 % (width + 1)
    y1 += 5
    y1 = y1 % (height + 1)

    fill(255, 0, 255)
    ellipse(x2, y2, 30, 30)
    x2 -= 1
    x2 = x2 % (width + 1)
    y2 += 1
    y2 = y2 % (height + 1)
```
