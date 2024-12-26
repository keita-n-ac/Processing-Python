# 第5回目 練習問題 解答例
## 練習問題
1. マウスのy座標位置に応じて画面の背景色を変更する（2分割）
```python
def setup():
    size(600, 600)

def draw():
    if mouseY < height/2:
        background(255, 0, 0)
    else:
        background(0, 0, 255)
    strokeWeight(4)
    line(0, height/2, width, height/2)
```

2. マウスのy座標位置に応じて画面の背景色を変更する（4分割）
```python
def setup():
    size(600, 600)

def draw():
    if mouseY < height/4:
        background(255, 0, 0)
    elif mouseY < height/4 * 2:
        background(0, 255, 0)
    elif mouseY < height/4 * 3:
        background(0, 0, 255)
    else:
        background(255, 255, 255)

    strokeWeight(4)
    line(0, height/4, width, height/4)
    line(0, height/4*2, width, height/4*2)
    line(0, height/4*3, width, height/4*3)
```

3. マウスの位置に応じて画面の背景色を変更する（境界線は，右上から左下の対角線）
```python
def setup():
    size(600, 600)

def draw():
    if mouseY < height - mouseX:
        background(255, 0, 0)
    else:
        background(0, 0, 255)

    strokeWeight(4)
    line(width, 0, 0, height)
```

4. マウスの位置に正方形を書き，マウスのx座標に応じて色変更する
   - 真ん中より左側にあると赤くなり，真ん中より右側にあると青くなる
```python
def setup():
    size(600, 600)

def draw():
    size = 30
    background(255, 255, 255)
    strokeWeight(2)
    if mouseX < width/2:
        fill(255, 0, 0)
    else:
        fill(0, 0, 255)
    rect(mouseX-size/2, mouseY-size/2, size, size)

    strokeWeight(4)
    line(width/2, 0, width/2, height)
```

5. マウスの位置に円を書き，マウスのy座標に応じて色変更する
   - 真ん中より上側にあると青くなり，真ん中より下側にあると赤くなる
```python
def setup():
    size(600, 600)

def draw():
    size = 30
    background(255, 255, 255)
    strokeWeight(2)
    if mouseY < height/2:
        fill(0, 0, 255)
    else:
        fill(255, 0, 0)
    ellipse(mouseX, mouseY, size, size)

    strokeWeight(4)
    line(0, height/2, width, height/2)
```