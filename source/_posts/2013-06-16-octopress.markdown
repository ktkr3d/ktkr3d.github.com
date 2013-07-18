---
layout: post
title: "Octopress"
date: 2013-06-16 12:34
comments: true
categories: blog
---
{% img /images/octopress.png %}

http://ktkr3d.site11.com 上のWordPress からGitHub 上のOctopress にブログを移行してみました。
<!-- more -->
WordPress は便利なのですが、メモリ消費量が多くなってしまい、海外無料Webサービスでの運用が困難になってきました。（解決策はいろいろとあるとは思いますが。）

そこで、Github Pages + Octopress でブログサイトを構築してみることにしました。Markdown で記述していきますが、よく知らないので、これから覚えていくことにしましょう。

### 使い方のメモ

http://octopress.org/docs/

- 新規記事の作成

{% codeblock %}
rake new_post["title"]
{% endcodeblock %}

- 記事の編集	

./octopress/source/_posts/*.markdown を編集します。
画像はsource/images/ に格納することにします。
画像の挿入は

{% codeblock %}
{% raw %}
{% img /images/Ubuntu-GNOME-13-10.png 600 %}
{% endraw %}
{% endcodeblock %}

- 生成とデプロイ

{% codeblock %}
rake generate && rake deploy
{% endcodeblock %}
	
- 新規ページの作成	

{% codeblock %}
rake new_page[page-name]
{% endcodeblock %}

- スタイルの変更

./octopress/source/stylesheets/ にスタイルシートがあります。
スタイルシートのカスタマイズは`./octopress/saas/custom/`にあるファイルを編集します。

OctoPress のテーマは画面幅が狭い場合にサイドバーが下部に移動するようになっているようですので、少し調整が必要そうです。
