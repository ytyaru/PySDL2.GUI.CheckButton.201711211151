# このソフトウェアについて

PySDL2でButtonを表示する。

![画像](https://cdn-ak.f.st-hatena.com/images/fotolife/y/ytyaru/20171121/20171121105606.png)

* `sdl2.ext.UIFactory(sdl2.ext.SpriteFactory(sdl2.ext.SOFTWARE)).from_color(sdl2.ext.BUTTON, color=sdl2.ext.Color(0,0,0), size=(100,50))`

# 問題

* マウスポインタがUIの表示領域から出た時のイベントハンドラが無い
    * 実装方法に統一性をもたせることができない
        * 中途半端なイベント駆動型プログラミングになってしまう

C#などの一般的な言語では、Enter, Leave, のようなイベントハンドラが用意されているのに……。

## Buttonの全イベントハンドラ

* motion
* pressed
* released
* click

# 対策

Leave時のみ、メインループ内でif文による実装をする。

```python
while running:
    events = sdl2.ext.get_events()
    for event in events:
        if button.state != sdl2.ext.HOVERED:
            sdl2.ext.fill(button.surface, GREY)
```

# 開発環境

* Linux Mint 17.3 MATE 32bit
* [SDL2](http://ytyaru.hatenablog.com/entry/2018/12/09/000000) 2.0.2
* [pyenv](https://github.com/pylangstudy/201705/blob/master/27/Python%E5%AD%A6%E7%BF%92%E7%92%B0%E5%A2%83%E3%82%92%E7%94%A8%E6%84%8F%E3%81%99%E3%82%8B.md) 1.0.10
    * Python 3.6.1
        * [PySDL2](http://ytyaru.hatenablog.com/entry/2018/12/10/000000) 0.9.6
        
# 参考

* [http://pysdl2.readthedocs.io/en/rel_0_9_4/modules/sdl2ext_gui.html]
    * [https://translate.google.com/translate?sl=en&tl=ja&js=y&prev=_t&hl=ja&ie=UTF-8&u=http%3A%2F%2Fpysdl2.readthedocs.io%2Fen%2Frel_0_9_4%2Fmodules%2Fsdl2ext_gui.html&edit-text=&act=url]
    
# 実行

```sh
$ python 0.py
$ python 1.py
$ python 2.py
$ python 3.py
```

# ライセンス

このソフトウェアはCC0ライセンスである。

[![CC0](http://i.creativecommons.org/p/zero/1.0/88x31.png "CC0")](http://creativecommons.org/publicdomain/zero/1.0/deed.ja)

利用ライブラリのライセンスは以下。

Library|License|Copyright
-------|-------|---------
[SDL2](https://www.libsdl.org/license.php)|zlib|[github](https://github.com/letoram/SDL2/blob/master/debian/copyright)
[PySDL2](https://pysdl2.readthedocs.io/en/rel_0_9_6/)|[CC0](http://pysdl2.readthedocs.io/en/rel_0_9_4/copying.html)|[Copyright (C) 2012-2014 Marcus von Appen  marcus@sysfault.org](http://pysdl2.readthedocs.io/en/rel_0_9_4/copying.html)

