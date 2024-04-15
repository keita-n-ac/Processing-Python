# 第1回目 練習問題 解答例

## 練習問題
1. 日本の国旗を描いてください（幅 : 高さ = 3 : 2）
```python
size(900, 600)
background(255, 255, 255)
noStroke()
fill(255, 0, 0)
ellipse(width/2, height/2, 300, 300)
```
2. フランスの国旗を描いてください（幅 : 高さ = 3 : 2）
```python
size(900, 600)
background(255, 255, 255)
noStroke()
fill(0, 0, 255)
rect(0, 0, width/3, height)
fill(255, 0, 0)
rect(2*width/3, 0, width/3, height)
```
3. ドイツの国旗を描いてください（幅 : 高さ = 3 : 2）
```python
size(900, 600)
background(0, 0, 0)
noStroke()
fill(255, 0, 0)
rect(0, height/3, width, height/3)
fill(255, 255, 0)
rect(0, 2*height/3, width, height/3)
```
4. スイスの国旗を描いてください（幅 : 高さ = 1 : 1）
```python
size(600, 600)
background(255, 0, 0)
noStroke()
fill(255, 255, 255)
rect(2*width/5, height/5, width/5, 3*height/5)
rect(width/5, 2*height/5, 3*width/5, height/5)
```