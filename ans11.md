# 第11回目 練習問題 解答例
## 練習問題

1.
```python
speed = 3
x = 0
def setup():
    size(600, 600)

def draw():
    global x, speed
    background(255, 255, 255)
    fill(255, 0, 255)
    strokeWeight(5)
    ellipse(x, height/2, 60, 60)
    x += speed
    if x < 0 or x > width:
        speed *= -1
    # 文字の表示
    fill(0, 0, 0)
    textSize(36)
    text('x: ' + str(x), 50, 450)
```

2.
```python
num = 50 # オブジェクトの数
x = []
y = []
d = []
r = []
g = []
b = []
speedY = []

def setup():
    global x, y, d, r, g, b, speedY
    size(600, 600)
    for i in range(num):
        # x座標
        temp = int(random(0, width))
        x.append(temp)
        # y座標
        temp = int(random(0, height))
        y.append(temp)
        # 直径
        temp = int(random(30, 200))
        d.append(temp)
        # 赤要素
        temp = int(random(0, 256))
        r.append(temp)
        # 緑要素
        temp = int(random(0, 256))
        g.append(temp)
        # 青要素
        temp = int(random(0, 256))
        b.append(temp)
        # 速度
        temp = random(0, 10)
        speedY.append(temp)

def draw():
    global y, speedY
    background(255, 255, 255)
    for i in range(num):
        fill(r[i], g[i], b[i])          # 色指定
        ellipse(x[i], y[i], d[i], d[i]) # 円を描画
        y[i] += speedY[i]
        if y[i] < 0 or y[i] > height:
            speedY[i] *= -1
```

3.
```python
num = 100 # オブジェクトの数
x = []  
y = []
d = []
r = []
g = []
b = []
speedX = []
speedY = []

def setup():
    global x, y, d, r, g, b, speedX, speedY
    size(600, 600)
    for i in range(num):
        # x座標
        temp = int(random(0, width))
        x.append(temp)
        # y座標
        temp = int(random(0, height))
        y.append(temp)
        # 直径
        temp = int(random(30, 200))
        d.append(temp)
        # 赤要素
        temp = int(random(0, 256))
        r.append(temp)
        # 緑要素
        temp = int(random(0, 256))
        g.append(temp)
        # 青要素
        temp = int(random(0, 256))
        b.append(temp)
        # 速度
        temp = random(0, 10)
        speedX.append(temp)
        temp = random(0, 10)
        speedY.append(temp)

def draw():
    global x, y, speedX, speedY
    background(255, 255, 255)

    for i in range(num):
        fill(r[i], g[i], b[i])          # 色指定
        ellipse(x[i], y[i], d[i], d[i]) # 円を描画
        x[i] += speedX[i]
        if x[i] < 0 or x[i] > width:
            speedX[i] *= -1
        y[i] += speedY[i]
        if y[i] < 0 or y[i] > height:
            speedY[i] *= -1
```

4.
```python
size(600, 600)
background(255, 255, 255)
xa = 100
ya = 500
xb = 500
yb = 100
strokeWeight(32)  # pointの大きさ
stroke(0, 0, 255) # pointの色
point(xa, ya)
point(xb, yb)

d = 20

strokeWeight(16) # pointの大きさ
stroke(0, 0, 0)  # pointの色
for i in range(d + 1):
    t = float(i) / d # float(整数)で整数を小数に変換
    x = xa * (1 - t) + xb * t
    y = ya * (1 - t) + yb * t
    point(x, y)
```

5.
```python
i = 0

def setup():
    size(600, 600)
    frameRate(5)

def draw():
    global i
    background(255, 255, 255)
    xa = 100
    ya = 500
    xb = 500
    yb = 100
    strokeWeight(32)  # pointの大きさ
    stroke(0, 0, 255) # pointの色
    point(xa, ya)
    point(xb, yb)

    d = 60

    strokeWeight(16) # pointの大きさ
    stroke(0, 0, 0)  # pointの色
    t = float(i) / d # float(整数)で整数を小数に変換
    x = xa * (1 - t) + xb * t
    y = ya * (1 - t) + yb * t
    point(x, y)

    # tの値を表示
    fill(0, 0, 255)
    textSize(32)
    text('t: ' + str(t), 50, 570)

    i = (i+1) % (d+1)
```