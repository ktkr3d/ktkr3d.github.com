---
layout: post
title: "GNOME Shell 3.9.4"
date: 2013-07-13 09:36
comments: true
categories: Linux
---

<a href="/images/gnome_shell_3_9_4.png">{% img /images/gnome_shell_3_9_4_tn.png %}</a>

https://launchpad.net/~ricotz/+archive/testing

GNOME Shell 3.9.4 をUbuntu GNOME 13.10 にインストールしてみました。

<!-- more --> 

#### GNOME Shell 3.9.4 のインストール

{% codeblock %}
$ sudo add-apt-repository ppa:ricotz/testing
$ sudo apt-get update
$ sudo apt-get install gnome-shell
{% endcodeblock %}

#### ドックの設定
前回のAWN に続き、このバージョンではCairo-Dock も動かなくなりました。Dash to Dock GNOME Shell 拡張も正常に動かないようです。Docky を使うことにしました。

{% codeblock %}
$ sudo apt-get install docky
{% endcodeblock %}

#### トップバーの非表示

Hide Top Bar GNOME Shell 拡張が正常に動かなかったので、以前使用していたautohidetopbar2@werewolves.us の方のGNOME Shell 拡張を使用してみました。
shell-version は3.9.4 を指定しました。

{% codeblock metadata.json lang:js %}
{ 
  "description": "Auto hide the top panel",
  "extension-id": "auto-hide-top-panel", 
  "gettext-domain": "gnome-shell-extensions", 
  "name": "Auto Hide Top Panel",
  "settings-schema": "org.gnome.shell.extensions.auto-hide-top-panel", 
  "shell-version": [
	"3.5.92",
	"3.6",
	"3.6.1",
	"3.9.4"
  ], 
  "url": "http://fpmurphy.com/gnome-shell-extensions",
  "uuid": "autohidetopbar2@werewolves.us",
  "version": 1
}
{% endcodeblock %}
