## Windowsにnodejs開発環境を構築

## nodist
nodistはnodejsのバージョン管理ツール
linuxでいうnodebrew
インストーラを使ってダウンロード、インストール

## nodejsのインストール
管理者でターミナル起動(terminalについては   [windowsでターミナルを使えるようにする](./windows_on_terminal.md.html)を参照)
nodist update
おわり
node -v
npm -v
で確認

## expressのインストール
proxy使用下では環境変数HTTP_PROXYを作成しておく
```
npm install express -g
npm install express-generator -g

```
以下テスト
```bash
express test
cd test
npm install
npm start
```
起動すれば成功
