# 第12回目 練習問題 解答例
## 練習問題

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
line(x0, y0, x60, y60)
line(x60, y60, x120, y120)
line(x120, y120, x180, y180)
line(x180, y180, x240, y240)
line(x240, y240, x300, y300)
line(x300, y300, x0, y0)
```

2.
```python
size(600, 600)
background(255, 255, 255)
r = 200       # 半径
cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

x0 = cX + r * cos(radians(0))
y0 = cY + r * sin(radians(0))

x72 = cX + r * cos(radians(72))
y72 = cY + r * sin(radians(72))

x144 = cX + r * cos(radians(144))
y144 = cY + r * sin(radians(144))

x216 = cX + r * cos(radians(216))
y216 = cY + r * sin(radians(216))

x288 = cX + r * cos(radians(288))
y288 = cY + r * sin(radians(288))

strokeWeight(5)
line(x0, y0, x144, y144)
line(x144, y144, x288, y288)
line(x288, y288, x72, y72)
line(x72, y72, x216, y216)
line(x216, y216, x0, y0)
```

3.
```python
d = 0

def setup():
    size(600, 600)
    colorMode(HSB, 360, 100, 100)

def draw():
    global d
    r = 200
    background(0, 0, 100)
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    x = cX + r * cos(radians(d))
    y = cY + r * sin(radians(d))
    strokeWeight(5)
    stroke(0, 100, 0)
    ellipse(cX, cY, 2*r, 2*r)
    strokeWeight(30)
    stroke(d, 100, 100)
    point(x, y)

    d = (d+1) % 360
```

4.
```python
d = 0

def setup():
    size(600, 600)
    colorMode(HSB, 360, 100, 100)

def draw():
    global d
    background(0, 0, 100)
    r1 = 50       # 半径1
    r2 = 125      # 半径2
    r3 = 200      # 半径3
    r4 = 275      # 半径4
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    # 円周を先に表示
    strokeWeight(5)
    stroke(0, 0, 0)
    ellipse(cX, cY, 2*r4, 2*r4)
    ellipse(cX, cY, 2*r3, 2*r3)
    ellipse(cX, cY, 2*r2, 2*r2)
    ellipse(cX, cY, 2*r1, 2*r1)

    strokeWeight(30)
    x = cX + r1 * cos(radians(d))
    y = cY + r1 * sin(radians(d))
    stroke(d, 100, 100)
    point(x, y)

    x = cX + r2 * cos(radians(d))
    y = cY + r2 * sin(radians(d))
    stroke(d, 100, 100)
    point(x, y)

    x = cX + r3 * cos(radians(d))
    y = cY + r3 * sin(radians(d))
    stroke(d, 100, 100)
    point(x, y)

    x = cX + r4 * cos(radians(d))
    y = cY + r4 * sin(radians(d))
    stroke(d, 100, 100)
    point(x, y)

    d = (d + 1) % 360
```

5.
```python
d = 0

def setup():
    size(600, 600)
    colorMode(HSB, 360, 100, 100)
    background(0, 0, 100)

def draw():
    global d
    r1 = 150
    r2 = 250
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    strokeWeight(30)
    stroke(0, 100, 100)
    x = cX + r1 * cos(radians(d))
    y = cY + r1 * sin(radians(d))
    point(x, y)

    x = cX + r2 * cos(radians(d))
    y = cY + r2 * sin(radians(d))
    point(x, y)

    d = d + 1
    if d == 360:
        d = 0
        background(0, 0, 100)
```

6.
```python
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    r = 250
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    strokeWeight(5)
    stroke(0, 0, 0)
    ellipse(cX, cY, 2*r, 2*r)

    strokeWeight(30)
    stroke(255, 0, 0)
    x = cX + r * cos(radians(d))
    y = cY + r * sin(radians(d))
    point(x, y)
    stroke(0, 0, 255)
    x = cX + r * cos(radians(d+180))
    y = cY + r * sin(radians(d+180))
    point(x, y)

    d = (d + 1) % 360
```
