# 第13回目
## 三角関数（応用）

### 復習: 点で円（円弧）を表現
- 点で円（円弧）を表現する場合，三角関数(sinとcos)を使用する
- 中心( $x_{c}$ , $y_{c}$ )，半径 $r$ の円を点で表現する場合，以下の式で書くことができる
$$x_{c} + r \cos{\theta}$$
$$y_{c} + r \sin{\theta}$$

- 1周分， $\theta$ を変えながら点を書くことで円を描くことができる
- ただし，processingは角度を度数法ではなく，弧度法で指定する．

# processingで三角関数を扱う
- ```sin(弧度法の角度)```: 指定した弧度法の角度におけるsin（正弦）の値を求めることができる
- ```cos(弧度法の角度)```: 指定した弧度法の角度におけるcos（余弦）の値を求めることができる
- ```radians(度数法の角度)```: 指定した度数法の角度における弧度法の角度を求めることができる
```python
# 静止画
size(600, 600)
background(255, 255, 255)
r = 200       # 半径
cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

strokeWeight(5)
# 0°から359°まで繰り返す
for d in range(360):
    x = cX + r * cos(radians(d))
    y = cY + r * sin(radians(d))
    point(x, y)
```

```python
# 動画
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    r = 200       # 半径
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    # 円周を先に表示
    strokeWeight(3)
    stroke(0, 0, 0)
    ellipse(cX, cY, 2*r, 2*r)
    # 円周上を動く円を表示
    strokeWeight(30)
    stroke(0, 0, 255)
    x = cX + r * cos(radians(d))
    y = cY + r * sin(radians(d))
    point(x, y)
    d = (d+1) % 360
```
- 角度を1度ずつ小さくすると，反時計回りになる
```python
# 動画
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    r = 200       # 半径
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    # 円周を先に表示
    strokeWeight(3)
    stroke(0, 0, 0)
    ellipse(cX, cY, 2*r, 2*r)
    # 円周上を動く円を表示
    strokeWeight(30)
    stroke(0, 0, 255)
    x = cX + r * cos(radians(-d))
    y = cY + r * sin(radians(-d))
    point(x, y)
    d = (d+1) % 360
```

```python
# 動画
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    r1 = 250      # 半径1
    r2 = 150       # 半径2
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    # 円周を先に表示
    strokeWeight(3)
    stroke(0, 0, 0)
    ellipse(cX, cY, 2*r1, 2*r1)
    ellipse(cX, cY, 2*r2, 2*r2)

    # 円周上を動く円を表示
    strokeWeight(30)
    stroke(0, 0, 255)
    x = cX + r1 * cos(radians(d))
    y = cY + r1 * sin(radians(d))
    point(x, y)

    stroke(255, 0, 0)
    x = cX + r2 * cos(radians(-d))
    y = cY + r2 * sin(radians(-d))
    point(x, y)

    d = (d+1) % 360
```

- 角度をずらしながら描画することで，オブジェクトを回転することができる

```python
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    r = 250
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    strokeWeight(5)
    stroke(0, 0, 0)
    ellipse(cX, cY, 2*r, 2*r)

    x1 = cX + r * cos(radians(d))
    y1 = cY + r * sin(radians(d))
    x2 = cX + r * cos(radians(d+180))
    y2 = cY + r * sin(radians(d+180))

    # 線を書く
    strokeWeight(5)
    stroke(0, 0, 0)
    line(x1, y1, x2, y2)

    # 円周上を動くオブジェクトを書く
    strokeWeight(30)
    stroke(255, 0, 0)
    point(x1, y1)
    stroke(0, 0, 255)
    point(x2, y2)

    d = (d+1)%360
```

