# Windows 環境でターミナルを使う。

## 概要
シェルに **Nyagos**
コンソールに**msys2**
ターミナルエミュレータに**cmder**を使用する。
ついでに環境変数の管理ツール**RapidEnviromentEditor**もインストールする

## とりあえず最低限の設定

cmderを起動。
settingを開く(win+alt+p)
startupのtaskno
startupのtaskに行く

＋押す
名前をnyagosに
command欄に
`C:\Users\username\Documents\nyagos\nyagos.exe`
のようにnyagos.exeの場所を描く。
同様に

msys2もつくる。
こっちはcommand欄に
`C:\msys64\usr\bin\mintty /usr/bin/bash --login -i`
と書く。

環境パスHOMEを適当な場所に作成
msysはデフォルトで起動時に環境変数HOMEにあるファイルを読み込みます。
ここに.bash_profileを作る
`export PATH=/mingw64/bin:$PATH`
と書く。

cmder上でこれらが起動すれば成功

## pacmanのproxy設定をする
C:\msys64\etc\profile.dにproxy.shを作成
いつも通りproxyを書く。
```
export http_proxy=http://proxy-n.t-kougei.ac.jp:8080/
export https_proxy=$http_proxy
export ftp_proxy=$http_proxy
export rsync_proxy=$http_proxy
export HTTP_PROXY=$http_proxy
export HTTPS_PROXY=$http_proxy
export FTP_PROXY=$http_proxy
export RSYNC_PROXY=$http_proxy

 export no_proxy="localhost,127.0.0.1,localaddress,.localdomain.com"
```

C:\msys64\etcのpacman.confで`XferCommand = /usr/bin/curl -C - -f %u > %o`のコメントアウトをはずしダウンローダをcurlにする。

```
pacman --needed -Sy bash pacman pacman-mirrors msys2-runtime
pacman -Su
```
を実行

## nyagosの設定
nyagosのconfigは.nyagosに記入する
$HOME下に.nyagosを作成
```
set{
  MSYSBIN =[[C:\msys64\usr\bin]]
}

alias{
  vim = [[C:\msys64\usr\bin\vim.exe]]
}
```

```
これでnyagosでもvimが使えます。

nyagosは\でも/でもディレクトリを指定できるので便利です。
