# CLAUDE.md - app-legal

個人開発アプリの利用規約・プライバシーポリシーを一元管理するリポジトリ。GitHub Pages で静的ホスティング。

## ディレクトリ構成

```
app-legal/
├── aeta/                   ← 会えた（大切な人に会った日を記録）
│   ├── index.html
│   ├── terms.html
│   ├── privacy-policy.html
│   └── style.css
├── battery-nest/           ← BatteryNest（バッテリー残量で Nest が変化する Widget アプリ）
│   ├── index.html
│   ├── terms.html
│   ├── privacy-policy.html
│   └── style.css
└── heyalog/                ← へやログ（部屋の間取りで持ち物管理）
    ├── index.html
    ├── terms.html
    ├── privacy-policy.html
    └── style.css
```

## ファイル構成ルール

- 各アプリは `<app-name>/` ディレクトリに配置
- 各ディレクトリには `index.html`、`terms.html`、`privacy-policy.html`、`style.css` の4ファイル
- CSS は各アプリのブランドカラーに合わせた個別ファイル（同ディレクトリ内の `style.css` を参照）
- ルートには共通ファイルを置かない（各アプリが独立して完結する構成）

## HTML テンプレート規約

- `lang="ja"`、`charset="UTF-8"`、`viewport` メタタグ必須
- 利用規約は「第N条（タイトル）」形式
- プライバシーポリシーは「N. タイトル」形式
- 制定日を `<p class="last-updated">` で記載
- 各詳細ページに `<a href="index.html" class="back-link">` で戻るリンク

## CSS ブランドカラー

各アプリの `style.css` で以下のカラーをアプリに合わせて設定する。

| プロパティ | aeta | battery-nest | heyalog |
|-----------|------|--------------|---------|
| 背景色 (`body`) | `#fffbf7` | `#ECECEF` | `#EFE6DB` |
| テキスト色 | `#2d2d2d` | `#1C1C1E` | `#2C2318` |
| サブテキスト色 | `#8c8c8c` | `#8E8E93` | `#8C7E70` |
| リンク色 / アクセント | `#e07a5f` | `#1C1C1E` | `#785A38` |
| h2 下線 | `#f0ebe5` | `#D1D1D6` | `#C9BBA9` |
| カード / リンクボタン背景 | `#fff` | `#F7F7F9` | `#FFFFFF` |
| リンクボタン hover | `#f8f3ee` | `#E5E5EA` | `#E5DACF` |

## 連絡先

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

### BatteryNest（battery-nest）

- 二層課金: 消費型チケット 3 パック（¥100/¥400/¥800）+ Pro サブスク（月額¥400/年額¥1,980）
- Supabase（DB・認証・Edge Function）+ RevenueCat（課金管理）
- バッテリー情報: 端末内処理のみ、サーバー送信なし（プライバシーポリシーで明示）
- 期間限定 Nest（販売期間あり、再販保証なし、永久所有モデル）
- 通知なし、広告なし、トラッキングなし
- パスワードリセット機能 v1 未実装 → 利用規約に **赤字級警告** あり
- 特商法表示を利用規約 第11条に統合
- 改正個情法 第28条 越境移転（Supabase/RevenueCat 米国移転）開示済み
- GDPR 最小開示（EU/EEA 圏向け）あり
- 制定日: 2026年5月10日

## GitHub Pages

- 公開URL: `https://taroshun32.github.io/app-legal/`
- デプロイ: main ブランチへの push で自動反映（GitHub Pages 設定でソースを main / root に指定）

## 新しいアプリを追加する手順

1. `<app-name>/` ディレクトリを作成
2. 既存アプリのファイルをコピーしてテンプレートとして利用
3. `style.css` のカラーをアプリのブランドカラーに変更（上記カラー表を参考）
4. アプリ固有の情報（サービス内容、料金プラン、取得データ、第三者サービス等）を書き換え
