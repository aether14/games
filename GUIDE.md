# ゲーム開発・デプロイ 指南書

このドキュメントは、ブラウザゲームの開発からCloudflare Pagesへのデプロイまでの手順をまとめたものです。

---

## 📁 プロジェクト構成

```
D:\Development\games\
├── janken/
│   └── index.html    ← じゃんけんゲーム
└── (今後追加するゲーム)/
    └── index.html
```

---

## 🌐 公開URL

| URL | 説明 |
|-----|------|
| https://games-11s.pages.dev/janken/ | Cloudflare Pages のデフォルトURL |
| https://games.sanakaku.blue/janken/ | カスタムドメイン（設定済み） |

---

## 🔧 技術スタック

- **フロントエンド**: HTML + CSS + JavaScript（単一ファイル）
- **ホスティング**: Cloudflare Pages
- **バージョン管理**: GitHub
- **ドメイン管理**: Cloudflare DNS

---

## 📝 開発フロー

### 1. ゲームを作成・編集

`D:\Development\games\` 内にフォルダを作成し、`index.html` を配置。

例：新しいゲーム「quiz」を追加する場合
```
games/
├── janken/
│   └── index.html
└── quiz/           ← 新規追加
    └── index.html
```

### 2. GitHubにプッシュ

```powershell
cd D:\Development\games
git add .
git commit -m "〇〇ゲームを追加"
git push
```

### 3. 自動デプロイ

GitHubにプッシュすると、Cloudflare Pagesが自動的にデプロイします。
通常1〜2分で反映されます。

---

## 🚀 初期セットアップ（完了済み）

以下は今回実施した初期セットアップの記録です。

### GitHubリポジトリ

- **リポジトリURL**: https://github.com/aether14/games
- **ブランチ**: main

### Cloudflare Pages設定

| 項目 | 設定値 |
|------|--------|
| プロジェクト名 | games |
| Pagesドメイン | games-11s.pages.dev |
| 連携リポジトリ | aether14/games |
| プロダクションブランチ | main |
| フレームワークプリセット | なし |
| ビルドコマンド | （空白） |
| ビルド出力ディレクトリ | / |

### DNS設定（Cloudflare）

sanakaku.blue のDNSレコード:

| タイプ | 名前 | ターゲット | プロキシ |
|--------|------|-----------|---------|
| CNAME | games | games-11s.pages.dev | オン |

---

## 🎮 じゃんけんゲームの機能

### 実装済み機能

- ✅ グー・チョキ・パーの選択
- ✅ コンピュータのランダム選択
- ✅ 勝敗判定
- ✅ スコア記録（勝ち・負け・あいこ）
- ✅ アニメーション効果
- ✅ 効果音（Web Audio API）
  - クリック音
  - シェイク音（じゃんけんぽん）
  - 勝利ファンファーレ
  - 負け音
  - あいこ音
  - リセット音

### デザイン

- ダークモードUI
- レスポンシブ対応（スマホ可）
- Zen Maru Gothicフォント使用

---

## 🔮 今後の拡張案

### 新しいゲームを追加する場合

1. `games/` フォルダ内に新しいフォルダを作成
2. `index.html` を作成
3. GitHubにプッシュ
4. 自動でデプロイされる

アクセスURL例:
- `https://games.sanakaku.blue/quiz/`
- `https://games.sanakaku.blue/memory/`

### バックエンド機能が必要な場合

スコアランキングやマルチプレイなど、サーバー側の処理が必要な場合は **Cloudflare Workers** を追加で設定可能。

---

## 🛠 トラブルシューティング

### デプロイが反映されない

1. GitHubにプッシュされているか確認
2. Cloudflare Pages ダッシュボードでデプロイステータス確認
3. ブラウザのキャッシュをクリア（Ctrl+Shift+R）

### カスタムドメインにアクセスできない

1. DNS設定を確認（CNAMEレコード）
2. SSL証明書の発行を待つ（最大24時間）
3. Cloudflare Pagesの「カスタムドメイン」タブでステータス確認

### 効果音が鳴らない

- ブラウザの音量設定を確認
- 最初のクリックで音声が有効化される仕様

---

## 📚 参考リンク

- [GitHub リポジトリ](https://github.com/aether14/games)
- [Cloudflare Pages ダッシュボード](https://dash.cloudflare.com/)
- [Cloudflare Pages ドキュメント](https://developers.cloudflare.com/pages/)

---

## 💡 Cursorでの作業のコツ

### Cursorを使うべき作業
- コードの作成・編集
- バグ修正
- 新機能の実装
- ファイル操作

### ChatGPT/Geminiに任せられる作業
- 設計相談・企画
- ドキュメント作成
- 一般的な質問
- Cloudflare等の設定手順の確認

---

*最終更新: 2024年12月18日*

