---
title: デスクトップ版について - capsicum
---

# デスクトップ版

capsicum は iOS / Android のモバイル版に加え、macOS / Linux / Windows のデスクトップ版にも段階的に展開しています。動機は、iOS 版を Mac 上で実況用途に使って得た手応えです。

すべてのプラットフォームで、モバイル版と同じ Flutter コードベースから配信しています。UI はウィンドウ幅に応じて自動でレスポンシブに切り替わり、Finder / ファイラー起点のメディア添付、ナウプレ共有（macOS）といったネイティブな体験を取り入れています。

## 配布チャネルとインストール

### macOS

[![Download on the Mac App Store](https://img.shields.io/badge/Download_on_the-Mac_App_Store-000000?style=for-the-badge&logo=apple&logoColor=white)](https://apps.apple.com/jp/app/capsicum/id6760206608)

**Mac App Store** から無償で配信中（v1.24 で初公開）。動作要件は macOS 11.5 以降。

Universal Purchase により iOS / iPadOS と同一の App として提供しています。同じ Apple ID で購入済みの方は、Mac でも追加費用なしでインストールできます（capsicum はそもそも無料ですが、購入履歴は共有されます）。

Apple Music などの「共有」メニューから capsicum を呼び出してナウプレ投稿を作成できる **Share Extension** も同梱しています。

### Linux

[![Linux AppImage](https://img.shields.io/badge/Linux-AppImage-000000?style=for-the-badge&logo=linux&logoColor=white)](https://github.com/pooza/capsicum/releases/latest)

**AppImage** を [GitHub Releases](https://github.com/pooza/capsicum/releases/latest) から即時配布しています（v1.24 で初公開）。ダウンロード後、実行権限を付与して起動するだけで動作します。

```bash
chmod +x capsicum-*.AppImage
./capsicum-*.AppImage
```

**Flathub への配信は断念しました**。今後は AppImage 単独運用に方針を切り替え、 AppImage の体験改善（[アプリ一覧への統合インストールスクリプト](https://github.com/pooza/capsicum/issues/640)・[新版通知](https://github.com/pooza/capsicum/issues/641)）に注力します。

**日本語入力について**: `ibus-mozc` 等の ibus 経路は動作確認済みです。`fcitx5` 経路も外部ユーザーから動作報告をいただいています。`uim` 用の immodule も同梱していますが、開発環境外のため **best-effort** とさせてください。動作しない場合は ibus か fcitx5 経由でご利用ください。

### Windows

[![Get it from Microsoft](https://img.shields.io/badge/Get_it_from-Microsoft-000000?style=for-the-badge&logo=microsoft&logoColor=white)](https://apps.microsoft.com/detail/9np2gr7m2w6p)

**Microsoft Store** から無償で配信中（v1.25 で初回配布開始、v1.27 で Store 公開達成）。証明書 import の手間なく、一般の Windows ユーザーがそのままインストールできます。

動作要件:

- Windows 10 (1809 以降) / Windows 11 x64

#### GitHub Releases 経由の自己署名 MSIX 直配（補助・上級者向け）

Store publish 完了前の先行検証や、証明書 import を厭わないユーザー向けに、[GitHub Releases](https://github.com/pooza/capsicum/releases/latest) からの自己署名 MSIX 直配も継続しています。インストール時に PowerShell の管理者実行で自己署名証明書を信頼ストアに import する必要があります（詳細な手順は [packaging/windows/INSTALL.md](https://github.com/pooza/capsicum/blob/main/packaging/windows/INSTALL.md)）。

コード署名証明書の取得（[#534](https://github.com/pooza/capsicum/issues/534)）は、Microsoft Store 公開達成により当面不要となっています（Store 経由は MS 側で再署名されるため、自己署名のまま submit 可）。

## プラットフォーム別の現状

| | 配布 | 通知 | ナウプレ共有 | 動画再生 |
| --- | --- | --- | --- | --- |
| macOS | Mac App Store | v1.34 で対応予定（共通経路 [#569](https://github.com/pooza/capsicum/issues/569) + ネイティブ [#468](https://github.com/pooza/capsicum/issues/468)） | Share Extension | ○ |
| Linux | AppImage | v1.34 で対応予定（3 OS 共通経路 [#569](https://github.com/pooza/capsicum/issues/569)） | 対応外 | △ ([#492](https://github.com/pooza/capsicum/issues/492)、v1.30 で改善予定) |
| Windows | Microsoft Store + MSIX 自己署名直配 | v1.34 で対応予定（共通経路 [#569](https://github.com/pooza/capsicum/issues/569)）。ネイティブ WNS は保留 ([#474](https://github.com/pooza/capsicum/issues/474)) | 対応外 | △ ([#492](https://github.com/pooza/capsicum/issues/492)、v1.30 で改善予定) |

「ナウプレ共有」は他アプリの「共有」メニューから capsicum を呼び出して投稿する機能です。OS の共有 API が必要なため、現状は macOS のみで完成しています。

## 設計について

デスクトップ展開にあたっては、プラットフォーム分岐を増やさない方針で進めています。

- **UI の分岐軸はプラットフォームではなく画面幅**。iPad で広いウィンドウならデスクトップ風レイアウトに、デスクトップで狭めればモバイル風に切り替わります
- **OS 固有機能は抽象層を経由**。通知・バックグラウンドタスク・メディア選択は v1.23 でプラットフォーム抽象化レイヤを導入済み
- **OAuth はシステムブラウザ経由**（Linux / Windows）。`flutter_web_auth_2` の制約を回避しつつ、Bitwarden / 1Password 等のパスワードマネージャ統合も副次的に達成

## ロードマップ（デスクトップ関連）

- **v1.30** — **Linux / Windows での動画再生対応**（[`video_player` → `media_kit` 移行 #492](https://github.com/pooza/capsicum/issues/492)）が主役。Linux AppImage 配布の体験補強（[アプリ一覧への統合インストール #640](https://github.com/pooza/capsicum/issues/640)・[新版通知 #641](https://github.com/pooza/capsicum/issues/641)）、ドラッグ＆ドロップ添付などの UX 改善
- **v1.32** — デスクトップ / パッケージング周りの構造整理（リファクタ集約）
- **v1.33** — プレイヤー横断ナウプレ取得（Linux MPRIS / Windows SMTC / Spotify 連携）
- **v1.34** — **デスクトップ 3 OS の通知本配線** — Mastodon `user` stream / Misskey `main` channel を WebSocket で受けて OS のローカル通知に流す共通経路（[#569](https://github.com/pooza/capsicum/issues/569)）と、macOS のネイティブ push 通知（APNs 経由、[#468](https://github.com/pooza/capsicum/issues/468)）を同テーマで実装

直近の達成: v1.27 で Windows の Microsoft Store 公開（Partner Center 手動 publish ルート、2026-05-20 審査通過）、v1.28 で Misskey のグループチャット対応、v1.29 で[プリセットサーバー](/preset-servers)向けのお知らせ通知配信。Linux 配布は Flathub 提出を断念し AppImage 単独運用に確定（2026-05-29、[#604](https://github.com/pooza/capsicum/issues/604)）。

詳細は [GitHub Milestones](https://github.com/pooza/capsicum/milestones) を参照してください。
