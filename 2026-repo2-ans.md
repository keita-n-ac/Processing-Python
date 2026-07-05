# レポート2 解答例

### 問題1
```python
size(600, 600)
background(255, 255, 255)
colorMode(HSB, 360, 100, 100)

for i in range(10):
    x = width - 60 * (i+1)
    for j in range(i + 1):
        fill(j*30, 100, 100)
        rect(x + 60*j, i*60, 60, 60)
```

### 問題2
```python
k = 0
def setup():
    size(600, 600)
    frameRate(2)
    colorMode(HSB, 360, 100, 100)
    background(0, 0, 100)
 
def draw():
    global k
    background(0, 0, 100)
    for i in range(10):
        x = width - 60 * (i+1)
        for j in range(k + 1):
            fill(j*30, 100, 100)
            rect(x + 60*j, i*60, 60, 60)
    k += 1
    if k == 10:
        k = 0
```

### 問題3
```python
k = 0
def setup():
    size(600, 600)
    frameRate(2)
    noStroke()
    background(255, 255, 255)
 
def draw():
    global k
    background(255, 255, 255)
    if k == 0:
        for i in range(10):
            if i % 2 == 0:
                fill(255, 255, 0)
            else:
                fill(0, 0, 0)
            ellipse(150, 150, 300-30*i, 300-30*i)
    elif k == 1:
        for i in range(10):
            if i % 2 == 0:
                fill(0, 0, 0)
            else:
                fill(255, 255, 0)
            ellipse(450, 150, 300-30*i, 300-30*i)
    elif k == 2:
        for i in range(10):
            if i % 2 == 0:
                fill(0, 0, 0)
            else:
                fill(255, 255, 0)
            ellipse(150, 450, 300-30*i, 300-30*i)            
    else:
        for i in range(10):
            if i % 2 == 0:
                fill(255, 255, 0)
            else:
                fill(0, 0, 0)
            ellipse(450, 450, 300-30*i, 300-30*i)
    k += 1
    if k == 4:
        k = 0
```
