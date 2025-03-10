# レポート2 解答例

1.
```python
size(600, 600)
colorMode(HSB, 360, 100, 100)
background(0, 0, 100)
noStroke()

for i in range(10):
    for j in range(i+1):
        fill(i*30, 100, 100)
        rect(width-(j+1)*60, i*60, 60, 60)
```

2.
```python
k = 0
def setup():
    size(600, 600)
    colorMode(HSB, 360, 100, 100)
    frameRate(5)
    noStroke()

def draw():
    global k
    background(0, 0, 100)
    for i in range(k+1):
        for j in range(i+1):
            fill(i*30, 100, 100)
            rect(width-(j+1)*60, i*60, 60, 60)
    k = (k + 1) % 10
```

3.
```python
k = 0
def setup():
    size(600, 600)
    strokeWeight(3)
    frameRate(3)

def draw():
    global k
    background(255, 255, 255)
    if k % 2 == 0:
        for i in range(10):
            if i % 2 == 0:
                fill(255, 255, 0)
            else:
                fill(0, 0, 0)
            ellipse(width/2, height/2, 60*(10-i), 60*(10-i))
    else:
        for i in range(10):
            if i % 2 == 0:
                fill(0, 0, 0)
            else:
                fill(255, 255, 0)
            ellipse(width/2, height/2, 60*(10-i), 60*(10-i))
    k = k + 1
```
