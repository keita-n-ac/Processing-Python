# 第8回目
## 繰り返し処理（応用編）

### 構造化プログラミング
- 1960年代後半にエドガー・ダイクストラによって提唱
  - 『1つの入口と1つの出口を持つプログラムは，順次・選択・反復の3つの論理構造によって記述できる』
    - 順次: 上から下へ順番にプログラムが実行される
    - 選択: 条件Aを満たしているなら，処理aを行う（条件分岐）
      - ```if文```，```elif文```，```else文```
    - 反復: 条件Bを満たしている間ずっと，処理bを繰り返す（繰り返し処理）
      - ```while文```，```for文```
  - 繰り返し文の中に選択処理を書くこともでき，選択処理の中に繰り返し文を書くことができる
```python
size(600, 600)
background(255, 255, 255)
noStroke()

for i in range(10):
    if i % 2 == 0:
        fill(0, 0, 255)
        rect(i*60, 0, 60, height)
```

```python
def setup():
    size(600, 600)
    noStroke()

def draw():
    noStroke()
    background(255, 255, 255)
    if mouseX <= width/2:
        for i in range(10):
            if i % 2 == 0:
                fill(0, 0, 255)
                rect(i*60, 0, 60, height)
    else:
        for i in range(10):
            if i % 2 == 0:
                fill(255, 0, 0)
                rect(0, i*60, width, 60)
    strokeWeight(10)
    stroke(0, 0, 0)
    line(width/2, 0, width/2, height)
```

### 2重ループ
- 繰り返し処理の中に，繰り返し処理を記述することで，より複雑なプログラムを書くことが出来る
- 2重ループの場合，内側にある繰り返し処理を，外側にあるループで設定した繰り返しで実行する

```python
size(600, 600)
background(255, 255, 255)
strokeWeight(4)

count = 3
for i in range(count):
    for j in range(count):
        rect(j * width/count, i * height/count, width/count, height/count)
```

```python
size(600, 600)
colorMode(HSB, 360, 100, 100)
background(0, 0, 100)
strokeWeight(3)

count = 30
for i in range(count):
    for j in range(count):
        fill(j*170/count + i*170/count, 100, 100)
        rect(j * width/count, i * height/count, width/count, height/count)
```


### 2重ループの応用1
- 繰り返し回数を変数として繰り返し処理を行うことで，さらに複雑な処理を行うことができる

```python
size(600, 600)
strokeWeight(4)
count = 10
background(255, 255, 255)
for i in range(count):
    for j in range(i+1):
        rect(j * width/count, i * height/count, width/count, height/count)
```

```python
size(600, 600)
strokeWeight(4)
count = 10
background(255, 255, 255)
for i in range(count):
    for j in range(count-1-i, -1, -1):
        rect(j * width/count, i * height/count, width/count, height/count)
```
### 2重ループの応用2
- 2重ループの中に選択処理を書くことで，より複雑な処理を行うことができる
```python
size(600, 600)
noStroke()
count = 10
background(255, 255, 255)
for i in range(count):
    for j in range(count):
        if j % 2 == 0:
            fill(0, 0, 0)
        else:
            fill(255, 255, 255)
        rect(j*width/count, i*height/count, width/count, height/count)
```

```python
size(600, 600)
noStroke()
count = 10
background(255, 255, 255)
for i in range(count):
    for j in range(count):
        if (i + j) % 2 == 0:
            fill(0, 0, 0)
        else:
            fill(255, 255, 255)
        rect(j*width/count, i*height/count, width/count, height/count)
```

```python
size(600, 600)
noStroke()
colorMode(HSB, 360, 100, 100)
count = 30
background(0, 0, 100)
for i in range(count):
    for j in range(count):
        a = (i + j) % count
        fill(a * 360 / count, 100, 100)
        rect(j*width/count, i*height/count, width/count, height/count)
```

```python
k = 0
def setup():
    size(600, 600)
    background(255, 255, 255)
    frameRate(3) # 3fpsにする
    noStroke()

def draw():
    global k
    for i in range(10):
        for j in range(10):
            if (i + j + k) % 2 == 1:
                fill(255, 255, 255)
            else:
                fill(0, 0, 0)
            rect(j*60, i*60, 60, 60)
    k = k + 1
```
- ```frameRate(整数)```:  指定したfpsにする

### 練習問題
- サンプルプログラムを参考に，大きさ600, 600の画面に対して，以下のプログラムを書きなさい
  1. 縦横で10分割行い<br>
        A. 行ごとに同じ色を塗りつぶす（全行違う色にすること）<br>
        B. 列ごとに同じ色を塗りつぶす（全列違う色にすること）
  2. 2重ループを使用して階段を作成しなさい（ただし以下の条件を満たすこと）<br>
    A. 全行違う色にする<br>
    B. 全列違う色にする
  3. 3fpsで縦縞模様・横縞模様を切り替えるアニメーションを作成しなさい
