# Chapter 8: ゲームのステージとスクロール

このチャプターでは、ゲームのステージを作成し、スクリーンのスクロールを実装する方法を学びます。具体的には、タイルマップを作成し、カメラ制御とスクロールを実装します。

## 目次
1. タイルマップの作成と描画
2. カメラ制御
3. スクロール実装

### 1. タイルマップの作成と描画
タイルマップを使ってゲームのステージを作成しましょう。Pyxelエディタでタイルを作成し、それをタイルマップに配置します。以下の例では、タイルマップを描画する方法を示しています。

```python
import pyxel

class App:
    def __init__(self):
        pyxel.init(160, 120)
        pyxel.load("my_resource.pyxres")
        pyxel.run(self.update, self.draw)

    def update(self):
        pass

    def draw(self):
        pyxel.cls(0)
        pyxel.bltm(0, 0, 0, 0, 0, 32, 32)

App()
```

### 2. カメラ制御
カメラ制御を実装することで、キャラクターが移動すると画面が追従するようになります。以下の例では、カメラの座標を更新し、それに応じてタイルマップを描画します。

```python
import pyxel

class App:
    def __init__(self):
        pyxel.init(160, 120)
        pyxel.load("my_resource.pyxres")
        self.x = 80
        self.y = 60
        self.camera_x = 0
        self.camera_y = 0
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

        self.camera_x = self.x - 80
        self.camera_y = self.y - 60

    def draw(self):
        pyxel.cls(0)
        pyxel.bltm(-self.camera_x, -self.camera_y, 0, 0, 0, 32, 32)
        pyxel.rect(self.x - self.camera_x, self.y - self.camera_y, 8, 8, 9)

App()
```

### 3. スクロール実装
スクロールを実装することで、ステージ全体を表示できるようになります。以下の例では、スクロールの範囲を設定し、カメラ座標を更新します。

```python
import pyxel

class App:
    def __init__(self):
        pyxel.init(160, 120)
        pyxel.load("my_resource.pyxres")
        self.x = 80
        self.y = 60
        self.camera_x = 0
        self.camera_y = 0
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

        self.camera_x = min(max(self.x - 80, 0), 32 * 8 - 160)
        self.camera_y = min(max(self.y - 60, 0), 32 * 8 - 120)

    def draw(self):
        pyxel.cls(0)
        pyxel.bltm(-self.camera_x, -self.camera_y, 0, 0, 0, 32, 32)
        pyxel.rect(self.x - self.camera_x, self.y - self.camera_y, 8, 8, 9)

App()
```

これで、ゲームのステージとスクロールが実装できました。次のチャプターでは、ゲームの完成とデプロイを行います。
