# 第10回目 練習問題 解答例
## 練習問題

1.
```python
speed = 3
x = 0
y = 0

def setup():
    global y
    size(600, 600)
    y = height/2

def draw():
    global x, y, speed
    background(255, 255, 255)
    fill(255, 0, 255)
    strokeWeight(5)
    ellipse(x, y, 60, 60)
    x += speed
    if x < 0 or x > width:
        speed *= -1
        y = int(random(0, height+1))
```

2.
```python
speed = 3
x = 0
r = 0 # 赤要素
g = 0 # 緑要素
b = 0 # 青要素

def setup():
    global r, g, b
    size(600, 600)
    r = 255
    g = 0
    b = 255

def draw():
    global x, r, g, b, speed
    background(255, 255, 255)
    fill(r, g, b)
    strokeWeight(5)
    ellipse(x, height/2, 60, 60)
    x += speed
    if x < 0 or x > width:
        speed *= -1
        r = int(random(0, 256))
        g = int(random(0, 256))
        b = int(random(0, 256))
```

3.
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
        s = random(0, 10)
        if speed > 0:
            speed = s
        else:
            speed = -s
    x = constrain(x, 0, width) # 調整のため有った方が良い
```

4.
```python
num = 10
speed = [3] * num
x = [0] * num

def setup():
    global x, speed
    size(600, 600)
    for i in range(num):
        speed[i] = random(0, 10)
        x[i] = width/2

def draw():
    global x, speed
    background(255, 255, 255)
    fill(255, 0, 255)
    strokeWeight(5)
    for i in range(num):
        ellipse(x[i], 30+60*i, 60, 60)
        x[i] += speed[i]
        if x[i] < 0 or x[i] > width:
            speed[i] *= -1
```