# Webview Kiosk - 日本語版 README

> [!WARNING]
> Google の新しい開発者認証要件（2026-2027年）により、サイドローディングや
> F-Droid、NewPipe などの代替ストアが廃止される見込みです。
>
> 詳細情報：
> - F-Droid: https://f-droid.org/en/2025/10/28/sideloading.html
> - Keep Android Open: https://keepandroidopen.org
> - ビデオ解説: https://www.youtube.com/watch?v=wRvqdLsnsKY

## Webview Kiosk とは

Webview Kioskは、Android デバイスでセキュアなキオスク・スタイルのウェブ閲覧を実現するための、フリー＆オープンソースアプリケーションです。

受付端末、デジタルサイネージ、キッズ向けブラウザ、インタラクティブなサイン・アップフォーム、ホームアシスタント・ダッシュボード、または単なる壁掛け時計として機能します。

小規模ビジネスや個人ユーザー向けの、シンプルで単体のキオスク・ソリューションを目指しています。

## 主要機能

### コア機能 / スタンドアロン

- **Lock Task モード（ピン）**: デバイスのホーム画面、アプリ、ステータスバーへのアクセスを防止
- **セキュアな設定**: 生体認証、デバイス認証、またはカスタムパスワードで保護
- **URL フィルタリング**: 正規表現を使用したURL ブラックリスト＆ホワイトリスト
- **エクスポート/インポート**: 設定を Base64 または JSON 形式でバックアップ・復元
- **ローカルファイル**: デバイスから画像、音声、ビデオ、HTML ファイルをキオスク・モードで表示
- **デフォルトランチャー**: ホーム・アプリとして使用し、他のアプリを Lock Task モードで起動

### リモート管理 / エンタープライズ

#### 1. MQTT（Message Queuing Telemetry Transport）
- イベント監視、設定更新、コマンド実行、カスタム自動化をAPI 経由で実現
- MQTT ブローカーが必要（例：Mosquitto、EMQX、HiveMQ、HomeAssistant 統合）

#### 2. UnifiedPush
- 分散化されたプッシュ通知システムを介してコマンドと設定を送信
- ディストリビューター・アプリが必要（例：sunup、ntfy、gCompat-UP）

#### 3. 管理構成（App Restrictions）
- フル・マネージド・デバイス向けに MDM/EMM プロバイダーを介して設定をリモート構成
- デバイス・ポリシー・コントローラーを使用するパワーユーザーも対応（例：Test DPC、OwnDroid）

## パーミッション

- **INTERNET**: 一般的なウェブ閲覧
- **CAMERA**: （オプション）写真・ビデオ撮影が必要なウェブアプリ用
- **RECORD_AUDIO**: （オプション）音声録音が必要なウェブアプリ用
- **MODIFY_AUDIO_SETTINGS**: オーディオ・ルーティング用（これがないとマイクが動作しません）
- **ACCESS_FINE_LOCATION**: （オプション）正確な位置情報が必要なウェブアプリ用
- **ACCESS_COARSE_LOCATION**: （オプション）概算位置情報が必要なウェブアプリ用
- **QUERY_ALL_PACKAGES**: 起動可能なアプリ、デバイス・オーナー、Lock Task パッケージを検索
- **POST_NOTIFICATIONS**: （オプション）Lock Task モード起動と MQTT 用通知
- **FOREGROUND_SERVICE**: 永続通知と Lock Task・MQTT 管理
- **FOREGROUND_SERVICE_SPECIAL_USE**: Lock Task モード用アプリ復帰メカニズム
- **USE_BIOMETRIC**: Android 9 以降での生体認証置き換え
- **USE_FINGERPRINT**: 設定へのアクセス・ロック解除時の指紋認証
- **WAKE_LOCK**: MQTT コマンド受信時に画面をウェイク
- **WRITE_EXTERNAL_STORAGE**: Android 9.0（SDK 28）以下でのファイル・ダウンロード
- **API（Dhizuku）**: 共有デバイス・オーナー権限をリクエスト

## インストール方法

