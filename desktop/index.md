---
title: デスクトップ版について - capsicum
---

# デスクトップ版

capsicum は iOS / Android のモバイル版に加え、macOS / Linux / Windows のデスクトップ版にも展開しています。
すべてのプラットフォームで、モバイル版と同じ Flutter コードベースから配信しています。UI はウィンドウ幅に応じて自動でレスポンシブに切り替わり、各OSのネイティブ機能に少しずつ対応しています。

## インストール

### macOS

[![Download on the Mac App Store](https://img.shields.io/badge/Download_on_the-Mac_App_Store-000000?style=for-the-badge&logo=apple&logoColor=white)](https://apps.apple.com/jp/app/capsicum/id6760206608)

Mac App Store から無償で配信中（v1.24 で初公開）。
Universal Purchase により、 iOS / iPadOS と同一の App として提供しています。

iPad でも、メニューバー（iPadOS 26〜）にデスクトップと同じメニューが並び、外付けキーボードからショートカットを使えます（v2.6〜）。

#### 動作要件

macOS 12 以降。Apple シリコン搭載の Mac を推奨します。

Intel Mac でもインストールはできますが、動作は実験的な扱いで、実用はおすすめしません。開発元に Intel Mac の実機がなく、動作を確かめられないためです。画面の描画が乱れるといった報告を受けています。不具合のご報告は歓迎しますが、対応の優先順位は低くなります。

### Windows

[![Get it from Microsoft](https://img.shields.io/badge/Get_it_from-Microsoft-000000?style=for-the-badge&logo=microsoft&logoColor=white)](https://apps.microsoft.com/detail/9np2gr7m2w6p)

**Microsoft Store** から無償で配信中（v1.25 で初回配布開始、v1.27 で Store 公開達成）。証明書 import の手間なく、一般の Windows ユーザーがそのままインストールできます。

#### 動作要件

- Windows 10 (1809 以降) / Windows 11 x64

Windows の配布は **Microsoft Store 単独**です。

### Linux

[![Linux AppImage](https://img.shields.io/badge/Linux-AppImage-000000?style=for-the-badge&logo=linux&logoColor=white)](https://github.com/pooza/capsicum/releases/latest)

AppImage を [GitHub Releases](https://github.com/pooza/capsicum/releases/latest) から即時配布しています（v1.24 で初公開）。

#### かんたんインストール（推奨）

以下のワンライナーで、最新の AppImage をダウンロードして `~/Applications/` に配置し、アプリメニューへの登録（`.desktop` エントリ + アイコン）までを一括で行います（sudo 不要）。

```bash
curl -fsSL https://capsicum.shrieker.net/install.sh | bash
```

実行後、アプリメニューに「capsicum」が表示されます（出ない場合はログアウト → 再ログインでランチャーが更新されます）。AppImageLauncher を導入していない環境でも、これだけで GUI ランチャーから起動できます（v1.30 で追加、[#640](https://github.com/pooza/capsicum/issues/640)）。ダウンロードした AppImage は、GitHub Releases に載っている SHA-256 と照合してからインストールします（v2.12 で追加、[#1384](https://github.com/pooza/capsicum/issues/1384)）。

**AppImageLauncher とは併用しないでください。**AppImageLauncher は `~/Applications/` にある AppImage を見つけるたびにアプリメニューへ登録するため、ワンライナーが置くファイルもそれぞれ登録され、アプリメニューに「capsicum」がいくつも並びます。ワンライナーで導入した場合は、アプリメニューへの登録は済んでいるので AppImageLauncher は不要です。

#### うまくいかないとき

ワンライナーは、ダウンロードした AppImage が SHA-256 と合わなければ、何もインストールせずに止まります。止まったときは、原因の候補が表示されます。

- **curl / wget の設定ファイル**（`~/.curlrc`・`~/.wgetrc` など）。ここに書いたオプションは毎回のダウンロードに加わります。たとえば curl の `-i`（応答のヘッダーを中身に混ぜる）が入っていると、ダウンロードしたファイルが壊れます
- **プロキシ・証明書の環境変数**（`https_proxy` / `ALL_PROXY` / `CURL_CA_BUNDLE` など）。表示されるのは変数の名前だけで、値は表示しません
- どちらも見つからなければ、ネットワークか配布側の一時的な問題の可能性があります。時間をおいて試してください

設定を見直すか、下の「手動インストール」に切り替えてください。それでも進めたいときは `--force` を付けると、照合が合わなくても警告を出したうえでインストールします（AppImage として読めないほど壊れたファイルはインストールしません）。

```bash
curl -fsSL https://capsicum.shrieker.net/install.sh | bash -s -- --force
```

#### 手動インストール

ダウンロード済みの AppImage をそのまま起動するだけでも動作します。

```bash
chmod +x capsicum-*.AppImage
./capsicum-*.AppImage
```

手元の AppImage をメニューに登録したい場合は、インストールスクリプトにパスを渡します。

```bash
curl -fsSL https://capsicum.shrieker.net/install.sh -o install.sh
bash install.sh ./capsicum-*.AppImage
```

#### アンインストール

メニュー登録・アイコン・`~/Applications/` 配下の AppImage を削除します（アカウント情報・設定・ログは残ります）。

```bash
curl -fsSL https://capsicum.shrieker.net/uninstall.sh | bash
```

新しいバージョンが出ると capsicum 内で更新を検知してお知らせします（直配チャネル向けの新版通知、v1.30 で追加、[#641](https://github.com/pooza/capsicum/issues/641)）。

**日本語入力について**: ibus・fcitx5・uim の 3 つの経路とも動作確認済みです（Ubuntu 26.04 で `ibus-mozc` / `fcitx5-mozc` / `uim-mozc`。ibus は Debian 13 でも確認、fcitx5 は外部ユーザーからも動作報告をいただいています）。上記以外の組み合わせで動作しない場合は、ご報告ください。

## プラットフォーム別の現状

### ナウプレ

詳しくは [ナウプレについて](/now-playing) を参照してください。

## 通知

### WebSocketベースの通知

デスクトップ版では、アプリの起動中に各サーバーへ常時 WebSocket 接続し（Mastodon の `user` ストリーム / Misskey の `main` チャンネル）、届いた通知を OS のローカル通知（macOS の通知センター / Linux の libnotify / Windows のトースト）に表示します。
タイムラインを前面に出していなくても、ウィンドウを開いてさえいれば通知が届きます。この方式はサーバー標準の streaming API の上で動作するため、[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)の有無を問わず、ログイン中のすべてのアカウントで利用できます。

### プッシュ通知

macOS版 と Windows 版は、[プッシュ通知](/push-notification)にも対応します。

## 設計について

デスクトップ展開にあたっては、プラットフォーム分岐を増やさない方針で進めています。

- **UI の分岐軸はプラットフォームではなく画面幅**。iPad で広いウィンドウならデスクトップ風レイアウトに、デスクトップで狭めればモバイル風に切り替わります
- **OS 固有機能は抽象層を経由**。通知・バックグラウンドタスク・メディア選択は v1.23 でプラットフォーム抽象化レイヤを導入済み
- **OAuth はシステムブラウザ経由**（Linux / Windows）。`flutter_web_auth_2` の制約を回避しつつ、Bitwarden / 1Password 等のパスワードマネージャ統合も副次的に達成

詳細は [GitHub Milestones](https://github.com/pooza/capsicum/milestones) を参照してください。

---

[capsicum](/)
