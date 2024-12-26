# 第4回目 練習問題 解答例
## 練習問題
1. マウスの位置に応じて領域を2つに分割する（境界線は横方向とし，各領域に色を付ける） 
```python
def setup():
    size(600, 600)

def draw():
    background(255, 255, 255)
    noStroke()
    fill(255, 255, 0)
    rect(0, 0, width, mouseY)
    fill(0, 255, 0)
    rect(0, mouseY, width, height-mouseY)
```

2. マウスの位置に応じて領域を4つに分割する（境界線は十字方向，各領域に色を付ける）
```python
def setup():
    size(600, 600)

def draw():
    background(255, 255, 255)
    noStroke()
    fill(255, 0, 0)
    rect(0, 0, mouseX, mouseY)
    fill(0, 255, 0)
    rect(mouseX, 0, width-mouseX, mouseY)
    fill(0, 0, 255)
    rect(0, mouseY, mouseX, height-mouseY)
    fill(255, 255, 0)
    rect(mouseX, mouseY, width-mouseX, height-mouseY)
```

3. マウスの位置に正方形を書くアニメーション
```python
def setup():
    size(600, 600)

def draw():
    size = 50
    background(255, 255, 255)
    strokeWeight(3)
    fill(255, 0, 255)
    rect(mouseX-size/2, mouseY-size/2, size, size)
```

4. マウスの位置に9個の正方形を書くアニメーション（図のように3×3の正方形を書くこと） 

```python
def setup():
    size(600, 600)

def draw():
    size = 50
    background(255, 255, 255)
    strokeWeight(3)
    fill(0, 255, 255)
    rect(mouseX-size/2, mouseY-size/2-size, size, size)
    rect(mouseX-size/2-size, mouseY-size/2-size, size, size)
    rect(mouseX-size/2+size, mouseY-size/2-size, size, size)
    rect(mouseX-size/2, mouseY-size/2, size, size)
    rect(mouseX-size/2-size, mouseY-size/2, size, size)
    rect(mouseX-size/2+size, mouseY-size/2, size, size)
    rect(mouseX-size/2, mouseY-size/2+size, size, size)
    rect(mouseX-size/2-size, mouseY-size/2+size, size, size)
    rect(mouseX-size/2+size, mouseY-size/2+size, size, size)
```

5. マウスの位置に4個の正方形を書くアニメーション（図のように2×2の正方形を書くこと）

```python
def setup():
    size(600, 600)

def draw():
    size = 50
    background(255, 255, 255)
    strokeWeight(3)
    fill(0, 255, 255)
    rect(mouseX, mouseY, size, size)
    rect(mouseX, mouseY-size, size, size)
    rect(mouseX-size, mouseY-size, size, size)
    rect(mouseX-size, mouseY, size, size)
```