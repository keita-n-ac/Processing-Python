# レポート1 解答例

1.
```python
size(600, 400)
background(255, 255, 255)
noStroke()
fill(0, 255, 0)
rect(0, 0, width/3, height)
fill(255, 0, 0)
rect(width/3*2, 0, width/3, height)
```

2.
```python
size(600, 400)
background(255, 255, 255)
noStroke()
fill(255, 0, 0)
rect(0, 0, width, height/3)
fill(0, 0, 255)
rect(0, height/3*2, width, height/3)
```

3.
```python
def setup():
    size(600, 600)

def draw():
    size = 30
    background(255, 255, 255)
    if mouseY < height/2:
        fill(0, 0, 255)
    else:
        fill(255, 0, 0)
    noStroke()
    rect(mouseX-size/2, mouseY-size/2, size, size)
    stroke(0, 0, 0)
    strokeWeight(3)
    line(0, height/2, width, height/2)
```
