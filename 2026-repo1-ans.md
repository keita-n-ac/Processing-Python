# レポート1 解答例

### 問題1
```python
size(900, 600)
noStroke()
background(255, 0, 0)
fill(0, 255, 0)
rect(width/4, 0, width/4*3, height/3)
fill(255, 255, 255)
rect(width/4, height/3, width/4*3, height/3)
fill(0, 0, 0)
rect(width/4, height/3*2, width/4*3, height/3)
```

### 問題2
```python
def setup():
    size(600, 600)

def draw():
    background(255, 255, 255)
    strokeWeight(3)
    fill(0, 255, 255)
    line(mouseX-25, mouseY-25, mouseX, mouseY)
    line(mouseX-25, mouseY, mouseX, mouseY)
    line(mouseX-25, mouseY+25, mouseX, mouseY)
    line(mouseX, mouseY-25, mouseX, mouseY)
    line(mouseX, mouseY+25, mouseX, mouseY)
    line(mouseX+25, mouseY-25, mouseX, mouseY)
    line(mouseX+25, mouseY, mouseX, mouseY)
    line(mouseX+25, mouseY+25, mouseX, mouseY)
    ellipse(mouseX, mouseY, 25, 25)
```

### 問題3
```python
def setup():
    size(600, 600)

def draw():
    background(255, 255, 255)
    strokeWeight(3)
    line(width/3, 0, width/3, height)
    line(width/3*2, 0, width/3*2, height)
    if width/3 > mouseX:
        fill(255, 0, 0)
    elif width/3*2 < mouseX:
        fill(0, 0, 255)
    else:
        fill(0, 255, 0)
    ellipse(mouseX, mouseY, 30, 30)
```
