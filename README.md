# 旭スタジオ Webサイト プロジェクト申し送り事項

本プロジェクトは「旭スタジオ」のWebサイトのソースコードとデプロイ環境を管理しています。

## 1. プロジェクト概要
- **GitHubリポジトリ**: `https://github.com/3from2/asahi-studio.git`
- **公開本番URL**: `https://asahi-studio.3from2.com`
- **ホスティング環境**: Vercel (デプロイ) + Cloudflare (ドメイン/DNS管理)
  - `main` ブランチにプッシュすると、自動的にVercelを通じて本番サイト（`asahi-studio.3from2.com`）にデプロイされます。

---

## 2. ファイル構成と役割
ルートディレクトリに本番用ファイルと、デザイン調整を行った別バージョンが存在します。

### 本番公開用ファイル
- **`index.html`**
  - **現状の適用状態**: 本番サイトで表示中。
  - **特徴**: 従来のTailwind CSSで構築された初期のすっきりとしたバージョン。

### 開発・検証用バリエーション（別バージョン）
- **`now_index_v3_sans_v2.html`**
  - **特徴**: Heroセクションのフォント構成を以下のように調整した「アコーディオンなし」バージョン。
    - タイトル「旭スタジオ」 ＝ Noto Sans JP (角ゴシック)
    - 縦書き説明文・住所 ＝ Noto Serif JP (明朝体)
    - Heroより下の各セクション ＝ Noto Sans JP (角ゴシック)
- **`now_index_v3_accordion.html`**
  - **特徴**: 各セクションをクリックするとスムーズに開閉する「アコーディオン」バージョン。
    - アコーディオンの展開には、カクつきのない滑らかなCSS Grid（`grid-template-rows: 0fr` ↔ `1fr`）を使用。
    - 各セクション見出し（`場について`など） ＝ Noto Serif JP (明朝体)
    - セクション内部のテキスト ＝ Noto Sans JP (角ゴシック)
- **`旧ver/`** (ディレクトリ)
  - 開発途中で作成した古いテストバージョン（`now_index_v3_sans.html` 等）を退避させています。

---

## 3. 今後の管理・運用ルール

### バージョンの切り替え方法（本番適用）
Vercelは `index.html` をルートの表示対象とします。
もし、アコーディオン版（`now_index_v3_accordion.html`）やフォント調整版（`now_index_v3_sans_v2.html`）を本番URLで公開したい場合は、**そのファイルの内容を `index.html` にコピー（上書き）して、GitHubへプッシュ**してください。

例（アコーディオン版を本番にする場合）:
1. `now_index_v3_accordion.html` の中身をコピー
2. `index.html` に貼り付けて上書き保存
3. Gitでコミットし、GitHubの `main` へプッシュ

### フォントスタックの指定ルール
- **明朝体 (Noto Serif JP)**:
  `font-family: "Noto Serif JP", "Hiragino Mincho ProN", "Yu Mincho", serif;`
- **角ゴシック (Noto Sans JP)**:
  `font-family: "Noto Sans JP", "Hiragino Kaku Gothic ProN", "Hiragino Sans", sans-serif;`
