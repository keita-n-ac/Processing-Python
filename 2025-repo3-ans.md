# レポート3 解答例

1.
```python
size(600, 600)
background(255, 255, 255)
strokeWeight(3)
r = 250
cX = width/2    
cY = height/2    
x0 = cX + r * cos(radians(0))
y0 = cY + r * sin(radians(0))
x45 = cX + r * cos(radians(45))
y45 = cY + r * sin(radians(45))
x90 = cX + r * cos(radians(90))
y90 = cY + r * sin(radians(90))
x135 = cX + r * cos(radians(135))
y135 = cY + r * sin(radians(135))
x180 = cX + r * cos(radians(180))
y180 = cY + r * sin(radians(180))
x225 = cX + r * cos(radians(225))
y225 = cY + r * sin(radians(225))
x270 = cX + r * cos(radians(270))
y270 = cY + r * sin(radians(270))
x315 = cX + r * cos(radians(315))
y315 = cY + r * sin(radians(315))

line(x0, y0, x135, y135)
line(x135, y135, x270, y270)
line(x270, y270, x45, y45)
line(x45, y45, x180, y180)
line(x180, y180, x315, y315)
line(x315, y315, x90, y90)
line(x90, y90, x225, y225)
line(x225, y225, x0, y0)
```

2.
```python
d = 0
def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    strokeWeight(3)
    r = 250
    cX = width/2    
    cY = height/2    
    x0 = cX + r * cos(radians(0+d))
    y0 = cY + r * sin(radians(0+d))
    x45 = cX + r * cos(radians(45+d))
    y45 = cY + r * sin(radians(45+d))
    x90 = cX + r * cos(radians(90+d))
    y90 = cY + r * sin(radians(90+d))
    x135 = cX + r * cos(radians(135+d))
    y135 = cY + r * sin(radians(135+d))
    x180 = cX + r * cos(radians(180+d))
    y180 = cY + r * sin(radians(180+d))
    x225 = cX + r * cos(radians(225+d))
    y225 = cY + r * sin(radians(225+d))
    x270 = cX + r * cos(radians(270+d))
    y270 = cY + r * sin(radians(270+d))
    x315 = cX + r * cos(radians(315+d))
    y315 = cY + r * sin(radians(315+d))

    line(x0, y0, x135, y135)
    line(x135, y135, x270, y270)
    line(x270, y270, x45, y45)
    line(x45, y45, x180, y180)
    line(x180, y180, x315, y315)
    line(x315, y315, x90, y90)
    line(x90, y90, x225, y225)
    line(x225, y225, x0, y0)
    
    d = (d+1)%360
```

3.
```python
size(600, 600)
background(255, 255, 255)
strokeWeight(5)
stroke(0, 0, 255)
R = 250
cX = width/2    
cY = height/2
  
for d in range(360):
    x = cX + R * sin(radians(3 * d))
    y = cY + R * sin(radians(2 * d))
    point(x, y)
```

4.
```python
d = 0

def setup():
    size(600, 600)
    background(255, 255, 255)
    strokeWeight(5)
    stroke(0, 0, 255)

def draw():
    global d
    R = 250
    cX = width/2    
    cY = height/2  
    x = cX + R * sin(radians(3 * d))
    y = cY + R * sin(radians(2 * d))
    point(x, y)
    
    d = d + 1
    if d == 360:
        d = 0
        background(255, 255, 255)
```