[v0.17.0](https://github.com/nktnet1/webview-kiosk/releases/tag/v0.17.0) 以降、
Google Play の[自動保護](https://support.google.com/googleplay/android-developer/answer/10183279)は
意図的に **無効化** されているため、Aurora Store からのインストールが可能です。

[v0.15.7](https://github.com/nktnet1/webview-kiosk/releases/tag/v0.15.7) 以降、
Google Play Store 以外のすべてのインストール・ソースから、パッケージ名が
`com.nktnet.webview_kiosk` から `uk.nktnet.webviewkiosk` に変更されました。

### 入手方法

<div align="center">

[<img src="./docs/public/static/images/badges/github.png" alt="GitHub でダウンロード" width="260px" />](https://github.com/nktnet1/webview-kiosk/releases)
[<img src="./docs/public/static/images/badges/obtainium.png" alt="Obtainium でダウンロード" width="260px" />](https://apps.obtainium.imranr.dev/redirect?r=obtainium://add/https://github.com/nktnet1/webview-kiosk)
[<img src="./docs/public/static/images/badges/google-play.svg" alt="Google Play でダウンロード" width="260px" />](https://play.google.com/store/apps/details?id=com.nktnet.webview_kiosk)
[<img src="./docs/public/static/images/badges/f-droid.svg" alt="F-Droid でダウンロード" width="260px" />](https://f-droid.org/packages/uk.nktnet.webviewkiosk)
[<img src="./docs/public/static/images/badges/izzy-on-droid.svg" alt="IzzyOnDroid でダウンロード" width="260px" />](https://apt.izzysoft.de/fdroid/index/apk/uk.nktnet.webviewkiosk)

</div>

## ドキュメント

### 日本語ドキュメント

- **[セットアップガイド（日本語）](./docs/SETUP_GUIDE_JA.md)** - キオスク設定の詳細手順
- **[キオスク設定ガイド（日本語）](./docs/KIOSK_SETUP_JA.md)** - 運用管理方法

### 英語ドキュメント

- **[Official Documentation](https://webviewkiosk.nktnet.uk)** - 公式ドキュメント

## クイックスタート

### 基本的な受付キオスク設定（GalaxyTab A9+ 向け）

#### 1. インストール

```bash
# APK ダウンロード
wget https://github.com/nktnet1/webview-kiosk/releases/download/v0.26.9/webview-kiosk-v0.26.9-release.apk

# デバイスにインストール
adb install webview-kiosk-v0.26.9-release.apk
```

#### 2. デバイス所有者権限の設定（初期セットアップ時）

```bash
# 工場出荷状態後に実行
adb shell dpm set-device-owner uk.nktnet.webviewkiosk/.WebviewKioskAdminReceiver

# 確認
adb shell dpm get-active-admin
```

#### 3. アプリ設定

1. **セキュリティ**：パスワード設定（例：`reception2025`）
2. **ウェブコンテンツ**：
   - URL：`https://www.e-shisetsu.e-aichi.jp/web_info.html`
   - ホワイトリスト：`https://www\.e-shisetsu\.e-aichi\.jp/.*`
3. **ウェブライフサイクル**：
   - 不活動時にリセット：600秒（10分）
4. **一般**：
   - Lock Task モード：ON
   - ホーム画面に設定

詳細は [セットアップガイド](./docs/SETUP_GUIDE_JA.md) を参照してください。

## ビルド方法

### 環境準備

```bash
# Android SDK をインストール
brew install android-commandlinetools

# SDK ライセンスを受け入れる
sdkmanager --licenses

# プラットフォームとビルドツールをインストール
sdkmanager "platforms;android-37" "build-tools;36.0.0"
```

### ビルド実行

```bash
# リリース APK をビルド
KEYSTORE_PASSWORD=your_password \
KEY_ALIAS=your_alias \
KEY_PASSWORD=your_key_password \
./gradlew assembleRelease

# デバッグ APK をビルド
./gradlew assembleDebug
```

APK ファイルは以下のディレクトリに生成されます：
- リリース版：`app/build/outputs/apk/release/app-release.apk`
- デバッグ版：`app/build/outputs/apk/debug/app-debug.apk`

## トラブルシューティング

### 設定画面にアクセスできない

パスワードをリセットする場合は、デバイスをリセット後に再度セットアップしてください。

### URLフィルタリングが動作しない

正規表現の形式を確認してください：
- ドット `.` はエスケープが必要：`\.`
- 正規表現例：`https://www\.e-shisetsu\.e-aichi\.jp/.*`

### 画面が勝手に消える

デバイス設定 → ディスプレイ → スクリーンタイムアウトを確認してください。

## セキュリティに関する注意

- 定期的にパスワードを変更してください（月1回推奨）
- 設定をエクスポートしてバックアップしてください
- Webview Kiosk を常に最新版に保ってください
- デバイス管理者権限は厳重に管理してください

## ライセンス

このプロジェクトは GNU Affero General Public License v3.0 またはそれ以降の下でライセンスされています。

詳細は [LICENSE](./LICENSE) ファイルを参照してください。

## サポート

- **公式ドキュメント**: https://webviewkiosk.nktnet.uk
- **GitHub リポジトリ**: https://github.com/nktnet1/webview-kiosk
- **メールサポート**: support@webviewkiosk.nktnet.uk
- **GitHub Issues**: https://github.com/nktnet1/webview-kiosk/issues

