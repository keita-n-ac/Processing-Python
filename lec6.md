# 第6回目
## 条件分岐を使用したアニメーション（応用編）

### 条件分岐復習
```python
r = 50

def setup():
    size(600, 600)

def draw():
    global r
    background(255, 255, 255)
    strokeWeight(5)
    if mouseY <= height/2:
        r += 10
    else:
        r -= 10
    ellipse(width/2, height/2, r, r)
    r = constrain(r, 50, 550)
```
### 論理演算子
- 2つ以上の条件を組み合わせ，真偽を判定する演算子
  - ```and``` : 論理積（使い方例: ```条件式A and 条件式B```）
    - 2つの条件を満たしている場合: ```True```
    - どちらか一方の条件式が満たしていない場合: ```False```
  - ```or``` : 論理和（使い方例: ```条件式A or 条件式B```）
    - どちらか一方の条件を満たしている場合: ```True```
    - 2つの条件を満たしていない場合: ```False```

| 論理演算子 | 日本語意味 | 
|-----|-----| 
| and | かつ |
| or | または |

- 例1: 変数xが0以上かつ300以下
  - ```x >= 0 and x <= 300```
- 例2: 変数xが100未満または500以上
  - ```x < 100 or x >= 500```
```python
def setup():
    size(600, 600)

def draw():
    background(255, 255, 255)
    strokeWeight(5)
    if mouseX >= width/2 and mouseY >= height/2:
        background(0, 255, 255)
    line(width/2, 0, width/2, height)
    line(0, height/2, width, height/2)
```

```python
speed = 3
x = 0
def setup():
    size(600, 600)

def draw():
    global x, speed
    background(255, 255, 255)
    fill(255, 0, 255)
    strokeWeight(5)
    ellipse(x, height/2, 50, 50)
    x += speed
    if x < 0 or x > width:
        speed *= -1
```

### mousePressed変数
- Processingではマウスが押されているかどうかを判断するために```mousePressed```変数が用意されている
  - この```mousePressed```は真偽値（```True``` / ```False```）である
  - ```True```の場合: マウスが押されている状態
  - ```False```の場合: マウスが押されていない状態

```python
r = 50

def setup():
    size(600, 600)

def draw():
    global r
    background(255, 255, 255)
    strokeWeight(5)
    if mousePressed == True:
        r += 10
    else:
        r -= 10
    ellipse(width/2, height/2, r, r)
    r = constrain(r, 50, 550)
```

- ```if```文などの条件式を書く際に，```真偽値変数 == True```を```真偽値変数```と省略して書いても条件式となる
  - ```if mousePressed == True:```を```if mousePressed:```と省略することができる
```python
r = 50

def setup():
    size(600, 600)

def draw():
    global r
    background(255, 255, 255)
    strokeWeight(5)
    if mousePressed:
        r += 10
    else:
        r -= 10
    ellipse(width/2, height/2, r, r)
    r = constrain(r, 50, 550)
```
### key変数
- Processingでは押しているキーを判断するために```key```変数が用意されている
  - この```key```は文字列として扱うため，シングルクォーテーション```''```かダブルクォーテーションで```""```で囲む必要がある
```python
def setup():
    size(600, 600)

def draw():
    background(255, 255, 255)
    if key == 'a': # aが押されたとき
        background(0, 255, 0)
    elif key == 'b': # bが押されたとき
        background(0, 0, 255)
    else: # それ以外の場合
        background(255, 255, 255)
```
### pmouseX, pmouseY変数
- Processingでは前フレームのマウスの位置を記憶する```pmouseX, pmouseY```変数がそれぞれ用意されている
```python
def setup():
    size(600, 600)
    background(255, 255, 255)

def draw():
    line(pmouseX, pmouseY, mouseX, mouseY)
```

```python
def setup():
    size(600, 600)
    background(255, 255, 255)

def draw():
    line(pmouseX, pmouseY, mouseX, mouseY)
    if key == 'a':
        stroke(0, 255, 0)
        strokeWeight(5)
    elif key == 'r':
        background(255, 255, 255)
        # 別のキーを押さない限り，何も書けなくなることに注意
    else:
        stroke(0, 0, 0)
        strokeWeight(1)
```

```python
def setup():
    size(600, 600)
    background(255, 255, 255)

def draw():
    # キーボード処理
    if key == 'a':
        fill(255, 255, 0)
        strokeWeight(5)
    elif key == 'b':
        fill(0, 255, 255)
        strokeWeight(7)
    elif key == 'r':
        background(255, 255, 255)
        # 別のキーを押さない限り，何も書けなくなることに注意
    else:
        stroke(0, 0, 0)
        strokeWeight(1)

    # マウス処理
    if mousePressed:
        ellipse(mouseX, mouseY, 50, 50)
```

## 練習問題
- サンプルプログラムを参考に，大きさ600, 600の画面に対して，以下のプログラムを書きなさい
  1. 上部と下部で円が跳ね返るアニメーションを作成しなさい（移動方向: 上下，位置: 画面中央）
  2. 画面を十字に分割して，マウスの位置に応じて，画面の背景色を変更する（4分割4種類）
  3. 画面を十字に分割して，マウスの位置に応じて，その領域の色を変更する（4分割4種類）
  4. 画面を2つの対角線に分割して，マウスの位置に応じて，画面の背景色を変更する（4分割4種類）
  5. キーボードのxを押している状態でクリックするとマウスの位置に正方形を書き，キーボードのyを押している状態でクリックするとマウスの位置に円を書き，rを押すと画面の背景をリセットするプログラムを作成しなさい