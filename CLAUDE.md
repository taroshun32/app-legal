# CLAUDE.md - app-legal

個人開発アプリの利用規約・プライバシーポリシーを一元管理するリポジトリ。GitHub Pages で静的ホスティング。

## ディレクトリ構成

```
app-legal/
├── index.html              ← ルートページ（アプリ一覧）
├── style.css               ← 全アプリ共通スタイルシート
├── aeta/                   ← 会えた（大切な人に会った日を記録）
│   ├── index.html
│   ├── terms.html
│   └── privacy-policy.html
└── heyalog/                ← へやログ（部屋の間取りで持ち物管理）
    ├── index.html
    ├── terms.html
    └── privacy-policy.html
```

## 規約

### ファイル構成ルール
- 各アプリは `<app-name>/` ディレクトリに配置
- 各ディレクトリには必ず `index.html`（トップ）、`terms.html`（利用規約）、`privacy-policy.html`（プライバシーポリシー）の3ファイル
- CSS はルートの `style.css` を共有（サブディレクトリからは `../style.css` で参照）
- ルート `index.html` にはすべてのアプリへのリンクを掲載

### HTML テンプレート規約
- `lang="ja"`、`charset="UTF-8"`、`viewport` メタタグ必須
- 利用規約は「第N条（タイトル）」形式
- プライバシーポリシーは「N. タイトル」形式
- 制定日を `<p class="last-updated">` で記載
- 各詳細ページに `<a href="index.html" class="back-link">` で戻るリンク

### 連絡先
- 全アプリ共通: taroshun32.dev@gmail.com

## アプリ別の要点

### 会えた（aeta）
- 買い切り課金（¥250）のみ
- Supabase（DB・認証）
- ローカル通知あり
- 制定日: 2025年2月8日

### へやログ（heyalog）
- サブスクリプション（月額/年額+7日無料トライアル）+ 買い切りの3プラン
- Supabase（DB・認証）+ RevenueCat（課金管理）
- 通知なし
- 制定日: 2026年2月28日

## GitHub Pages

- 公開URL: `https://<username>.github.io/app-legal/`
- デプロイ: main ブランチへの push で自動反映（GitHub Pages 設定でソースを main / root に指定）

## 新しいアプリを追加する手順

1. `<app-name>/` ディレクトリを作成
2. 既存アプリのファイルをコピーしてテンプレートとして利用
3. アプリ固有の情報（サービス内容、料金プラン、取得データ、第三者サービス等）を書き換え
4. ルート `index.html` にリンクを追加
