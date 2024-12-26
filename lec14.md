# 第14回目
## まとめ（これまでの復習）

### Processingの応用例
- マウス・キーボードとのインタラクション
- メディアファイル（画像，音楽，動画など）との連携
- 電子回路との連携
- スマートフォン，Webとの連携

##### ステップバイステップ形式で，簡単な物理ゲームである『ハエたたきゲーム』の作成方法を学ぶ

#### ハエたたきゲーム
- マウスを「ハエたたき」とし，オブジェクトを「ハエ」とする

##### Step1: ウィンドウを設定する
- 画面の大きさ，背景色を設定する
```python
def setup():
    size(800, 800) # ウィンドウのサイズ

def draw():
    background(255, 255, 255) # 背景⾊を決める
```

##### Step2: マウスでハエたたきを操作する
- ハエたたきをマウスの位置で操作できるようにする
  - ```mouseX```, ```mouseY```を使用する
- ハエたたきの中心位置の座標を(```mouseX```, ```mouseY```)にすればする
  - 今回は正方形オブジェクトをハエたたきとする
```python
def setup():
    size(800, 800) # ウィンドウのサイズ

def draw():
    background(255, 255, 255) # 背景⾊を決める
    tW = 40                   # ハエたたきの幅
    tH = 40                   # ハエたたきの⾼さ
    fill(198, 204, 255)       # ハエたたきの⾊
    # ハエたたきを描画する
    rect(mouseX - tW/2, mouseY - tH/2, tW, tH)
```

##### Step3: ハエを動かす
- ハエの位置，速度をグローバル変数として宣言し，```draw```で更新する
    - 速度は1フレームで動くピクセル量となる
- x方向とy方向の変化量を指定することで，平面を1方向に
移動することができる
    - xとyの変化量が同じ場合，45度の方向で進む

```python
fX = 50 # ハエのx座標
fY = 50 # ハエのy座標
fVx = 9 # ハエのx⽅向に対するの更新量
fVy = 2 # ハエのy⽅向に対するの更新量

def setup():
    size(800, 800) # ウィンドウのサイズ

def draw():
    global fX, fY, fVx, fVy   # グローバル変数を変更する
    background(255, 255, 255) # 背景⾊を決める
    tW = 40                   # ハエたたきの幅
    tH = 40                   # ハエたたきの⾼さ
    fill(198, 204, 255)       # ハエたたきの⾊
    # ハエたたきを描画する
    rect(mouseX - tW/2, mouseY - tH/2, tW, tH)

    fill(0, 0, 0) # ハエの⾊
    ellipse(fX, fY, 10, 10) # ハエを描画する
    fX += fVx # ハエのx座標を更新する
    fY += fVy # ハエのy座標を更新する
```

##### Step4: ハエを壁で反射させる
- 上端，下端，左端，右端にハエが衝突した場合，ハエが反射するようにする
    -「衝突した場合」と「ハエを反射する」をプログラムで表現する
- 「衝突した場合」のプログラム表現
  - 上端に衝突する: ```ハエのy座標 < 0```
  - 下端に衝突する: ```ハエのy座標 > ウィンドウ高さ```
  - 左端に衝突する: ```ハエのx座標 < 0```
  - 右端に衝突する: ```ハエのx座標 > ウィンドウ幅```

- 「ハエを反射する」のプログラム表現
    - 上端に衝突した場合
      - x方向の速度は変化せず，y方向の速度は逆になる
    - 下端に衝突した場合
      - x方向の速度は変化せず，y方向の速度は逆になる
    - 左端に衝突した場合
      - x方向の速度は逆になり，y方向の速度は変化しない
    - 右端に衝突した場合
      - x方向の速度は逆になり，y方向の速度は変化しない

- まとめると
  - 上端・下端に衝突した場合
（ハエのy座標が0より小さい場合，または，
ウィンドウ高さより大きい場合）
    - x方向の速度は変化せず，y方向の速度は逆になる
  - 左端・右端に衝突した場合
（ハエのx座標が0より小さい場合，または，ウィンドウ幅より大きい場合）
    - x方向の速度は逆になり，y方向の速度は変化しない

##### Step5: ハエたたきとハエの衝突判定
-  ハエと壁との衝突判定を参考にして，ハエたたきとハエの衝突判定を行う
   - マウスをクリックした状態で，ハエたたき（四角形）の内部にハエが存在するかどうかを条件とすれば良い
- ハエ叩きの左端と上端の座標を求めるとプログラムしやすい
  - ハエ叩きの幅と高さから，ハエ叩きの右端と下端の座標を求めることができる

- 衝突したと判断した場合，ハエの位置，速度をランダムな値にしてハエの設定を変更すれば，ゲームとして機能する
  - ```random(n)``` を使用する
    - 0以上n未満の値を求める

