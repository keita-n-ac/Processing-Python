# 第14回目 練習問題 解答例
## 練習問題

1.
```python
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    noFill()
    strokeWeight(3)
    cX = width / 2
    cY = height / 2
    R = 240
    r = 80

    # 定円を描く
    stroke(0, 0, 0)
    ellipse(cX, cY, 2 * R, 2 * R)

    # 動く円の中心を求める
    cX2 = (R - r) * cos(radians(d)) + cX
    cY2 = (R - r) * sin(radians(d)) + cY
    stroke(0, 0, 255)
    ellipse(cX2, cY2, 2 * r, 2 * r)
    strokeWeight(10)
    point(cX2, cY2)

    for t in range(d+1):
        # 回転するときの円周上の定点を描く
        pX = (R - r) * cos(radians(t)) + r * cos(radians(t) - R * radians(t) / r) + cX
        pY = (R - r) * sin(radians(t)) + r * sin(radians(t) - R * radians(t) / r) + cY
        if t == d:
            strokeWeight(35)
        stroke(255, 0, 0)
        point(pX, pY)
    d = (d + 1) % 360
```

```python
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    noFill()
    strokeWeight(3)
    cX = width / 2
    cY = height / 2
    R = 240
    r = 60

    # 定円を描く
    stroke(0, 0, 0)
    ellipse(cX, cY, 2 * R, 2 * R)

    # 動く円の中心を求める
    cX2 = (R - r) * cos(radians(d)) + cX
    cY2 = (R - r) * sin(radians(d)) + cY
    stroke(0, 0, 255)
    ellipse(cX2, cY2, 2 * r, 2 * r)
    strokeWeight(10)
    point(cX2, cY2)

    for t in range(d+1):
        # 回転するときの円周上の定点を描く
        pX = (R - r) * cos(radians(t)) + r * cos(radians(t) - R * radians(t) / r) + cX
        pY = (R - r) * sin(radians(t)) + r * sin(radians(t) - R * radians(t) / r) + cY
        if t == d:
            strokeWeight(35)
        stroke(255, 0, 0)
        point(pX, pY)
    d = (d + 1) % 360
```

3.
```python
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    noFill()
    strokeWeight(3)
    cX = width / 2
    cY = height / 2
    R = 100
    r = 100

    # 定円を描く
    stroke(0, 0, 0)
    ellipse(cX, cY, 2 * R, 2 * R)

    # 動く円の中心を求める
    cX2 = (R + r) * cos(radians(d)) + cX
    cY2 = (R + r) * sin(radians(d)) + cY
    stroke(0, 0, 255)
    ellipse(cX2, cY2, 2 * r, 2 * r)
    strokeWeight(10)
    point(cX2, cY2)

    d = (d + 1) % 360
```

4.
```python
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    noFill()
    strokeWeight(3)
    cX = width / 2
    cY = height / 2
    R = 100
    r = 100

    # 定円を描く
    stroke(0, 0, 0)
    ellipse(cX, cY, 2 * R, 2 * R)

    # 動く円の中心を求める
    cX2 = (R + r) * cos(radians(d)) + cX
    cY2 = (R + r) * sin(radians(d)) + cY
    stroke(0, 0, 255)
    ellipse(cX2, cY2, 2 * r, 2 * r)
    strokeWeight(10)
    point(cX2, cY2)

    # 回転するときの円周上の定点を描く
    pX = (R + r) * cos(radians(d)) - r * cos(radians(d) + R * radians(d) / r) + cX
    pY = (R + r) * sin(radians(d)) - r * sin(radians(d) + R * radians(d) / r) + cY
    stroke(255, 0, 0)
    point(pX, pY)

    d = (d + 1) % 360
```

5.
```python
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    noFill()
    strokeWeight(3)
    cX = width / 2
    cY = height / 2
    R = 100
    r = 100

    # 定円を描く
    stroke(0, 0, 0)
    ellipse(cX, cY, 2 * R, 2 * R)

    # 動く円の中心を求める
    cX2 = (R + r) * cos(radians(d)) + cX
    cY2 = (R + r) * sin(radians(d)) + cY
    stroke(0, 0, 255)
    ellipse(cX2, cY2, 2 * r, 2 * r)
    strokeWeight(10)
    point(cX2, cY2)

    for t in range(d+1):
        # 回転するときの円周上の定点を描く
        pX = (R + r) * cos(radians(t)) - r * cos(radians(t) + R * radians(t) / r) + cX
        pY = (R + r) * sin(radians(t)) - r * sin(radians(t) + R * radians(t) / r) + cY
        if t == d:
            strokeWeight(35)
        stroke(255, 0, 0)
        point(pX, pY)
    d = (d + 1) % 360
```