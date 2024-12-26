# 第8回目 練習問題 解答例
## 練習問題
- 1-A: 縦横で10分割行い，行ごとに同じ色を塗りつぶす（全行違う色にすること）
```python
size(600, 600)
colorMode(HSB, 360, 100, 100)

for i in range(10):
    fill(i * 24, 100, 100)
    for j in range(10):
        rect(j*60, i*60, 60, 60)
```
- 1-B: 縦横で10分割行い，列ごとに同じ色を塗りつぶす（全列違う色にすること）
```python
size(600, 600)
colorMode(HSB, 360, 100, 100)

for i in range(10):
    for j in range(10):
        fill(j * 24, 100, 100)
        rect(j*60, i*60, 60, 60)
```
- 2-A: 2重ループを使用して階段を作成しなさい（全行違う色にする）
```python
size(600, 600)
colorMode(HSB, 360, 100, 100)
background(0, 0, 100)
for i in range(10):
    fill(i * 24, 100, 100)
    for j in range(i+1):
        rect(j*60, i*60, 60, 60)
```
- 2-B: 2重ループを使用して階段を作成しなさい（全列違う色にする）
```python
size(600, 600)
colorMode(HSB, 360, 100, 100)
background(0, 0, 100)
for i in range(10):
    for j in range(i+1):
        fill(j * 24, 100, 100)
        rect(j*60, i*60, 60, 60)
```
3. 3fpsで縦縞模様・横縞模様を切り替えるアニメーションを作成しなさい
```python
k = 0
def setup():
    size(600, 600)
    background(255, 255, 255)
    frameRate(3) # 3fpsにする
    noStroke()

def draw():
    global k
    noStroke()
    background(255, 255, 255)
    if k % 2 == 0:
        for i in range(10):
            if i % 2 == 0:
                fill(0, 0, 255)
                rect(i*60, 0, 60, height)
    else:
        for i in range(10):
            if i % 2 == 0:
                fill(255, 0, 0)
                rect(0, i*60, width, 60)
    k = k + 1
```