```python
fX = 50 # ハエのx座標
fY = 50 # ハエのy座標
fVx = 9 # ハエのx⽅向に対するの更新量
fVy = 2 # ハエのy⽅向に対するの更新量

def setup():
    size(800, 800) # ウィンドウのサイズ

def draw():
    global fX, fY, fVx, fVy   # グローバル変数を変更する
    background(255, 255, 255) # 背景⾊を決める
    tW = 40                   # ハエたたきの幅
    tH = 40                   # ハエたたきの⾼さ
    fill(198, 204, 255)       # ハエたたきの⾊
    # ハエたたきを描画する
    rect(mouseX - tW/2, mouseY - tH/2, tW, tH)

    fill(0, 0, 0) # ハエの⾊
    ellipse(fX, fY, 10, 10) # ハエを描画する
    fX += fVx # ハエのx座標を更新する
    fY += fVy # ハエのy座標を更新する

    if fY < 0 or fY > height: # 上下端衝突
        fVy *= -1
    if fX < 0 or fX > width: # 左右端衝突
        fVx *= -1
    sL = mouseX - tW / 2 # ハエたたきの左端座標
    sR = mouseX + tW / 2 # ハエたたきの右端座標
    sT = mouseY - tH / 2 # ハエたたきの上端座標
    sB = mouseY + tH / 2 # ハエたたきの下端座標

    # ハエたたきとハエの衝突（衝突後，ハエの位置と速度を変更する）
    if mousePressed and sL <= fX and sR >= fX and sT <= fY and sB >= fY:
        fX = int(random(width + 1))
        fY = int(random(height + 1))
        fVx = int(random(10)) + 1
        fVy = int(random(10)) + 1
```

##### Step6: 文字列によるインタラクション
- 画面に文字列を出力させ，ゲームの見栄えを良くする
  - ハエたたきとハエが衝突した回数を表示する
    - 衝突した回数を保存する変数はグローバル変数とする
- 以下を使用する
  - ```textSize(size)```: 文字の大きさを```size```にする
  - ```text(data, x, y)```: 文字列```data```を座標```(x, y)```に出力する

```python
fX = 50   # ハエのx座標
fY = 50   # ハエのy座標
fVx = 9   # ハエのx⽅向に対するの更新量
fVy = 2   # ハエのy⽅向に対するの更新量
count = 0 # 衝突回数

def setup():
    size(800, 800) # ウィンドウのサイズ

def draw():
    global fX, fY, fVx, fVy, count # グローバル変数を変更する
    background(255, 255, 255)      # 背景⾊を決める
    tW = 40                        # ハエたたきの幅
    tH = 40                        # ハエたたきの⾼さ
    fill(198, 204, 255)            # ハエたたきの⾊
    # ハエ叩きを描画する
    rect(mouseX - tW/2, mouseY - tH/2, tW, tH)

    fill(0, 0, 0) # ハエの⾊
    ellipse(fX, fY, 10, 10) # ハエを描画する
    fX += fVx # ハエのx座標を更新する
    fY += fVy # ハエのy座標を更新する

    if fY < 0 or fY > height: # 上下端衝突
        fVy *= -1
    if fX < 0 or fX > width: # 左右端衝突
        fVx *= -1
    sL = mouseX - tW / 2 # ハエたたきの左端座標
    sR = mouseX + tW / 2 # ハエたたきの右端座標
    sT = mouseY - tH / 2 # ハエたたきの上端座標
    sB = mouseY + tH / 2 # ハエたたきの下端座標

    # ハエたたきとハエの衝突（衝突後，ハエの位置と速度を変更する）
    if mousePressed and sL <= fX and sR >= fX and sT <= fY and sB >= fY:
        fX = int(random(width + 1))
        fY = int(random(height + 1))
        fVx = int(random(10)) + 1
        fVy = int(random(10)) + 1
        count += 1 # 衝突数を増やす

    # 衝突数を表⽰する
    textSize(16)
    text(str(count), 20, 20) # ⽂字列にキャストする
```


##### Step7: 魔改造
- これまでのプログラムを参考にして，ゲームを魔改造する
- 以下，魔改造の例
  - ハエを一定数倒せば，ゲームクリアにする
  - ハエの数を増やす
  - ハエの移動スピードを変化させる
  - ハエたたきの進入禁止領域を定義し，ハエたたきがそこに触れるとゲームオーバーにする
- 発想次第でいくらでもゲームを魔改造できます
  - 発想力向上，プログラミング向上につながる

#### 内サイクロイド（ハイポサイクロイド）
  - 定円に内接しながら円が滑らずに回転するときの円周上の定点の軌跡をいう

- 以下の例では，定円（動かない円）の半径を240，回転しながら動く円の半径を120の内サイクロイドを考える
  - つまり，240:120の関係，2:1の関係を考える

- 定円（動かない円）の中心を( $x_{c}, y_{c}$ )，半径を $R$，回転しながら動く円の中心を( $x_{c2}, y_{c2}$ )，半径を $r$とする．

##### Step1: 定円を描く
```python
def setup():
    size(600, 600)

def draw():
    background(255, 255, 255)
    noFill()
    strokeWeight(3)
    cX = width / 2
    cY = height / 2
    R = 240

    # 定円を描く
    ellipse(cX, cY, 2 * R, 2 * R)
```

