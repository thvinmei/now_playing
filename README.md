now_playing
===========

NowPlaying plugin for mikutter

ということで, mikutterから再生中の曲を投稿できるプラグインです.
正直Ruby書いたこと無かったのでなんで動いてるのかよくわかってません.
デフォではAudaciousで再生している曲を投稿しますが, ソースコード中の
rb_service = bus.service("org.mpris.MediaPlayer2.audacious")
のaudaciousのところをrhythmbox等に変更すると他のプレイヤーにも使えます.
DBus使ってるのでdbusが動いてるシステムでしか動きません.
上記の変更をしてもMPRISっていうのに対応してるプレイヤーしか使えません.
たぶんLinuxとかBSDで動く新しめのプレイヤーだったら大体対応してると思います.
あとソースコード中の文字列をいじると投稿するメッセージを変更できます.

誰でも書ける程度のことしかしてませんが誰もしてなかったので書きました. コロンブスの卵ですね.
ではでは.


以下追記．
## 要 ruby-dbus
```bash
sudo gem install ruby-dbus
```

## 音楽プレーヤー名の確認と編集
ターミナルで，
```bash
dbus-send --session --dest=org.freedesktop.DBus --type=method_call --print-reply /org/freedesktop/DBus org.freedesktop.DBus.ListNames | grep mpris
```
すれば実行中のMPRISで動作しているアプリケーションが抽出できるので，探す．

参考．
[DBus での BUS 一覧の取得方法](http://qiita.com/TNaruto/items/d481b4b5446f77ac556b)