```python
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    r = 250
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    strokeWeight(5)
    stroke(0, 0, 0)
    ellipse(cX, cY, 2*r, 2*r)

    x1 = cX + r * cos(radians(d))
    y1 = cY + r * sin(radians(d))
    x2 = cX + r * cos(radians(d+120))
    y2 = cY + r * sin(radians(d+120))
    x3 = cX + r * cos(radians(d+240))
    y3 = cY + r * sin(radians(d+240))

    # 線を書く
    strokeWeight(5)
    stroke(0, 0, 0)
    line(x1, y1, x2, y2)
    line(x2, y2, x3, y3)
    line(x3, y3, x1, y1)

    # 円周上を動くオブジェクトを書く
    strokeWeight(30)
    stroke(255, 0, 0)
    point(x1, y1)
    stroke(0, 0, 255)
    point(x2, y2)
    stroke(0, 255, 0)
    point(x3, y3)

    d = (d+1)%360
```
```python
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    r = 250
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    strokeWeight(5)
    stroke(0, 0, 0)
    ellipse(cX, cY, 2*r, 2*r)

    x1 = cX + r * cos(radians(d))
    y1 = cY + r * sin(radians(d))
    x2 = cX + r * cos(radians(d+90))
    y2 = cY + r * sin(radians(d+90))
    x3 = cX + r * cos(radians(d+180))
    y3 = cY + r * sin(radians(d+180))
    x4 = cX + r * cos(radians(d+270))
    y4 = cY + r * sin(radians(d+270))

    # 線を書く
    strokeWeight(5)
    stroke(0, 0, 0)
    line(x1, y1, x2, y2)
    line(x2, y2, x3, y3)
    line(x3, y3, x4, y4)
    line(x4, y4, x1, y1)

    # 円周上を動くオブジェクトを書く
    strokeWeight(30)
    stroke(255, 0, 0)
    point(x1, y1)
    stroke(0, 0, 255)
    point(x2, y2)
    stroke(0, 255, 0)
    point(x3, y3)
    stroke(0, 255, 255)
    point(x4, y4)

    d = (d+1)%360
```

- リストを使用することで，似ている処理を一つにまとめる
```python
num = 3
x = [0] * num
y = [0] * num
d = 0

def setup():
    size(600, 600)
    colorMode(HSB, 360, 100, 100)

def draw():
    global d, x, y
    background(0, 0, 100)
    r = 250
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    strokeWeight(1)
    stroke(0, 0, 0)
    ellipse(cX, cY, 2*r, 2*r)

    for i in range(num):
        x[i] = cX + r * cos(radians(d + i * float(360)/num))
        y[i] = cY + r * sin(radians(d + i * float(360)/num))

    # 線を書く
    strokeWeight(3)
    stroke(0, 0, 0)
    for i in range(num):
        j = (i+1) % num
        line(x[i], y[i], x[j], y[j])

    # 円周上を動くオブジェクトを書く
    strokeWeight(20)
    for i in range(num):
        angle = int(d + i * float(360)/num) % 360
        stroke(angle, 100, 100)
        point(x[i], y[i])

    d = (d+1)%360
```

### 媒介変数表示
$x$, $y$ の関係を $x$ と $y$ の直接の関係式で書くのでは無く，別の文字で， $x$ と $y$ を表現すること
- 円の方程式の場合
  - 直接の関係式の場合: $x^{2} + y^{2} = r^{2}$
  - 媒介変数の場合: $x = r \cos{\theta}$, $y = r \sin{\theta}$
    -  $\theta$ を媒介変数とよぶ（ $\theta$ で $x$ と $y$ をそれぞれ表しているため）
- 媒介変数表示を使用することで，様々な図形をかくことができる

- 螺旋の描画
    - 円を描く式を利用して，半径を増やしつつ，角度を回転させると螺旋を描画できる
- 螺旋の中心( $x_{c}$ ,  $y_{c}$ )とすると， $r$ を増やしながら，
$$x_{c} + r  \cos{\theta}$$
$$y_{c} + r  \sin{\theta}$$



```python
# 静止画
size(600, 600)
background(255, 255, 255)
r = 1       # 半径
cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

strokeWeight(5)
# 0°から1080°まで繰り返す(3回転)
stroke(0, 0, 255)
for d in range(1080):
    r += 0.27 # 半径を少しずつ増やす
    x = cX + r * cos(radians(d))
    y = cY + r * sin(radians(d))
    point(x, y)
```

- パスカルの蝸牛形
  - 媒介変数表示で以下の通りで書くと，カタツムリのように見える曲線を描くことが出来る
$$x = (a \cos{\theta} + l)\cos{\theta}$$
$$y = (a \cos{\theta} + l)\sin{\theta} $$
- $a$ と $l$ の値で，曲線の形状が変わる
- $\theta$ は1度ずつ1周分変化させる
- 螺旋の中心($x_{c}$, $y_{c}$)とすると，
$$x = x_{c} + (a \cos{\theta} + l)\cos{\theta}$$
$$y = y_{c} + (a \cos{\theta} + l)\sin{\theta} $$

```python
# 静止画
size(600, 600)
background(255, 255, 255)
cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

strokeWeight(5)
# 0°から360°まで繰り返す
stroke(0, 0, 255)
a = 150
l = 100
for d in range(360):
    x = cX + (a * cos(radians(d)) + l) * cos(radians(d))
    y = cY + (a * cos(radians(d)) + l) * sin(radians(d))
    point(x, y)
```
- アステロイド
  - 媒介変数表示で以下の通りで書くと，ひし形に似ている星のように見える曲線を描くことが出来る
