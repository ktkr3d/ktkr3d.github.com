---
layout: post
title: "Zenity OctoPress Helper"
date: 2013-07-15 13:26
comments: true
categories: blog
---
<a href="/images/zenity_octopress_menu.png">{% img /images/zenity_octopress_menu.png %}</a>

OctoPress のフロントエンドをZenity で作ってみました。
Web ベースのUI を作っている方もいるようですが、とりあえずこれでもお手軽になりました。

<!-- more -->

#### zenity スクリプト

<a href="/images/zenity_octopress_new_post.png">{% img /images/zenity_octopress_new_post.png %}</a><br>
<a href="/images/zenity_octopress_deploy.png">{% img /images/zenity_octopress_deploy.png %}</a>

Zenity のリストボックス、テキスト入力、プログレスバー等を利用して、フロントエンドを作成します。

{% codeblock octopress_helper.sh %}
{% raw %}
#!/bin/bash

OCTOPRESS_DIR=/mnt/common/github/octopress

PATH=$PATH:$HOME/bin:$HOME/.rvm/bin # Add RVM to PATH for scripting
source $HOME/.rvm/scripts/rvm
cd $OCTOPRESS_DIR

while :
do
	pick=$(zenity --list --title "OctoPress Helper" --text "Select Action." --radiolist --column Pick --column dummy --column Action --hide-column 2 true 0 "New Post" false 1 "New Page" false 2 "Generate" false 3 "Deploy" false 4 "Open Posts Folder");
	case $pick in
		0)
			article_title=$(zenity --entry --title="New Post" --text="Enter Title." )
			if [ $article_title > 0 ] ; then
				rake new_post["$article_title"] >(zenity --progress --title="New Post" --pulsate --auto-close --auto-kill)
			fi
			;;
		1) 
			page_title=$(zenity --entry --title="New Page" --text="Enter Title." )
			if [ $page_title > 0 ] ; then
				rake new_page["$page_title"] >(zenity --progress --title="New Page" --pulsate --auto-close --auto-kill)
			fi
			;;
		2)
			rake generate >(zenity --progress --title="Generate" --pulsate --auto-close --auto-kill)
			;;
		3)
			rake deploy >(zenity --progress --title="Deploy" --pulsate --auto-close --auto-kill)
			;;
		4)
			nautilus $OCTOPRESS_DIR/source/_posts/
			;;
		*)
			break
			;;
	esac
done
{% endraw %}
{% endcodeblock %}

#### 起動用ショートカットアイコン

起動用のショートカットファイル`octopress_helper.desktop`を作成してドックにドラッグ&ドロップします。
端末を非表示にする場合は`Terminal=false`とします。

{% codeblock %}
[Desktop Entry]
Encoding=UTF-8
Name=OctoPress Helper
Exec=/mnt/common/home/Script/octopress_helper.sh
Icon=/usr/share/pixmaps/octopress.png
Terminal=true
Type=Application
Categories=Application;
StartupNotify=false
{% endcodeblock %}

#### プレビュー

私は `rake preview` をログイン時に常駐させて、ブラウザから `http://localhost:4000/` にアクセスしてレイアウト結果を確認しています。フォルダ内の変更が監視されるので、多少の負荷はあるかもしれません。
