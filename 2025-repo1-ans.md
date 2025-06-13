# レポート1 解答例

1.
```python
size(900, 600)
background(255, 255, 255)
noStroke()
fill(255, 165, 0)
rect(0, 0, width, height/3)
ellipse(width/2, height/2, height/3-10, height/3-10)
fill(0, 255, 0)
rect(0, height/3*2, width, height/3)
```

2.
```python
def setup():
    size(600, 600)

def draw():
    background(255, 255, 255)
    size = 30
    strokeWeight(3)
    fill(0, 255, 255)
    ellipse(mouseX, mouseY, size, size)
    line(mouseX-size/2, mouseY, 0, mouseY)
    line(mouseX+size/2, mouseY, width, mouseY)
    line(mouseX, mouseY-size/2, mouseX, 0)
    line(mouseX, mouseY+size/2, mouseX, height)
```

3.
```python
def setup():
    size(600, 600)

def draw():
    background(255, 255, 255)
    size = 30
    strokeWeight(3)
    if mouseX > mouseY:
        fill(0, 255, 255)
    else:
        fill(255, 0, 255)
    ellipse(mouseX, mouseY, size, size)
    line(0, 0, width, height)
```
