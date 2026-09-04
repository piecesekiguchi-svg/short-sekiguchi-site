# HIROKI SEKIGUCHI サイト（素のHTML/CSS版）

現在の short-sekiguchi.com（Wix）と同じ雰囲気で作った、GitHub Pagesで公開できる静的サイトです。
フレームワーク不要。VSコードで `index.html` と `css/style.css` を直接編集するだけで更新できます。

## フォルダ構成

```
site/
├── index.html        ページ本体（セクションごとにコメントで区切ってあります）
├── css/
│   └── style.css      デザイン（色・余白・フォントはここで調整）
└── images/            写真（今は仮のプレースホルダー画像が入っています）
```

## 写真の差し替え（重要）

`images/` フォルダの画像は、レイアウト確認用の仮画像（グレーの背景にファイル名が入っているだけ）です。
サンドボックス環境のネットワーク制限により、Wixサイトの写真を自動ダウンロードできませんでした。

以下の手順で、ご自身の写真に差し替えてください。同じファイル名で保存すればコードの変更は不要です。

1. short-sekiguchi.com を開き、使いたい写真を右クリック →「名前を付けて画像を保存」
2. 保存した画像を `images/` フォルダの対応するファイル名にリネームして上書き
   - `hero.jpg` … トップの大きい写真
   - `catch1.jpg` … キャッチコピー下の写真
   - `gallery1.jpg`〜`gallery5.jpg` … GALLERYセクション
   - `profile.jpg` … PROFILEセクションの顔写真
   - `story1.jpg` / `story2.jpg` … STORYセクション
   - `review1.jpg`〜`review4.jpg` … REVIEWセクション（お客様の声のスクショなど）
3. ブラウザで `index.html` を開いて確認

## ローカルで確認する

VSコードの拡張機能「Live Server」を入れて `index.html` を右クリック →「Open with Live Server」が一番簡単です。
拡張機能を使わない場合はターミナルで：

```bash
cd site
python3 -m http.server 8000
```

その後ブラウザで `http://localhost:8000` を開きます。

## GitHubに公開する（GitHub Pages）

1. GitHubで新しいリポジトリを作成（例: `short-sekiguchi-site`）
2. このフォルダの中身をそのリポジトリにアップロード（VSコードなら「ソース管理」パネルからPublish、
   またはターミナルで以下）

   ```bash
   cd site
   git init
   git add .
   git commit -m "初回公開"
   git branch -M main
   git remote add origin https://github.com/【ユーザー名】/short-sekiguchi-site.git
   git push -u origin main
   ```

3. GitHubのリポジトリページ → Settings → Pages
4. 「Branch」を `main` / `/(root)` に設定して Save
5. 数分後、`https://【ユーザー名】.github.io/short-sekiguchi-site/` で公開されます

### 独自ドメイン（short-sekiguchi.com）を使う場合

- `site/` フォルダ直下に `CNAME` という名前のファイルを作り、中身に `www.short-sekiguchi.com` の1行だけ書く
- 現在のドメイン管理画面（お名前.com、Wixなど）で、CNAMEレコードを `【ユーザー名】.github.io` に向ける
- GitHub Pages の Settings → Pages で Custom domain に同じドメインを入力して保存

## 更新の流れ（VSコードでの運用）

1. VSコードで `site` フォルダを開く
2. `index.html` のテキストや `css/style.css` の色・余白を編集
3. 保存 → VSコードの「ソース管理」パネルで変更をコミット → Push
4. GitHub Pagesが自動で再ビルドし、数分後に反映されます
