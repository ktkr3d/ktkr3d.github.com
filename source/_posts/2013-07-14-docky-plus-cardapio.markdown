---
layout: post
title: "Docky + Cardapio"
date: 2013-07-14 11:11
comments: true
categories: Linux
---
<a href="/images/docky_cardapio.png">{% img /images/docky_cardapio_tn.png %}</a>

Ubuntu 13.10 + GNOME Shell 3.9.4 上で、Docky に移行して困ったことは、以下でした。

1. 電源ボタンが無いこと
2. アプリケーションメニューがないこと

Docky とCardapio の設定で上記を動くようにしてみました。

<!-- more --> 

#### 電源ボタンの設定
一番右の「画面のロック」アイコンを右クリックすることで、「画面のロック」、「ログアウト」、「サスペンド」、「再起動」、「シャットダウン」のようなサブメニューが表示されます。
「画面のロック」のアイコン上でマウスのホイールボタンで上下にホイールすると、デフォルトの動作を指定できます。
ボタン押下後に再起動かシャットダウンかを選択させる形式がよかったのですが、とりあえずこれで良しとしましょう。

#### Cardapio の設定
Cardapio を使ってDocky からアプリケーションメニューを表示することにします。

{% codeblock %}
$ sudo add-apt-repository ppa:cardapio-team/unstable
$ sudo apt-get update
$ sudo apt-get install cardapio
{% endcodeblock %}

saucy 向けのCardapio が存在しなかったので、ソフトウェアソースをquantal 向けに切り替えてインストールしました。
cardapio を起動してみたところ、いくつかエラーが表示されたので、`/usr/lib/cardapio/Cardapio.py` を修正しました。

1. 以下を追加<br>
`from xdg import BaseDirectory`

2. 以下を置換<br>
`DesktopEntry.xdg_config_home` -> `BaseDirectory.xdg_config_home`

3. 以下を置換<br>
`DesktopEntry.xdg_cache_home` -> `BaseDirectory.xdg_cache_home`

#### Docky へCardapio を登録

cardapio-helper というDocky のヘルパーを使うと、Docky アイコンクリックで、Cardapio が起動されるはずなのですが、うまく動作しませんでした。
仕方がないので、`/usr/share/applications/cardapio.desktop` をDocky にドラッグ&ドロップして、メニューアイコンを登録しました。
