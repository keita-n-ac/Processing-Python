# 第6回目 練習問題 解答例
## 練習問題
1. 上部と下部で円が跳ね返るアニメーションを作成しなさい（移動方向: 上下，位置: 画面中央）
```python
speed = 5
y = 0

def setup():
    size(600, 600)

def draw():
    global speed, y
    size = 40
    background(255, 255, 255)
    strokeWeight(4)
    fill(255, 0, 255)
    ellipse(width/2, y, size, size)
    y = y + speed
    if y < 0 or y > height:
        speed = speed * -1
```

2. 画面を十字に分割して，マウスの位置に応じて，画面の背景色を変更する（4分割4種類）
```python
def setup():
    size(600, 600)

def draw():
    if mouseX < width/2 and mouseY < height/2:
        background(255, 0, 0)
    elif mouseX < width/2 and mouseY >= height/2:
        background(0, 255, 0)
    elif mouseX >= width/2 and mouseY < height/2:
        background(0, 0, 255)
    else:
        background(255, 255, 255)
    strokeWeight(4)
    line(width/2, 0, width/2, height)
    line(0, height/2, width, height/2)
```

3. 画面を十字に分割して，マウスの位置に応じて，その領域の色を変更する（4分割4種類）
```python
def setup():
    size(600, 600)

def draw():
    background(255, 255, 255)
    fill(0, 0, 0)
    if mouseX < width/2 and mouseY < height/2:
        rect(0, 0, width/2, height/2)
    elif mouseX < width/2 and mouseY >= height/2:
        rect(0, height/2, width/2, height/2)
    elif mouseX >= width/2 and mouseY < height/2:
        rect(width/2, 0, width/2, height/2)
    else:
        rect(width/2, height/2, width/2, height/2)
    strokeWeight(4)
    line(width/2, 0, width/2, height)
    line(0, height/2, width, height/2)
```

4. 画面を2つの対角線に分割して，マウスの位置に応じて，画面の背景色を変更する（4分割4種類）
```python
def setup():
    size(600, 600)

def draw():
    if mouseX < mouseY and mouseY < height - mouseX:
        background(255, 255, 0)
    elif mouseX >= mouseY and mouseY < height - mouseX:
        background(0, 255, 255)
    elif mouseX < mouseY and mouseY >= height - mouseX:
        background(255, 0, 255)
    else:
        background(255, 255, 255)
    strokeWeight(4)
    line(0, 0, width, height)
    line(width, 0, 0, height)
```

5. キーボードのxを押している状態でクリックするとマウスの位置に正方形を書き，キーボードのyを押している状態でクリックするとマウスの位置に円を書き，rを押すと画面の背景をリセットするプログラムを作成しなさい
```python
def setup():
    size(600, 600)
    background(255, 255, 255)

def draw():
    size = 30
    # キーボード処理
    if key == 'x' and mousePressed:
        fill(255, 255, 0)
        strokeWeight(4)
        ellipse(mouseX, mouseY, size, size)
    elif key == 'y' and mousePressed:
        fill(0, 255, 255)
        strokeWeight(3)
        rect(mouseX-size/2, mouseY-size/2, size, size)
    elif key == 'r':
        background(255, 255, 255)
        # 別のキーを押さない限り，何も書けなくなることに注意
    else:
        fill(255, 255, 255)
        stroke(0, 0, 0)
        strokeWeight(1)
```