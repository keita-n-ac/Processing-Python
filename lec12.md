# 第12回目
## 三角関数（基礎）

### 点で円（円弧）を表現
- 点で円（円弧）を表現する場合，三角関数(sinとcos)を使用する
- 中心($x$, $y$)，半径 $r$ の円を点で表現する場合，以下の式で書くことができる
$$x + r * \cos{\theta}$$
$$y + r * \sin{\theta}$$

- 1周分， $\theta$ を変えながら点を書くことで円を描くことができる
- ただし，processingは角度を度数法ではなく，弧度法で指定する．

### 角度の表現方法
- 度数法: 角度を表す際に，円の一周を 360°として扱う方法
  - 単位は```°```
  - 直角を90°と表現する
- 弧度法: 円弧の長さ と 円の半径 の比で角度を定義する方法
  - 単位は```ラジアン（rad）```
  - 円弧の長さを半径の長さで割った値が弧度法における角度になる
    - 半径 $r$ の円周は直径×円周率より， $2\pi r$ なので，弧度法における一周の角度は $2\pi r$ を $r$ で割った値である $2\pi$ となる
    - つまり， $360° = 2\pi$ radとなる
    - 直角は弧度法で $\pi$ /2 radと表現できる

# processingで三角関数を扱う
- 以下の方法を利用できる
  - ```sin(弧度法の角度)```: 指定した弧度法の角度におけるsin（正弦）の値を求めることができる
  - ```cos(弧度法の角度)```: 指定した弧度法の角度におけるcos（余弦）の値を求めることができる
  - ```radians(度数法の角度)```: 指定した度数法の角度における弧度法の角度を求めることができる
  - ```degrees(弧度法の角度)```: 指定した弧度法の角度における度数法の角度を求めることができる

```python
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

# 角度の方向
- 角度と方向の関係は以下の通り
  - 0°の方向: +X方向（右方向）
  - 90°の方向: +Y方向（下方向）
  - 180°の方向: -X方向（左方向）
  - 270°の方向: -Y方向（上方向）

```python
size(600, 600)
background(255, 255, 255)
r = 200       # 半径
cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

# 0°から359°まで繰り返す
for d in range(360):
    x = cX + r * cos(radians(d))
    y = cY + r * sin(radians(d))
    if d == 0:
        strokeWeight(50)
        stroke(255, 0, 0)
    elif d == 90:
        strokeWeight(50)
        stroke(0, 255, 0)
    elif d == 180:
        strokeWeight(50)
        stroke(0, 0, 255)
    elif d == 270:
        strokeWeight(50)
        stroke(0, 255, 255)
    else:
        strokeWeight(5)
        stroke(0, 0, 0)
    point(x, y)
```

### 正n角形の作成
- 正n角形は，円の中心のまわりをn等分し，円周上の点を結ぶことで作成できる
  - 360°を4で割ると90°になるため，0°→90°→180°→270°→0°で直線を書けば，正4角形（正方形）を書くことができる．

```python
size(600, 600)
background(255, 255, 255)
r = 200       # 半径
cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

x0 = cX + r * cos(radians(0))
y0 = cY + r * sin(radians(0))

x90 = cX + r * cos(radians(90))
y90 = cY + r * sin(radians(90))

x180 = cX + r * cos(radians(180))
y180 = cY + r * sin(radians(180))

x270 = cX + r * cos(radians(270))
y270 = cY + r * sin(radians(270))

strokeWeight(5)
line(x0, y0, x90, y90)
line(x90, y90, x180, y180)
line(x180, y180, x270, y270)
line(x270, y270, x0, y0)
```

- 270°の方向が上方向なので，0°の方向を上向きにしたい場合は，点の位置を計算する際に，270°を足せば良い
  - cosとsinの値は，周目が違っても問題無い
  - ただし，360°以上，720°未満の角度は2周目という意味になる

```python
size(600, 600)
background(255, 255, 255)
r = 200       # 半径
offset = 270  # 0°を上向きにするための角度
cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

# 0°から359°まで繰り返す
for d in range(360):
    x = cX + r * cos(radians(d + offset))
    y = cY + r * sin(radians(d + offset))
    if d == 0:
        strokeWeight(50)
        stroke(255, 0, 0)
    elif d == 90:
        strokeWeight(50)
        stroke(0, 255, 0)
    elif d == 180:
        strokeWeight(50)
        stroke(0, 0, 255)
    elif d == 270:
        strokeWeight(50)
        stroke(0, 255, 255)
    else:
        strokeWeight(5)
        stroke(0, 0, 0)
    point(x, y)
