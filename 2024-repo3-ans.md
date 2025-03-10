# レポート3 解答例

1.
```python
size(600, 600)
background(255, 255, 255)
r = 200       # 半径
cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

x0 = cX + r * cos(radians(0))
y0 = cY + r * sin(radians(0))

x60 = cX + r * cos(radians(60))
y60 = cY + r * sin(radians(60))

x120 = cX + r * cos(radians(120))
y120 = cY + r * sin(radians(120))

x180 = cX + r * cos(radians(180))
y180 = cY + r * sin(radians(180))

x240 = cX + r * cos(radians(240))
y240 = cY + r * sin(radians(240))

x300 = cX + r * cos(radians(300))
y300 = cY + r * sin(radians(300))

strokeWeight(5)
line(x0, y0, x120, y120)
line(x120, y120, x240, y240)
line(x240, y240, x0, y0)

line(x60, y60, x180, y180)
line(x180, y180, x300, y300)
line(x300, y300, x60, y60)
```

2.
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

    x60 = cX + r * cos(radians(60 + d))
    y60 = cY + r * sin(radians(60 + d))

    x120 = cX + r * cos(radians(120 + d))
    y120 = cY + r * sin(radians(120 + d))

    x180 = cX + r * cos(radians(180 + d))
    y180 = cY + r * sin(radians(180 + d))

    x240 = cX + r * cos(radians(240 + d))
    y240 = cY + r * sin(radians(240 + d))

    x300 = cX + r * cos(radians(300 + d))
    y300 = cY + r * sin(radians(300 + d))

    strokeWeight(5)
    line(x0, y0, x120, y120)
    line(x120, y120, x240, y240)
    line(x240, y240, x0, y0)

    line(x60, y60, x180, y180)
    line(x180, y180, x300, y300)
    line(x300, y300, x60, y60)

    d = (d + 1) % 360
```

3.
```python
# 静止画
size(600, 600)
background(255, 255, 255)
cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

strokeWeight(5)
# 0°から180°まで繰り返す
stroke(0, 0, 255)
a = 250
for d in range(180):
    x = cX + a * sin(radians(3 * d)) * cos(radians(d))
    y = cY + a * sin(radians(d)) * sin(radians(3 * d))
    point(x, y)
```


4.
```python
d = 0

def setup():
    size(600, 600)
    background(255, 255, 255)

def draw():
    global d
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y

    strokeWeight(5)
    # 0°から180°まで繰り返す
    stroke(0, 0, 255)
    a = 250
    x = cX + a * sin(radians(3 * d)) * cos(radians(d))
    y = cY + a * sin(radians(d)) * sin(radians(3 * d))
    point(x, y)

    d = d + 1
    if d == 180:
        background(255, 255, 255)
        d = 0
```
