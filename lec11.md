# 第11回目
## リスト（応用）


### リスト
- 数値や文字列などを並べて格納できるデータ
  - リストと繰り返しを上手に使用することで，より複雑な処理を少ない行数で書くことができる
- 今回は複数のオブジェクトを描画するように使用する


### リストに関する操作
- ```len(リスト変数名)```: リストの要素数を求めることができる
- ```リスト変数名.append(値)```: カッコの中にある値をリストの最後に追加する
- 要素数が0のリスト（空リスト）を作成する場合，```リスト変数名 = []``` と書けばよい
- ```リスト * 整数```とすると，そのリストを整数回連結したリストを生成する

### リストと繰り返し処理
- 数値や文字列などを並べて格納しているため，繰り返し処理と相性がよく，以下の方法で1つずつ値を順番に取り出すことができる

```python
# サンプルプログラム1

# オブジェクト1つの描画の場合，リストは使用しなくて良い
size(600, 600)
background(255, 255, 255)
x = width/2         # x座標
y = height/2        # y座標
d = 100             # 直径
r = 255             # 赤要素
g = 0               # 緑要素
b = 0               # 青要素
fill(r, g, b)       # 色指定
ellipse(x, y, d, d) # 円を描画
```

```python
# サンプルプログラム2

# オブジェクト2つの描画の場合，
# リストを使用しないで書くと，それぞれ変数を用意する必要がある
size(600, 600)
background(255, 255, 255)

# 1つ目の描画
x1 = width/2 - 150      # x座標
y1 = height/2           # y座標
d1 = 70                 # 直径
r1 = 0                  # 赤要素
g1 = 255                # 緑要素
b1 = 0                  # 青要素
fill(r1, g1, b1)        # 色指定
ellipse(x1, y1, d1, d1) # 円を描画

# 2つ目の描画
x2 = width/2 + 150      # x座標
y2 = height/2           # y座標
d2 = 170                # 直径
r2 = 0                  # 赤要素
g2 = 0                  # 緑要素
b2 = 255                # 青要素
fill(r2, g2, b2)        # 色指定
ellipse(x2, y2, d2, d2) # 円を描画
```

```python
# サンプルプログラム3

# リストを使用して複数のオブジェクトを書く
size(600, 600)
background(255, 255, 255)

# 変数の宣言 -> for文で初期化 -> for文で描画の順番で行う

# 1: 変数の宣言
num = 2       # オブジェクトの数
x = [0] * num # x座標
y = [0] * num # y座標
d = [0] * num # 直径
r = [0] * num # 赤要素
g = [0] * num # 緑要素
b = [0] * num # 青要素

# 2: 変数の初期化（for文で）
for i in range(num):
    x[i] = int(random(0, width))
    y[i] = int(random(0, height))
    d[i] = int(random(30, 200))
    r[i] = int(random(0, 256))
    g[i] = int(random(0, 256))
    b[i] = int(random(0, 256))

# 3: 描画（for文で）
for i in range(num):
    fill(r[i], g[i], b[i])          # 色指定
    ellipse(x[i], y[i], d[i], d[i]) # 円を描画

```

- リストを宣言・初期化する際，空リストと```append```（要素を追加する）を使用しても問題無い

```python
# サンプルプログラム4

# リストを使用して複数のオブジェクトを書く
# 空リストとappendを使用した場合

size(600, 600)
background(255, 255, 255)

# 変数の宣言 -> for文で初期化 -> for文で描画の順番で行う

# 1: 変数（空リストで）の宣言
num = 10 # オブジェクトの数
x = []  
y = []
d = []
r = []
g = []
b = []

# 2: 変数の初期化（for文とappendで）
for i in range(num):
    # x座標
    temp = int(random(0, width))
    x.append(temp)
    # y座標
    temp = int(random(0, height))
    y.append(temp)
    # 直径
    temp = int(random(30, 200))
    d.append(temp)
    # 赤要素
    temp = int(random(0, 256))
    r.append(temp)
    # 緑要素
    temp = int(random(0, 256))
    g.append(temp)
    # 青要素
    temp = int(random(0, 256))
    b.append(temp)

# 3: 描画（for文で）
for i in range(num):
    fill(r[i], g[i], b[i])          # 色指定
    ellipse(x[i], y[i], d[i], d[i]) # 円を描画
```

- リストを使った複数のオブジェクトのアニメーションを行う場合，以下の通りで行う
    1. 最初に変数を宣言
    2. setup内でfor文で初期化
    3. draw内でfor文で描画・変数の更新
