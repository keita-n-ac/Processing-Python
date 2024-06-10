# 第9回目 練習問題 解答例
## 練習問題
1.   
```python
size(660, 660)
colorMode(HSB, 360, 100, 100)

for i in range(11):
    for j in range(11):
        fill(240, 10*(10-j), 10*(10-i))
        rect(j*60, i*60, 60, 60)
```

2-A.
```python
k = 0
def setup():
    size(600, 600)
    background(0, 0, 0)
    frameRate(5)

def draw():
    global k
    noStroke()
    for i in range(10):
        for j in range(10):
            if k == i:
                fill(255, 255, 0)
            else:
                fill(0, 0, 0)
            rect(j*60, i*60, 60, 60)
    k = (k + 1) % 10
```

2-B.
```python
k = 0
def setup():
    size(600, 600)
    background(0, 0, 0)
    frameRate(5)

def draw():
    global k
    noStroke()
    for i in range(10):
        for j in range(10):
            if k == 9 - i:
                fill(255, 255, 0)
            else:
                fill(0, 0, 0)
            rect(j*60, i*60, 60, 60)
    k = (k + 1) % 10
```

3.
```python
k = 0
def setup():
    size(600, 600)
    colorMode(HSB, 360, 100, 100)
    background(0, 0, 100)
    frameRate(5)

def draw():
    global k
    noStroke()
    for i in range(10):
        for j in range(10):
            if k >= i + j:
                fill((i+j)*18, 100, 100)
            else:
                fill(0, 0, 100)
            rect(j*60, i*60, 60, 60)
    k = (k + 1) % 20
```

4.
```python
size(600, 600)
colorMode(HSB, 360, 100, 100)
background(0, 0, 100)
strokeWeight(2)
for i in range(10):
    for j in range(10):
        for k in range(5):
            ellipse(30+j*60, 30+i*60, 60-12*k, 60-12*k)
```

5.
```python
size(600, 600)
colorMode(HSB, 360, 100, 100)
background(0, 0, 0)
strokeWeight(2)
for i in range(10):
    for j in range(10):
        for k in range(5):
            fill(60*k, 100, 100)
            ellipse(30+j*60, 30+i*60, 60-12*k, 60-12*k)
```