##### Step2: 内接しながら動く円を描く
-  内接しながら動く円の中心( $x_{c2}, y_{c2}$ )は以下の式で求めることができる
$$x_{c2} = (R - r) \cos{\theta} + x_{c} $$
$$y_{c2} = (R - r) \sin{\theta} + y_{c} $$

```python
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    noFill()
    strokeWeight(3)
    cX = width / 2
    cY = height / 2
    R = 240
    r = 120

    # 定円を描く
    ellipse(cX, cY, 2 * R, 2 * R)

    # 動く円の中心を求める
    cX2 = (R - r) * cos(radians(d)) + cX
    cY2 = (R - r) * sin(radians(d)) + cY
    ellipse(cX2, cY2, 2 * r, 2 * r)
    strokeWeight(10)
    point(cX2, cY2)

    d = (d + 1) % 360
```

##### Step3: 回転するときの円周上の定点を描く
- 回転するときの円周上の定点( $x_{p}, y_{p}$ )は以下の式で求めることができる
$$x_{p} = (R - r) \cos{\theta} + r \cos{(\theta - \frac{R}{r}\theta)} + x_{c}$$
$$y_{p} = (R - r) \sin{\theta} + r \sin{(\theta - \frac{R}{r}\theta)} + y_{c}$$
```python
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    noFill()
    strokeWeight(3)
    cX = width / 2
    cY = height / 2
    R = 240
    r = 120

    # 定円を描く
    stroke(0, 0, 0)
    ellipse(cX, cY, 2 * R, 2 * R)

    # 動く円の中心を求める
    cX2 = (R - r) * cos(radians(d)) + cX
    cY2 = (R - r) * sin(radians(d)) + cY
    stroke(0, 0, 255)
    ellipse(cX2, cY2, 2 * r, 2 * r)
    strokeWeight(10)
    point(cX2, cY2)

    # 回転するときの円周上の定点を描く
    pX = (R - r) * cos(radians(d)) + r * cos(radians(d) - R * radians(d) / r) + cX
    pY = (R - r) * sin(radians(d)) + r * sin(radians(d) - R * radians(d) / r) + cY
    stroke(255, 0, 0)
    point(pX, pY)

    d = (d + 1) % 360
```

- Step4: 軌跡を描く
```python
d = 0

def setup():
    size(600, 600)

def draw():
    global d
    background(255, 255, 255)
    noFill()
    strokeWeight(3)
    cX = width / 2
    cY = height / 2
    R = 240
    r = 120

    # 定円を描く
    stroke(0, 0, 0)
    ellipse(cX, cY, 2 * R, 2 * R)

    # 動く円の中心を求める
    cX2 = (R - r) * cos(radians(d)) + cX
    cY2 = (R - r) * sin(radians(d)) + cY
    stroke(0, 0, 255)
    ellipse(cX2, cY2, 2 * r, 2 * r)
    strokeWeight(10)
    point(cX2, cY2)

    for t in range(d+1):
        # 回転するときの円周上の定点を描く
        pX = (R - r) * cos(radians(t)) + r * cos(radians(t) - R * radians(t) / r) + cX
        pY = (R - r) * sin(radians(t)) + r * sin(radians(t) - R * radians(t) / r) + cY
        if t == d:
            strokeWeight(35)
        stroke(255, 0, 0)
        point(pX, pY)
    d = (d + 1) % 360
```

### 練習問題
- サンプルプログラムを利用して，各問を満たすプログラムを作成しなさい
1. 内サイクロイドのプログラムを利用して，デルトイドの軌跡を描いてください
   - 定円（動かない円）の半径と回転しながら動く円の半径の比を3:1にすれば良い

2. 内サイクロイドのプログラムを利用して，アステロイドの軌跡を描いてください
   - 定円（動かない円）の半径と回転しながら動く円の半径の比を4:1にすれば良い

- 定円に外接しながら円が滑らずに回転するときの円周上の定点の軌跡を外サイクロイド（エピサイクロイド）とよぶ
3. 外接しながら動く円を描くアニメーションを作成してください
   - 定円（動かない円）の中心を( $x_{c}, y_{c}$ )，半径を $R$，回転しながら動く円の中心を( $x_{c2}, y_{c2}$ )，半径を $r$とする．
    $$x_{c2} = (R + r) \cos{\theta} + x_{c}$$
    $$y_{c2} = (R + r) \sin{\theta} + y_{c}$$

4. このときの回転するときの円周上の定点を描くアニメーションを作成してください
- 回転するときの円周上の定点( $x_{p}, y_{p}$ )は以下の式で求めることができる
$$x_{p} = (R + r) \cos{\theta} - r \cos{(\theta + \frac{R}{r}\theta)} + x_{c}$$
$$y_{p} = (R + r) \sin{\theta} - r \sin{(\theta + \frac{R}{r}\theta)} + y_{c}$$
5. このときのアニメーション（外サイクロイドの軌跡）を作成してください