```python
# サンプルプログラム5

# リストを使用して複数のオブジェクトを書くアニメーション
# appendを使用した場合

# 変数の宣言（最初） -> for文で初期化（setup内で） -> for文で描画（draw内）の順番で行う

# 1: 変数（空リストで）の宣言
num = 10 # オブジェクトの数
x = []  
y = []
d = []
r = []
g = []
b = []
speedX = []

def setup():
    global x, y, d, r, g, b, speedX
    size(600, 600)
    # 2: 変数の初期化（for文とappendで）
    for i in range(num):
        # x座標
        temp = int(random(0, width))
        x.append(temp)
        # y座標
        temp = int(random(0, height))
        y.append(temp)
        # 直径
        temp = int(random(30, 200))
        d.append(temp)
        # 赤要素
        temp = int(random(0, 256))
        r.append(temp)
        # 緑要素
        temp = int(random(0, 256))
        g.append(temp)
        # 青要素
        temp = int(random(0, 256))
        b.append(temp)
        # 速度
        temp = random(0, 10)
        speedX.append(temp)

def draw():
    global x, speedX
    background(255, 255, 255)

    # 3: 描画（for文で）
    for i in range(num):
        fill(r[i], g[i], b[i])          # 色指定
        ellipse(x[i], y[i], d[i], d[i]) # 円を描画
        x[i] += speedX[i]
        if x[i] < 0 or x[i] > width:
            speedX[i] *= -1
```

### 文字を画面に表示
- Processingでは，以下の方法で文字列を画面に出力できる
  - ```textSize(size)```: 文字の大きさをsizeにする
  - ```text(data, x, y)```: 文字列dataを座標(x, y)に出力する
  - ```str(数値)```: 数値を文字列に変換する

```python
# サンプルプログラム6
x = 0
def setup():
    size(600, 600)
    
def draw():
    global x
    background(255, 255, 255)
    fill(0, 0, 0) # 文字の色
    textSize(30)
    text(str(x), 100, 100)
    x += 1
```

```python
# サンプルプログラム7
x = 0
def setup():
    size(600, 600)

def draw():
    global x
    background(255, 255, 255)
    if x > 450:
        fill(0, 0, 255) # 文字の色
    elif x > 300:
        fill(0, 255, 0) # 文字の色
    elif x > 150:
        fill(255, 0, 0) # 文字の色
    else:
        fill(0, 0, 0)
    textSize(x/2+10)
    text(str(x), 50, 300)
    x = (x + 1) % 601
```

### 軌跡の描画
- 点が一定の条件に従って動くときに描く図形を軌跡とよぶ
- 点を繋げることで線を書くことができる
- 以下の式を用いることで，点を繋げることで座標a($x_{a}$, $y_{a}$)から座標b($x_{b}$, $y_{b}$)へ向かう直線を書くことができる
  - x座標: $$x_{a} * (1 - t) + x_{b} * t $$
  - y座標: $$y_{a} * (1 - t) + y_{b} * t $$
- $t$を0〜1の値にする．
  - $t$を細かくすることで，直線にする
- ```float(整数)```: 整数を小数にする
  - Processingでは整数と整数の割り算は整数の値になるので注意
  - ```1 / 10```は0となる
  - ```float(1) / 10```は0.1となる
```python
# 点を繋げることで(100, 100)から(500, 500)へ向かう直線を作成する
size(600, 600)
background(255, 255, 255)
xa = 100
ya = 100
xb = 500
yb = 500
strokeWeight(32)  # pointの大きさ
stroke(0, 0, 255) # pointの色
point(xa, ya)
point(xb, yb)

d = 5 # tを5分割

strokeWeight(16) # pointの大きさ
stroke(0, 0, 0)  # pointの色
for i in range(d + 1):
    t = float(i) / d # float(整数)で整数を小数に変換
    x = xa * (1 - t) + xb * t
    y = ya * (1 - t) + yb * t
    point(x, y)
```

```python
# (100, 100)から(500, 500)へ向かう点のアニメーション
i = 0

def setup():
    size(600, 600)
    frameRate(5)

def draw():
    global i
    background(255, 255, 255)
    xa = 100
    ya = 100
    xb = 500
    yb = 500
    strokeWeight(32)  # pointの大きさ
    stroke(0, 0, 255) # pointの色
    point(xa, ya)
    point(xb, yb)

    d = 30 # tを30分割

    strokeWeight(16) # pointの大きさ
    stroke(0, 0, 0)  # pointの色
    t = float(i) / d # float(整数)で整数を小数に変換
    x = xa * (1 - t) + xb * t
    y = ya * (1 - t) + yb * t
    point(x, y)

    # tの値を表示
    fill(0, 0, 255)
    textSize(32)
    text('t: ' + str(t), 50, 500)

    i = (i+1) % (d+1)
```

### 練習問題
- サンプルプログラムを利用して，各問を満たすプログラムを作成しなさい
1. 1個の円が左右に衝突した場合に反射するアニメーションプログラムを作成し，x座標の位置も画面に出力するようにしなさい
2. 50個の円が上下に衝突した場合に反射するアニメーション
3. 100個の円が上下左右に衝突した場合に反射するアニメーション
4. 点を繋げることで，座標1(100, 500)から座標2(500, 100)へ向かう直線を作成しなさい
5. 座標1(100, 500)から座標2(500, 100)へ向かう点アニメーションを作成しなさい
