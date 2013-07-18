---
layout: post
title: "Ubuntu 13.10 Daily Build + Mir"
date: 2013-07-01 00:30
comments: true
categories: Linux
---
<a href="/images/ubuntu_13_10_daily_build_mir.png">{% img /images/ubuntu_13_10_daily_build_mir_tn.png %}</a>

https://launchpad.net/~mir-team/+archive/staging

Ubuntu 13.10 Daily Build にMir を適用してみました。現時点では若干もたつく感じがしますが、今後改善されるでしょう。

<!-- more --> 

{% codeblock %}
$ sudo apt-add-repository ppa:mir-team/staging
$ sudo apt-get update
$ sudo apt-get upgrade
{% endcodeblock %}

特に資料を参考にしていないので、正式な手順ではないかもしれませんし、不十分かもしれません。

<a href="/images/ubuntu_13_10_daily_build_mir_gnome_shell.png">{% img /images/ubuntu_13_10_daily_build_mir_gnome_shell_tn.png %}</a>

GNOME Shell 3.8.3 で使った方が快適なような気がします。気のせいかもしれませんが。

http://www.olli-ries.com/running-mir/

ここにインストール方法が書いてありました。
