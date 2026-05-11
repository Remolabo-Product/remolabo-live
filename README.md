# リモラボ 朝昼夜活ライブ 公開ページ

## 📋 概要

リモラボの朝活・昼活・夜活で配信される動画を自動再生するWebページ。
Fireworkの動画プレイリストを埋め込んでいます。
リモシティにHTML埋め込みができないため、Netlifyで公開し、URLをリモシティに貼り付ける。

---

## 🎨 デザイン

**ベース**: 積み上げアプリと同じカラースキーム・フォント

### カラースキーム
- 背景: グラデーション `linear-gradient(135deg, #fff8e1 0%, #ffe082 100%)`
- ヘッダー: グラデーション `linear-gradient(135deg, #fff9c4 0%, #ffd54f 100%)`
- アクセントカラー: `#ff6f00`（オレンジ）
- テキスト: `#3e2723`（ダークブラウン）
- コンテナ背景: `#fffef7`（薄いクリーム色）

### フォント
- M PLUS Rounded 1c（Google Fonts）

### レスポンシブ対応
- スマホ・タブレット・PC対応

---

## 📦 ファイル構成

```
firework-playlist/
├── README.md          # このファイル
├── index.html         # メインページ
├── styles.css         # スタイルシート
├── _redirects         # Netlify用リダイレクト設定
└── assets/
    ├── remonyan.png       # リモにゃんアイコン
    ├── remonyan-1.png     # リモにゃんイラスト（小）
    ├── remonyan-2.png     # リモにゃんイラスト（中）
    └── remonyan-3.png     # リモにゃんイラスト（大）
```

---

## 🚀 デプロイ手順

### Phase 1: ローカル確認
1. ブラウザで `index.html` を開く
2. デザインが正しく表示されるか確認
3. Firework動画が埋め込まれているか確認

### Phase 2: GitHubリポジトリ作成
```bash
cd "h:\マイドライブ\Obsidian\93_remolabo_コンテンツ\firework-playlist"
git init
git add .
git commit -m "初回コミット: Firework動画プレイリストページ"
git branch -M main
git remote add origin https://github.com/Remolabo-Product/remolabo-live.git
git push -u origin main
```

### Phase 3: Netlifyデプロイ
1. Netlifyにログイン
2. 「New site from Git」を選択
3. GitHubリポジトリ `Remolabo-Product/remolabo-live` を選択
4. Build settings:
   - Build command: （空欄）
   - Publish directory: `.`
5. 「Deploy site」をクリック
6. デプロイURL確認（例: `https://remolabo-live.netlify.app`）

### Phase 4: スマホ動作確認
1. スマホからデプロイURLにアクセス
2. Firework動画が正常に表示されるか確認
3. 自動再生が動作するか確認
4. レイアウト崩れがないか確認

### Phase 5: カスタムドメイン設定（池田さん連携）
1. 池田さんにカスタムドメイン追加を依頼
   - 例: `firework.remolabo.com`
2. Netlify側でカスタムドメイン設定
   - Site settings → Domain management → Add custom domain
3. DNS設定（池田さん側で実施）
   - Aレコード or CNAMEレコード追加
4. SSL証明書自動発行確認（Netlify側）

### Phase 6: リモシティ連携
1. リモシティにURLを貼り付け
2. プレビュー確認
3. 参加者に動作確認してもらう

---

## 🔧 メンテナンス

### ファイル更新
1. ローカルでファイルを編集
2. git commit & push
3. Netlifyが自動デプロイ（約1分）

### Firework埋め込みコード更新
`index.html` の以下の部分を編集:
```html
<fw-storyblock
  channel="remolabo"
  playlist="o8N2q4"
></fw-storyblock>
```

---

## 📝 補足

### Firework埋め込みコード
```html
<script async type="module" src="//asset.fwcdn3.com/js/module/fwn.js?business_id=o0WWlj"></script>
<script async nomodule src="//asset.fwcdn3.com/js/fwn.js?business_id=o0WWlj"></script>

<fw-storyblock
  channel="remolabo"
  playlist="o8N2q4"
></fw-storyblock>
```

### 動作確認項目
- ✅ ブラウザで正常表示
- ✅ スマホで正常表示
- ✅ Firework動画が埋め込まれている
- ✅ 時間になったら自動再生される
- ✅ レスポンシブデザインが機能している
