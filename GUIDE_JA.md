# Webview Kiosk v0.26.9 - 完全ガイド

このドキュメントは、Webview Kiosk v0.26.9 の完全なセットアップ・運用ガイドです。

## 📦 ディレクトリ構成

```
webview-kiosk/
├── releases/                          # リリースパッケージ
│   ├── webview-kiosk-v0.26.9-release.apk  # 本番環境用（推奨）
│   ├── webview-kiosk-v0.26.9-debug.apk    # 開発・テスト用
│   ├── README_RELEASE.md              # リリースノート
│   ├── BUILD_INFO.txt                 # ビルド情報
│   └── CHECKLIST.md                   # 導入チェックリスト
│
├── docs/                              # ドキュメント
│   ├── SETUP_GUIDE_JA.md              # セットアップガイド（詳細）
│   ├── KIOSK_SETUP_JA.md              # キオスク設定ガイド
│   └── README.md                      # 元のドキュメント
│
└── README_JA.md                       # 日本語 README

```

## 🚀 クイックスタート（5分で完了）

### Step 1: APK をインストール

```bash
adb install releases/webview-kiosk-v0.26.9-release.apk
```

### Step 2: デバイス所有者権限を設定

**重要：工場出荷状態またはリセット直後に実行**

```bash
adb shell dpm set-device-owner uk.nktnet.webviewkiosk/.WebviewKioskAdminReceiver
```

### Step 3: アプリを起動して初期設定

1. **セキュリティ**: パスワード設定
2. **ウェブコンテンツ**: URL ホワイトリスト設定
3. **タイムアウト**: 600秒（10分）に設定
4. **Lock Task**: ON に設定
5. **ホーム画面**: Webview Kiosk を選択

詳細は [セットアップガイド](docs/SETUP_GUIDE_JA.md) を参照してください。

## 📚 ドキュメント一覧

### インストール関連

| ドキュメント | 内容 | 対象 |
|-----------|------|------|
| [README_RELEASE.md](releases/README_RELEASE.md) | リリースノート・インストール手順 | 全員 |
| [BUILD_INFO.txt](releases/BUILD_INFO.txt) | ビルド情報・環境詳細 | 管理者 |

### セットアップ関連

| ドキュメント | 内容 | 対象 |
|-----------|------|------|
| [SETUP_GUIDE_JA.md](docs/SETUP_GUIDE_JA.md) | 詳細なセットアップ手順書 | 初回設定者 |
| [KIOSK_SETUP_JA.md](docs/KIOSK_SETUP_JA.md) | キオスク機能詳細説明 | 管理者 |

### 導入・運用関連

| ドキュメント | 内容 | 対象 |
|-----------|------|------|
| [CHECKLIST.md](releases/CHECKLIST.md) | 導入チェックリスト | 導入担当者 |
| [README_JA.md](README_JA.md) | 全体的な説明書 | 全員 |

## 🎯 使用シーン別ガイド

### 初めてインストールする場合

1. [README_RELEASE.md](releases/README_RELEASE.md) を読む
2. APK をダウンロードしてインストール
3. [SETUP_GUIDE_JA.md](docs/SETUP_GUIDE_JA.md) に従って設定
4. [CHECKLIST.md](releases/CHECKLIST.md) で確認

### 受付キオスクとして運用する場合

1. [KIOSK_SETUP_JA.md](docs/KIOSK_SETUP_JA.md) で設定方法確認
2. 以下の設定を実施：
   - URL ホワイトリスト：`https://www\.e-shisetsu\.e-aichi\.jp/.*`
   - タイムアウト：600秒（10分）
   - Lock Task：ON
3. 定期的なパスワード変更

### トラブルが発生した場合

1. [SETUP_GUIDE_JA.md](docs/SETUP_GUIDE_JA.md) の「トラブルシューティング」セクション
2. [README_RELEASE.md](releases/README_RELEASE.md) の「トラブルシューティング」セクション
3. 公式サポート：support@webviewkiosk.nktnet.uk

## 💾 ファイル情報

### APK ファイル

#### リリース版（本番環境推奨）
```
ファイル名：webview-kiosk-v0.26.9-release.apk
サイズ：4.3 MB
署名：本番署名キー付き
用途：実装環境・ユーザー配布
```

#### デバッグ版（開発・テスト用）
```
ファイル名：webview-kiosk-v0.26.9-debug.apk
サイズ：18 MB
署名：デバッグ署名キー付き
用途：開発・テスト・QA
```

## ✅ 確認リスト

以下の全てが完了したら、本番環境での運用を開始できます：

- [ ] APK がインストール済み
- [ ] デバイス所有者権限が設定済み
- [ ] セキュリティ設定（パスワード）が完了
- [ ] URL ホワイトリストが設定済み
- [ ] タイムアウトが 10分に設定済み
- [ ] Lock Task モードが ON
- [ ] ホーム画面に設定済み
- [ ] すべての機能テストが完了
- [ ] セキュリティテストが合格
- [ ] スタッフが操作方法を理解

詳細は [CHECKLIST.md](releases/CHECKLIST.md) を参照してください。

## 🔒 セキュリティに関する注意

### ✅ 実施すべき項目

- 月1回以上のパスワード変更
- 定期的な設定バックアップ
- 常に最新版のアプリを使用
- デバイス管理者権限の厳格な管理

### ❌ 避けるべき項目

- Lock Task モードの無効化
- URL ホワイトリストの削除
- パスワード設定の解除
- 他のアプリのインストール

詳細は [SETUP_GUIDE_JA.md](docs/SETUP_GUIDE_JA.md) の「セキュリティのベストプラクティス」を参照。

## 📞 サポート情報

### 公式リソース

- **Web サイト**: https://webviewkiosk.nktnet.uk
- **GitHub**: https://github.com/nktnet1/webview-kiosk
- **メール**: support@webviewkiosk.nktnet.uk
- **Issues**: https://github.com/nktnet1/webview-kiosk/issues

## 📋 バージョン情報

| 項目 | 詳細 |
|-----|------|
| **アプリバージョン** | 0.26.9 |
| **リリース日** | 2026-05-03 |
| **ビルド環境** | macOS Sonoma + Java 21 + Android SDK 37 |
| **ターゲット Android** | Android 14（API 37）以下 |
| **最小 Android** | Android 5.0（API 21）以上 |
| **ライセンス** | GNU AGPL-3.0 以降 |

## 🔄 更新履歴

| バージョン | 日付 | 更新内容 |
|----------|------|--------|
| 0.26.9 | 2026-05-03 | 日本語化対応・ドキュメント整備 |

## 📝 ドキュメント更新

これらのドキュメントは定期的に更新されます。
最新版は GitHub リポジトリから取得してください：
https://github.com/nktnet1/webview-kiosk

---

**ドキュメント作成日**: 2026-05-03  
**対象バージョン**: 0.26.9

