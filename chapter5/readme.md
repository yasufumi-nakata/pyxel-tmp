# Chapter 5: キーボード入力とキャラクターの操作

このチャプターでは、キーボード入力を取得し、それを使ってキャラクターを操作する方法を学びます。具体的には、キャラクターを移動させたり、アクションを実行させたりする方法を説明します。

## 目次
1. キーボード入力の取得方法
2. キャラクターの移動
3. キャラクターのアクション実装

### 1. キーボード入力の取得方法
Pyxelでは、`pyxel.btn`関数と`pyxel.btnp`関数を使ってキーボードの入力を取得できます。`pyxel.btn`はキーが押されている間、`pyxel.btnp`はキーが押された瞬間のみTrueを返します。

```python
import pyxel

class App:
    def __init__(self):
        pyxel.init(160, 120)
        pyxel.run(self.update, self.draw)

    def update(self):
        if pyxel.btn(pyxel.KEY_W):
            print("Wキーが押されている")

        if pyxel.btnp(pyxel.KEY_S):
            print("Sキーが押された瞬間")

    def draw(self):
        pyxel.cls(0)

App()
```

### 2. キャラクターの移動
キーボード入力を使ってキャラクターの位置を更新しましょう。以下の例では、Wキーで上に、Sキーで下に、Aキーで左に、Dキーで右に移動します。

```python
import pyxel

class App:
    def __init__(self):
        pyxel.init(160, 120)
        self.x = 80
        self.y = 60
        pyxel.run(self.update, self.draw)

    def update(self):
        if pyxel.btn(pyxel.KEY_W):
            self.y -= 1
        if pyxel.btn(pyxel.KEY_S):
            self.y += 1
        if pyxel.btn(pyxel.KEY_A):
            self.x -= 1
        if pyxel.btn(pyxel.KEY_D):
            self.x += 1

    def draw(self):
        pyxel.cls(0)
        pyxel.rect(self.x, self.y, 8, 8, 9)

App()
```

### 3. キャラクターのアクション実装
キーボード入力を使ってキャラクターにアクションを実行させましょう。以下の例では、スペースキーを押すことでキャラクターがジャンプします。

```python
import pyxel

class App:
    def __init__(self):
        pyxel.init(160, 120)
        self.x = 80
        self.y = 60
        self.vy = 0
        self.is_jumping = False
        pyxel.run(self.update, self.draw)

    def update(self):
        if pyxel.btn(pyxel.KEY_W):
            self.y -= 1
        if pyxel.btn(pyxel.KEY_S):
            self.y += 1
        if pyxel.btn(pyxel.KEY_A):
            self.x -= 1
        if pyxel.btn(pyxel.KEY_D):
            self.x += 1

        if pyxel.btnp(pyxel.KEY_SPACE) and not self.is_jumping:
            self.vy = -5
            self.is_jumping = True

        self.y += self.vy
        self.vy += 0.2

        if self.y >= 60:
            self.y = 60
            self.vy = 0
            self.is_jumping = False

    def draw(self):
        pyxel.cls(0)
        pyxel.rect(self.x, self.y, 8, 8, 9)

App()
```

これで、キーボード入力によるキャラクターの操作ができるようになりました。次のチャプターでは、衝突判定の方法を学びます。
