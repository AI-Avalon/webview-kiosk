# Webview Kiosk v0.26.9 - リリースパッケージ

このフォルダには、Webview Kiosk v0.26.9 の APK ファイルとセットアップ情報が含まれています。

## ファイル一覧

| ファイル | サイズ | 説明 |
|---------|--------|-----|
| `webview-kiosk-v0.26.9-release.apk` | 4.3 MB | **本番環境向け**（推奨） |
| `webview-kiosk-v0.26.9-debug.apk` | 18 MB | **開発・デバッグ用** |
| `README_RELEASE.md` | - | このファイル |

## インストール方法

### 方法 1: ADB コマンド（推奨）

```bash
# USB デバッグが有効なデバイスに接続
adb devices

# APK をインストール
adb install webview-kiosk-v0.26.9-release.apk
```

### 方法 2: ファイル転送

1. APK をデバイスにコピー
2. ファイル・マネージャーから APK を選択
3. インストールをタップ
4. 不明なソースからのインストールを許可（初回のみ）

## セットアップ手順

### Step 1: デバイス所有者権限の設定（重要）

受付キオスク用途では、**デバイス所有者（Device Owner）権限** が必須です。

工場出荷状態またはリセット直後に以下を実行：

```bash
adb shell dpm set-device-owner uk.nktnet.webviewkiosk/.WebviewKioskAdminReceiver
```

確認コマンド：
```bash
adb shell dpm get-active-admin
```

### Step 2: アプリ起動と初期設定

1. **Webview Kiosk を開く**
2. **設定** → セキュリティ
3. **認証方法**：パスワード を選択
4. **パスワード**を設定（例：`reception2025`）

### Step 3: ウェブコンテンツ設定

1. **設定** → ウェブコンテンツ
2. **ウェブサイト URL**：
   ```
   https://www.e-shisetsu.e-aichi.jp/web_info.html
   ```
3. **ホワイトリスト**：
   ```
   https://www\.e-shisetsu\.e-aichi\.jp/.*
   ```

### Step 4: タイムアウト設定

1. **設定** → ウェブライフサイクル
2. **不活動時にリセット (秒)**：`600`（10分）

### Step 5: Lock Task 有効化

1. **設定** → 一般
2. **Lock Task モード**：ON
3. **戻るボタン動作**：無効

### Step 6: ホーム画面に設定

1. **設定** → 一般
2. **デフォルトランチャー**：Webview Kiosk を選択

詳細は GitHub リポジトリのドキュメントを参照してください：
- **セットアップガイド**: https://github.com/nktnet1/webview-kiosk/blob/main/docs/SETUP_GUIDE_JA.md
- **キオスク設定ガイド**: https://github.com/nktnet1/webview-kiosk/blob/main/docs/KIOSK_SETUP_JA.md

## 運用上の注意

### 日常の使用フロー

```
デバイス起動
  ↓
Webview Kiosk 自動起動
  ↓
ホーム画面 → 来客がサイト操作
  ↓
10分間無操作
  ↓
自動リセット → ホーム画面に戻る
```

### セキュリティのベストプラクティス

✅ **実施すべき項目**
- 月1回以上のパスワード変更
- 定期的な設定情報のバックアップ
- アプリの定期的なアップデート
- デバイス管理者権限の保護

❌ **避けるべき項目**
- Lock Task モードの無効化
- URL ホワイトリストの削除
- パスワード設定の解除
- 他のアプリのインストール

## トラブルシューティング

### Q: 設定画面にアクセスできない

**A:** パスワードをリセットする場合、デバイスをリセット後に再度セットアップしてください。

### Q: URLフィルタリングが機能しない

**A:** ホワイトリストの正規表現を確認してください。
- 正：`https://www\.e-shisetsu\.e-aichi\.jp/.*`
- 誤：`https://www.e-shisetsu.e-aichi.jp/.*` （ドットがエスケープされていない）

### Q: 画面が勝手に消える

**A:** デバイス設定 → ディスプレイ → スクリーンタイムアウトを確認してください。

### Q: 電源ボタンを押すと他のアプリが起動する

**A:** Webview Kiosk 設定で Lock Task モードが ON になっているか確認してください。

## 技術仕様

| 項目 | 詳細 |
|-----|------|
| **アプリ名** | Webview Kiosk |
| **バージョン** | 0.26.9 |
| **最小 Android** | Android 5.0（API 21） |
| **ターゲット Android** | Android 14（API 37） |
| **アプリケーション ID** | `uk.nktnet.webviewkiosk` |
| **ファイル形式** | APK（Android Package） |

## サポート情報

- **公式 Web サイト**: https://webviewkiosk.nktnet.uk
- **GitHub リポジトリ**: https://github.com/nktnet1/webview-kiosk
- **メールサポート**: support@webviewkiosk.nktnet.uk
- **GitHub Issues**: https://github.com/nktnet1/webview-kiosk/issues

## ライセンス

Webview Kiosk は GNU Affero General Public License v3.0（AGPL-3.0）またはそれ以降の下でライセンスされています。

詳細は https://github.com/nktnet1/webview-kiosk/blob/main/LICENSE を参照してください。

---

**リリース日時**: 2026-05-03  
**ビルド環境**: macOS Sonoma + Gradle 9.5.0 + Android SDK API 37

