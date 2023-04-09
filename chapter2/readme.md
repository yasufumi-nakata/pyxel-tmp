# Chapter 2: 基本的なプログラム構造

## 概要

このチャプターでは、Pyxelでゲームを開発するための基本的なプログラム構造について学びます。Pyxelアプリケーションの作成方法、init、update、draw関数の説明を行います。

## 目次
1. Pyxelアプリケーションの作成方法
2. init関数の説明
3. update関数の説明
4. draw関数の説明

### 1. Pyxelアプリケーションの作成方法

Pyxelでゲームを開発するには、まずpyxe.Appクラスを継承したクラスを作成します。以下は、最もシンプルなPyxelアプリケーションの例です。

```python
import pyxel

class MyApp(pyxel.App):
    def __init__(self):
        super().__init__(width=128, height=128, caption="MyApp", fps=60)
        pyxel.run(self.update, self.draw)

if __name__ == "__main__":
    MyApp()
```

### 2. init関数の説明

init関数は、Pyxelアプリケーションの初期化処理を行う関数です。例えば、画面サイズやFPSの設定、画像や音楽のロードなどを行います。以下の例では、画面サイズを128x128ピクセルに設定し、ウィンドウのキャプションを"MyApp"に設定し、FPSを60に設定しています。

```python
def __init__(self):
    super().__init__(width=128, height=128, caption="MyApp", fps=60)
```

### 3. update関数の説明

update関数は、ゲームの状態を更新するための関数です。例えば、キャラクターや敵の移動、衝突判定、スコアの計算、キーボード入力の処理などを行います。update関数は、FPSに応じて繰り返し呼び出されます。以下の例では、qキーが押されたらアプリケーションを終了する処理を行っています。

```python
def update(self):
    if pyxel.btnp(pyxel.KEY_Q):
        pyxel.quit()
```

### 4. draw関数の説明

draw関数は、ゲーム画面を描画するための関数です。例えば、キャラクターや敵、背景、スコアなどの描画を行います。draw関数は、update関数の後に繰り返し呼び出されます。以下の例では、画面をクリアし、(0, 0)の座標に"Hello, Pyxel!"というテキストを描画しています。

```python
def draw(self):
    pyxel.cls(0)
    pyxel.text(0, 0, "Hello, Pyxel!", pyxel.COLOR_WHITE)
```

## まとめ

このチャプターでは、Pyxelでゲームを開発するための基本的なプログラム構造について学びました。次のチャプターでは、グラフィックの描画方法について学びます。
