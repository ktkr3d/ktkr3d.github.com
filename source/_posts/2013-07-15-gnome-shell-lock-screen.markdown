---
layout: post
title: "GNOME Shell Lock Screen"
date: 2013-07-15 08:57
comments: true
categories: Linux
---
<a href="/images/gnome_shell_lock_screen.png">{% img /images/gnome_shell_lock_screen.png %}</a>

GNOME Shell のロック画面で表示される時刻のフォントの上部が欠けていたので、暫定対策しました。

<!-- more -->

#### ロック画面のフォントの変更

`font-family: "DejaVu Sans";`でフォントファミリーを指定しています。

{% codeblock /usr/share/gnome-shell/theme/gnome-shell.css lang:css %}
.screen-shield-clock-time {
    font-family: "DejaVu Sans";
    font-size: 64pt;
    text-shadow: 0px 2px 2px rgba(0,0,0,0.4);
}

.screen-shield-clock-date {
    font-family: "DejaVu Sans";
    font-size: 24pt;
}
{% endcodeblock %}

#### 設定の反映

設定を反映するには、`Alt + F2` を押下、`r` を入力して`Enter`で、GNOME Shell を再起動します。
