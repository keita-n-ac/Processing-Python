# 第2回目
## Pythonプログラミング
### 標準出力

- 数値，文字列，計算結果を標準出力（画面出力）するには，```print()```を使用する．
```python
print(1 + 3)
print(2 - 4)
print(987)
print(2 ** 6)
```
- ```**```は，累乗を表す

### 変数
- コンピュータのメモリ上の領域に名前を付けて値を格納する仕組み
  - この仕組みを利用して，値を一時保存できる
  - 数値や文字列に付ける名札のようなもの
  - ```変数 = 初期値```で変数の初期化を行う
    - ```=``` を代入演算子とよぶ（ ```=``` を等号の意味で使用しない）
  - ```print(変数)``` とすると，その変数に格納されている値を，表示することができる
```python
size(800, 600)
print(width)
print(height)
```
 - ```print(変数1, 変数2, ･･･, 変数n)``` とすると，```変数1 変数2 ･･･ 変数n```と表示する
 - 変数は自由に付けられるが，以下のルールがある
   - 英数字，アンダースコア ```_``` のみ使用可能
   - 数字から始まらないこと（英字，アンダースコアはOK）
     - 例: 変数```ABC```と変数```abc```は別の変数として扱われる
   - 予約語（Pythonの文法で定義されている名前）は使用不可
     - ```if```，```for```，```and``` など
   - Processingの特別語は使用できるが，別の値の代入は不可
     - ```width```，```height``` など

```python
a = 10   # 変数aに10を代⼊
print(a) # 変数aの中身を表⽰
# aという名前がついた箱の中に
# 整数の10というデータが入っているイメージをしてプログラムを行う
# この考え方がプログラミングの基本
```

```python
a = 10   # 変数aに10を代⼊
print(a) # 変数aの値を表⽰


b = 5    # 変数bに5を代⼊
print(b) # 変数bの値を表⽰

c = a + b # 変数cに変数aの値と変数bの値の和を代⼊
print(c)  # 変数cの値を表⽰

print(a, b) # 変数aとbの値を表⽰
```

### 変数の値の更新
- ```変数 = 同じ変数 演算⼦ 値``` で変数の値を更新できる
  - プログラミング特有の書き方
- 例1: ```x = x + 4``` (『変数xに4を加えた値』を『変数xに代入する』)
- 例2: ```y = y - 5``` (『変数yに5を引いた値』を『変数yに代入する』)
```python
a = 11     # 変数aに11を代⼊
print(a)   # 変数aの値を表⽰

a = a * 11 # 変数aの値を更新する（11倍した値にする）
print(a)   # 更新した変数aの値を表示
```
### 複合代入演算子
- 変数に演算した結果を同じ変数に代入する演算子
  - 変数の値を更新する場合に使われることが多い

| 演算子 | 使用例 | 意味 | 
|-----|-----|------------| 
| ```+=```  | ```a += 1``` | ```a = a + 1```  | 
| ```-=```  | ```a -= 2``` | ```a = a - 2```  | 
| ```*=```  | ```a *= 3``` | ```a = a * 3```  | 
| ```/=```  | ```a /= 4``` | ```a = a / 4```  | 
| ```%=```  | ```a %= 5``` | ```a = a % 5```  | 
| ```**=``` | ```a **= 6``` | ```a = a ** 6``` | 

```python
colorB = 255
size(600, 600)
noStroke()
fill(0, 0, colorB)
rect(0, 0, width/2, height)
colorB /= 2
fill(0, 0, colorB)
rect(width/2, 0, width/2, height)
```

```python
size(600, 600)
background(0, 0, 0)
x = 0
y = height/2
r = 200
noStroke()
fill(0, 255, 0)
ellipse(x, y, r, r)
x += 200
ellipse(x, y, r, r)
x += 200
ellipse(x, y, r, r)
x += 200
ellipse(x, y, r, r)
```

```python
size(500, 300)
background(255, 255, 255)
centX = width/2
centY = height/2
stroke(130, 0, 0)
strokeWeight(2)
ellipse(centX, centY, 40, 40)
line(centX-50, centY-50, centX+50, centY+50)
line(centX+50, centY-50, centX-50, centY+50)
```

### HSBによる色指定
- ```colorMode(HSB, 360, 100, 100)```と書くことで，HSB形式で色を指定することができる（書かない場合，RGB形式で色を指定する）
  - **H**(色相: 色味の違い)を360段階
    - 0: 赤
    - 60: 黄
    - 120: 緑
    - 180: シアン
    - 240: 青
    - 300: マゼンタ
  - **S**(彩度: 色の鮮やかさ)を100段階
    - 0: 白（濁り），100: 鮮やか 
  - **B**(輝度: 色の明るさ)を100段階
    - 0: 暗い，100: 明るい

```python
size(600, 600)
colorMode(HSB, 360, 100, 100)
# 以下，HSB形式で色を指定
background(100, 0, 100)
noStroke()
y = height/2
h = 0
r = 100
fill(0, 100, 100)
ellipse(100, y, r, r)
fill(120, 100, 100)
ellipse(300, y, r, r)
fill(240, 100, 100)
ellipse(500, y, r, r)
```

```python
# 色相と明度を固定，彩度だけ変化
colorMode(HSB, 360, 100, 100)
noStroke()
fill(180, 0, 80)
rect(0, 0, 25, 100)
fill(180, 25, 80)
rect(25, 0, 25, 100)
fill(180, 50, 80)
rect(50, 0, 25, 100)
fill(180, 75, 80)
rect(75, 0, 25, 100)
```

```python
# 色相と彩度を固定，明度だけ変化
colorMode(HSB, 360, 100, 100)
noStroke()
fill(180, 42, 0)
rect(0, 0, 25, 100)
fill(180, 42, 25)
rect(25, 0, 25, 100)
fill(180, 42, 50)
rect(50, 0, 25, 100)
fill(180, 42, 75)
rect(75, 0, 25, 100)
```

```python
# HSBモードで赤色から緑色に変化
colorMode(HSB, 360, 100, 100)
noStroke()
fill(0, 70, 80)
rect(0, 0, 20, 100)
fill(25, 70, 80)
rect(20, 0, 20, 100)
fill(50, 70, 80)
rect(40, 0, 20, 100)
fill(75, 70, 80)
rect(60, 0, 20, 100)
fill(100, 70, 80)
rect(80, 0, 20, 100)
```

## 練習問題
- 大きさ600, 600の画面に対して，以下のプログラムを書きなさい（色の指定は，HSB形式で行うこと）
  1. 赤い円を5個横に並べること（画面中央に1行に並べること）
  2. 青い正方形を5個縦に並べること（画面中央に1列に並べること）
  3. 緑色の正方形を5個対角線上（左上から右下）に並べること
  4. 黒色の正方形を5個対角線上（右上から左下）に並べること
- 以下のプログラムを参考にして，×マークから，+マークに変更しなさい（色の指定は，RGB形式で行うこと）
```python
size(500, 300)
background(255, 255, 255)
centX = width/2
centY = height/2
stroke(130, 0, 0)
strokeWeight(2)
ellipse(centX, centY, 40, 40)
line(centX-50, centY-50, centX+50, centY+50)
line(centX+50, centY-50, centX-50, centY+50)
```
