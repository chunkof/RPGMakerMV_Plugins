# chunkof_DataFileNoCache.js

ゲームデータファイル(data/\*.json)のキャッシュを使用しなくするプラグイン。

ゲームをWeb公開している場合、ゲームの内容(マップやシナリオ、データベースなど)を変更してもキャッシュが残っていて変更が反映されない場合があります。
それを防止するプラグインです。

キャッシュのコントロールはプラグインを使用する以外にも、サーバの設定などでも可能です。よければそちらも検討ください。

## 留意点
このプラグインで対応できるのはゲームデータファイル(data/\*.json)のキャッシュのみです。
以下の変更には効果がありません。

 - 本体ソースファイル(\*.js)の更新
 - 登録プラグインの登録(plugins.js)
 - プラグイン(plugins/\*.js)の更新
 - 各種メディアファイルの更新

 など

## パラメータ
### useCacheByVersionID
- 1 : 変更がない場合キャッシュ使用。(デフォルト)
- 0 : キャッシュは常に使用しない。

RPGツクールMV以外の外部ツールを使ってゲームデータファイル(data/\*.json)を変更しないのであれば、1で問題ありません。（恐らく）

変更の有無はversionIDで検出しています。versionIDはRPGツクールMVでプロジェクトを保存するたびに更新されます。
これはSystem.jsonのロード完了していないとこの検出はできません。
versionIDによる変更チェックができない場合は、とりあえずキャッシュを使用しません。

System.jsonのロードには少し時間がかかるため、実際にはマップやイベントの読み込み時ぐらいしか変更チェックができないことが多いです。