# Helios Drift

恒星ヘリオスを巡る7つの惑星を探索し、海賊と古代の守護機に挑むブラウザ宇宙探索アクションです。Three.js（r160）で動き、インストールは不要です。

## ファイル構成

```
index.html        紹介サイト（スクロール連動の3Dツアー）
game/index.html   ゲーム本体
favicon.svg       サイトアイコン
404.html          存在しないURLを開いたときのページ
.nojekyll         GitHub Pages の Jekyll 処理を無効化
```

紹介サイトの「プレイする」ボタンは `game/` を開き、ゲームのタイトル画面下部の「紹介サイトへ戻る」は紹介サイトへ戻ります。リンクはすべて相対パスなので、リポジトリ名に関係なくそのまま動きます。

## GitHub Pages で公開する手順

1. GitHub で新しいリポジトリを作成します（例：`helios-drift`）。公開範囲は Public にします。
2. この Zip を展開し、中身（`index.html` や `game` フォルダなど）をリポジトリの直下にアップロードします。
   - ブラウザの場合：リポジトリの「Add file」→「Upload files」に、展開したファイルとフォルダをまとめてドラッグします。
   - `.nojekyll` は隠しファイルのため、ドラッグで漏れることがあります。漏れても表示に影響はありません。
3. リポジトリの「Settings」→「Pages」を開きます。
4. 「Build and deployment」の Source を「Deploy from a branch」にし、Branch を `main`、フォルダを `/ (root)` にして「Save」を押します。
5. 1〜2分待つと、同じ画面に公開URL（`https://<ユーザー名>.github.io/<リポジトリ名>/`）が表示されます。

コマンドラインの場合：

```bash
cd helios-drift-site
git init
git add .
git commit -m "Publish Helios Drift"
git branch -M main
git remote add origin https://github.com/<ユーザー名>/helios-drift.git
git push -u origin main
```

その後、上の手順 3〜5 で Pages を有効にします。

## 手元で確認する

`index.html` をダブルクリックで開くと、ES モジュールの読み込みがブラウザに止められて表示されないことがあります。簡易サーバーを使ってください。

```bash
cd helios-drift-site
python3 -m http.server 8000
# ブラウザで http://localhost:8000 を開く
```

## 外部リソース

- Three.js 0.160.0（cdn.jsdelivr.net、バージョン固定）
- Google Fonts：Michroma / Zen Kaku Gothic New / JetBrains Mono

どちらもインターネット接続が必要です。

## セキュリティ

- 各ページに Content-Security-Policy を設定し、スクリプトの読み込み先を自サイトと cdn.jsdelivr.net に、フォントの読み込み先を Google Fonts に限定しています。
- サーバー側の処理、外部への送信、秘密情報はありません。
- セーブデータはブラウザの localStorage にだけ保存されます。読み込み時に型・範囲・サイズを検証し、不正な値は初期値に戻します。
- 画面に表示する文字列はすべて `textContent` で挿入しており、`innerHTML` は使っていません。
- 外部リンクはありません（ゲームと紹介サイトの相互リンクのみ）。

## 操作（抜粋）

| 操作 | キーボード&マウス | ゲームパッド |
|---|---|---|
| 機首の向き | マウス / 矢印キー | 左スティック |
| スロットル | W / S・ホイール | RT / LT |
| 射撃 | 左クリック / Space | A |
| ミサイル | Z / 右クリック | 十字キー上 |
| 巡航ドライブ | C | LB |
| スキャン・調査 | R 長押し | X |
| ドッキング | F | Y |

タッチ操作にも対応しています。詳しくはゲーム内の「操作方法」を参照してください。
# helios-drift-site
