# 第13回目 練習問題 解答例
## 練習問題

1.
```python
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    r = 200       # 半径
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y

    x0 = cX + r * cos(radians(0 + d))
    y0 = cY + r * sin(radians(0 + d))

    x72 = cX + r * cos(radians(72 + d))
    y72 = cY + r * sin(radians(72 + d))

    x144 = cX + r * cos(radians(144 + d))
    y144 = cY + r * sin(radians(144 + d))

    x216 = cX + r * cos(radians(216 + d))
    y216 = cY + r * sin(radians(216 + d))

    x288 = cX + r * cos(radians(288 + d))
    y288 = cY + r * sin(radians(288 + d))

    strokeWeight(5)
    line(x0, y0, x144, y144)
    line(x144, y144, x288, y288)
    line(x288, y288, x72, y72)
    line(x72, y72, x216, y216)
    line(x216, y216, x0, y0)

    d = (d + 1) % 360
```

2.
```python
# 静止画
size(600, 600)
background(255, 255, 255)
cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

strokeWeight(5)
# 0°から360°まで繰り返す
stroke(0, 0, 255)
a = 4.5
for d in range(3600):
    x = cX + a * radians(d) * cos(radians(d))
    y = cY + a * radians(d) * sin(radians(d))
    point(x, y)
```

3.
```python
d = 0 # 角度

def setup():
    size(600, 600)
    background(255, 255, 255)

def draw():
    global d
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    strokeWeight(5)
    # 0°から360°まで繰り返す
    stroke(0, 0, 255)
    a = 4.5
    x = cX + a * radians(d) * cos(radians(d))
    y = cY + a * radians(d) * sin(radians(d))
    point(x, y)

    d = d + 1

    if d == 3600:
        background(255)
        d = 0
```

4.
```python
d = 0 # 角度

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    strokeWeight(5)
    stroke(0, 0, 255)
    a = 4.5
    for t in range(d+1):
        x = cX + a * radians(t) * cos(radians(t))
        y = cY + a * radians(t) * sin(radians(t))
        point(x, y)

    d = d + 1
    if d == 3600:
        background(255)
        d = 0

    # 文字の描画
    fill(0, 0, 0)
    textSize(36)
    text('angle: ' + str(d), 10, 570)
```

5.
```python
# 静止画
size(600, 600)
background(255, 255, 255)
cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

strokeWeight(5)
# 0°から360°まで繰り返す
stroke(0, 0, 255)
r = 75
for d in range(360):
    x = cX + 2 * r * cos(radians(d)) + r * cos(radians(2 * d))
    y = cY + 2 * r * sin(radians(d)) - r * sin(radians(2 * d))
    point(x, y)
```

6.
```python
d = 0 # 角度
r = [75, 45, 15]

def setup():
    size(600, 600)
    background(255, 255, 255)

def draw():
    global d
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    strokeWeight(5)

    for t in range(d+1):
        for i in range(len(r)):
            if i == 0:
                stroke(0, 0, 255)
            elif i == 1:
                stroke(0, 255, 0)
            else:
                stroke(255, 0, 0)
            x = cX + 2 * r[i] * cos(radians(d)) + r[i] * cos(radians(2 * d))
            y = cY + 2 * r[i] * sin(radians(d)) - r[i] * sin(radians(2 * d))
            point(x, y)

    d = d + 1

    if d == 360:
        background(255)
        d = 0
```