```

# 円弧の書き方
- 角度の範囲を一周ではなく，指定することで円弧を書くことができる
```python
size(600, 600)
background(255, 255, 255)
r = 200       # 半径
cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

strokeWeight(5)
# 30°から210°まで繰り返す
for d in range(30, 211):
    x = cX + r * cos(radians(d))
    y = cY + r * sin(radians(d))
    point(x, y)
```

# HSB形式
- HSB形式による色指定との連携
```python
size(600, 600)
colorMode(HSB, 360, 100, 100)
background(0, 0, 100)
r = 200       # 半径
cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

strokeWeight(5)
for d in range(360):
    x = cX + r * cos(radians(d))
    y = cY + r * sin(radians(d))
    stroke(d, 100, 100)
    point(x, y)
```

# 同心円の描画
- 半径を変更することで，同心円を書くことができる
```python
size(600, 600)
colorMode(HSB, 360, 100, 100)
background(0, 0, 100)
r1 = 50       # 半径1
r2 = 150      # 半径2
r3 = 250      # 半径3

cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

strokeWeight(5)
for d in range(360):
    x = cX + r1 * cos(radians(d))
    y = cY + r1 * sin(radians(d))
    stroke(d, 100, 100)
    point(x, y)

    x = cX + r2 * cos(radians(d))
    y = cY + r2 * sin(radians(d))
    stroke(d, 100, 100)
    point(x, y)

    x = cX + r3 * cos(radians(d))
    y = cY + r3 * sin(radians(d))
    stroke(d, 100, 100)
    point(x, y)
```

```python
# リストと2重ループを使用
size(600, 600)
colorMode(HSB, 360, 100, 100)
background(0, 0, 100)
r = [50, 150, 250]

cX = width/2  # 中心の座標x
cY = height/2 # 中心の座標y

strokeWeight(5)

for a in r:
    for d in range(360):
        x = cX + a * cos(radians(d))
        y = cY + a * sin(radians(d))
        stroke(d, 100, 100)
        point(x, y)
```

### アニメーション
- これまでのプログラムを利用して，円周上を移動するオブジェクトのアニメーションを作成できる

```python
d = 0

def setup():
    size(600, 600)
    colorMode(HSB, 360, 100, 100)

def draw():
    global d
    r = 200
    background(0, 0, 100)
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    x = cX + r * cos(radians(d))
    y = cY + r * sin(radians(d))
    strokeWeight(30)
    stroke(0, 100, 100)
    point(x, y)

    d = (d+1) % 360
```

```python
# 円周を書いてわかりやすくする
d = 0

def setup():
    size(600, 600)
    colorMode(HSB, 360, 100, 100)

def draw():
    global d
    r = 200
    background(0, 0, 100)
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    x = cX + r * cos(radians(d))
    y = cY + r * sin(radians(d))

    # 先に円周を書く
    strokeWeight(5)
    stroke(0, 100, 0)
    ellipse(cX, cY, 2*r, 2*r)
    # 円周上を移動する円を書く
    strokeWeight(30)
    stroke(0, 100, 100)
    point(x, y)

    d = (d+1) % 360
```

```python
# backgroundを適切に配置し，軌跡を書く
d = 0

def setup():
    size(600, 600)
    colorMode(HSB, 360, 100, 100)
    background(0, 0, 100)

def draw():
    global d
    r = 200
    cX = width/2  # 中心の座標x
    cY = height/2 # 中心の座標y
    x = cX + r * cos(radians(d))
    y = cY + r * sin(radians(d))
                
    strokeWeight(30)
    stroke(0, 100, 100)
    point(x, y)

    d = d + 1
    if d == 360:
        d = 0
        background(0, 0, 100)
```

### 練習問題
- サンプルプログラムを利用して，各問を満たすプログラムを作成しなさい
1. 正六角形を出力するプログラム
2. 五芒星を出力するプログラム
3. 色を変えながら円周上を移動する円のアニメーション
4. 4つ円からなる同心円を作成し，各円周上を移動する円のアニメーションプログラム
5. 2つの円からなる同心円の軌跡アニメーション
6. 円周上を移動する2つの円のアニメーション（ただし，2つの円は等間隔に配置すること）
