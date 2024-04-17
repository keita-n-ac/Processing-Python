# 第2回目 練習問題 解答例
## 練習問題
1. 大きさ600, 600の画面に対して，以下のプログラムを書きなさい（色の指定は，HSB形式で行うこと）
   1. 赤い円を5個横に並べること（画面中央に1行に並べること）
        ```python
        size(600, 600)
        colorMode(HSB, 360, 100, 100)
        background(0, 0, 100)
        size = width/5
        startX = size/2
        startY = height/2
        fill(0, 100, 100)
        strokeWeight(4)
        ellipse(startX, startY, size, size)
        ellipse(startX+size, startY, size, size)
        ellipse(startX+2*size, startY, size, size)
        ellipse(startX+3*size, startY, size, size)
        ellipse(startX+4*size, startY, size, size)
        ```
   2. 青い正方形を5個縦に並べること（画面中央に1列に並べること）
        ```python
        size(600, 600)
        colorMode(HSB, 360, 100, 100)
        background(0, 0, 100)
        size = width/5
        startX = width/2-size/2
        startY = 0
        fill(240, 100, 100)
        strokeWeight(4)
        rect(startX, startY, size, size)
        rect(startX, startY+size, size, size)
        rect(startX, startY+2*size, size, size)
        rect(startX, startY+3*size, size, size)
        rect(startX, startY+4*size, size, size)
        ```
    3. 緑色の正方形を5個対角線上（左上から右下）に並べること
        ```python
        size(600, 600)
        colorMode(HSB, 360, 100, 100)
        background(0, 0, 100)
        size = width/5
        startX = 0
        startY = 0
        fill(120, 100, 100)
        strokeWeight(4)
        rect(startX, startY, size, size)
        rect(startX+size, startY+size, size, size)
        rect(startX+2*size, startY+2*size, size, size)
        rect(startX+3*size, startY+3*size, size, size)
        rect(startX+4*size, startY+4*size, size, size)
        ```
    4. 黒色の正方形を5個対角線上（右上から左下）に並べること
        ```python
        size(600, 600)
        colorMode(HSB, 360, 100, 100)
        background(0, 0, 100)
        size = width/5
        startX = 4*width/5
        startY = 0
        fill(0, 0, 0)
        strokeWeight(4)
        rect(startX, startY, size, size)
        rect(startX-size, startY+size, size, size)
        rect(startX-2*size, startY+2*size, size, size)
        rect(startX-3*size, startY+3*size, size, size)
        rect(startX-4*size, startY+4*size, size, size)
        ```
2. ×マークから，+マークに変更しなさい（色の指定は，RGB形式で行うこと）
```python
size(500, 300)
background(255, 255, 255)
centX = width/2
centY = height/2
stroke(130, 0, 0)
strokeWeight(2)
ellipse(centX, centY, 40, 40)
line(centX-50, centY, centX+50, centY)
line(centX, centY-50, centX, centY+50)
```