$$x = a \cos^{3}{\theta}$$
$$y = a \sin^{3}{\theta}$$
- $a$ の値で，曲線の形状が変わる
- $\theta$ は1度ずつ1周分変化させる
- 中心($x_{c}$, $y_{c}$)とすると，
$$x = x_{c} + a \cos^{3}{\theta}$$
$$y = y_{c} + a \sin^{3}{\theta}$$

```python
# 静止画
size(600, 600)
background(255, 255, 255)
cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

strokeWeight(5)
# 0°から360°まで繰り返す
stroke(0, 0, 255)
a = 250
for d in range(360):
    x = cX + a * cos(radians(d)) * cos(radians(d)) * cos(radians(d))
    y = cY + a * sin(radians(d)) * sin(radians(d)) * sin(radians(d))
    point(x, y)
```

```python
# アステロイド軌跡アニメーション
# 1周は360度

d = 0 # 角度

def setup():
    size(600, 600)
    background(255, 255, 255)

def draw():
    global d
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    strokeWeight(5)
    stroke(255, 0, 0)
    a = 250
    x = cX + a * cos(radians(d)) * cos(radians(d)) * cos(radians(d))
    y = cY + a * sin(radians(d)) * sin(radians(d)) * sin(radians(d))
    point(x, y)

    d = d + 1

    if d == 360:
        background(255)
        d = 0
```

```python
# アステロイド軌跡アニメーション
# 1周は360度

d = 0 # 角度
a = [50, 150, 250]

def setup():
    size(600, 600)
    background(255, 255, 255)

def draw():
    global d
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    strokeWeight(5)
    stroke(255, 0, 0)
    for i in range(len(a)):
        if i == 0:
            stroke(255, 0, 0)
        elif i == 1:
            stroke(0, 255, 0)
        else:
            stroke(0, 0, 255)
        x = cX + a[i] * cos(radians(d)) * cos(radians(d)) * cos(radians(d))
        y = cY + a[i] * sin(radians(d)) * sin(radians(d)) * sin(radians(d))
        point(x, y)

    d = d + 1

    if d == 360:
        background(255)
        d = 0
```

- 文字と軌跡を同時表示したい場合は，backgroundによる画面初期化のタイミングに気をつけること
```python
# アステロイド軌跡アニメーション
# 1周は360度

d = 0 # 角度
a = [50, 150, 250]

def setup():
    size(600, 600)
    frameRate(20)

def draw():
    global d
    background(255, 255, 255)
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    strokeWeight(5)
    stroke(255, 0, 0)
    for t in range(d+1):
        for i in range(len(a)):
            if i == 0:
                stroke(255, 0, 0)
            elif i == 1:
                stroke(0, 255, 0)
            else:
                stroke(0, 0, 255)
            x = cX + a[i] * cos(radians(t)) * cos(radians(t)) * cos(radians(t))
            y = cY + a[i] * sin(radians(t)) * sin(radians(t)) * sin(radians(t))
            point(x, y)

    d = d + 1
    if d == 360:
        background(255)
        d = 0

    # 文字の描画
    fill(0, 0, 0)
    textSize(36)
    text('angle: ' + str(d), 20, 550)
```


### 練習問題
- サンプルプログラムを利用して，各問を満たすプログラムを作成しなさい
1. 五芒星が回転するアニメーションプログラム

2. アルキメデスの螺旋とよばれる間隔が一定の螺旋を描いてください
    - 螺旋の中心($x_{c}$, $y_{c}$)とすると，
     $$x_{c} + a \theta  \cos{\theta}$$
     $$y_{c} + a \theta  \sin{\theta}$$
    - $a$は定数である（今回は $a = 4.5$ ,  $\theta$ を10回転させること）
3. アルキメデスの螺旋を描く軌跡のアニメーションを作成しなさい

4. アルキメデスの螺旋を描く軌跡と同時に角度の値を表示するアニメーションを作成しなさい

5. デルトイドとよばれる三芒形を描いてください
   - デルトイドの中心($x_{c}$, $y_{c}$)とすると，
    $$x_{c} + 2 r \cos{\theta}+ r \cos{2\theta}$$
    $$y_{c} + 2 r \sin{\theta}- r \sin{2\theta}$$
   - $r$ は定数である（今回は $r = 75$ ,  $\theta$ を1回転させること）

6. $r$ が15, 45, 75の時のデルトイドの軌跡を同時に描くアニメーションを作成しなさい
