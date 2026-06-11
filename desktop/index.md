---
title: デスクトップ版について - capsicum
---

# デスクトップ版

capsicum は iOS / Android のモバイル版に加え、macOS / Linux / Windows のデスクトップ版にも段階的に展開しています。動機は、iOS 版を Mac 上で実況用途に使って得た手応えです。

すべてのプラットフォームで、モバイル版と同じ Flutter コードベースから配信しています。UI はウィンドウ幅に応じて自動でレスポンシブに切り替わり、Finder / ファイラー起点のメディア添付、再生中の曲を投稿フォームに挿入する[ナウプレ取得](/now-playing)（Linux / Windows、v1.33〜）、共有メニューからの[ナウプレ共有](/now-playing)（macOS）、アプリ起動中の[通知](/push-notification)を OS のローカル通知に表示する仕組み（3 OS 共通、macOS はネイティブ push にも対応、v1.34〜）といったネイティブな体験を取り入れています。

## 配布チャネルとインストール

### macOS

[![Download on the Mac App Store](https://img.shields.io/badge/Download_on_the-Mac_App_Store-000000?style=for-the-badge&logo=apple&logoColor=white)](https://apps.apple.com/jp/app/capsicum/id6760206608)

**Mac App Store** から無償で配信中（v1.24 で初公開）。動作要件は macOS 11.5 以降。

Universal Purchase により iOS / iPadOS と同一の App として提供しています。同じ Apple ID で購入済みの方は、Mac でも追加費用なしでインストールできます（capsicum はそもそも無料ですが、購入履歴は共有されます）。

Apple Music などの「共有」メニューから capsicum を呼び出してナウプレ投稿を作成できる **Share Extension** も同梱しています。

### Linux

[![Linux AppImage](https://img.shields.io/badge/Linux-AppImage-000000?style=for-the-badge&logo=linux&logoColor=white)](https://github.com/pooza/capsicum/releases/latest)

**AppImage** を [GitHub Releases](https://github.com/pooza/capsicum/releases/latest) から即時配布しています（v1.24 で初公開）。**Flathub への配信は断念し、AppImage 単独運用に確定**しました。その分、ストアに頼らない導入体験を磨いています。

#### かんたんインストール（推奨）

以下のワンライナーで、最新の AppImage をダウンロードして `~/Applications/` に配置し、アプリメニューへの登録（`.desktop` エントリ + アイコン）までを一括で行います（sudo 不要・ユーザー領域のみ）。

```bash
curl -fsSL https://capsicum.shrieker.net/install.sh | bash
```

実行後、アプリメニューに「capsicum」が表示されます（出ない場合はログアウト → 再ログインでランチャーが更新されます）。AppImageLauncher を導入していない環境でも、これだけで GUI ランチャーから起動できます（v1.30 で追加、[#640](https://github.com/pooza/capsicum/issues/640)）。

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

**日本語入力について**: `ibus-mozc` 等の ibus 経路は動作確認済みです。`fcitx5` 経路も外部ユーザーから動作報告をいただいています。`uim` 用の immodule も同梱していますが、開発環境外のため **best-effort** とさせてください。動作しない場合は ibus か fcitx5 経由でご利用ください。

### Windows

[![Get it from Microsoft](https://img.shields.io/badge/Get_it_from-Microsoft-000000?style=for-the-badge&logo=microsoft&logoColor=white)](https://apps.microsoft.com/detail/9np2gr7m2w6p)

**Microsoft Store** から無償で配信中（v1.25 で初回配布開始、v1.27 で Store 公開達成）。証明書 import の手間なく、一般の Windows ユーザーがそのままインストールできます。

動作要件:

- Windows 10 (1809 以降) / Windows 11 x64

#### GitHub Releases 経由の自己署名 MSIX 直配（補助・上級者向け）

一般のユーザーには、証明書 import の不要な **Microsoft Store** からの導入を推奨します。Store を利用できない環境など限られたケース向けに、[GitHub Releases](https://github.com/pooza/capsicum/releases/latest) からの自己署名 MSIX 直配も残しています。自己署名のため、インストール前に証明書を信頼ストアへ登録する必要があります。

1. Release アセットから 2 ファイルをダウンロード
   - `capsicum.msix` — アプリ本体
   - `capsicum-signing.cer` — 自己署名証明書
2. **PowerShell を管理者として実行**し、ダウンロードフォルダへ `cd`
3. 証明書を信頼ストア（Trusted People / LocalMachine）に import

   ```powershell
   Import-Certificate -FilePath .\capsicum-signing.cer -CertStoreLocation Cert:\LocalMachine\TrustedPeople
   ```

4. MSIX をインストール

   ```powershell
   Add-AppxPackage -Path .\capsicum.msix
   ```

5. スタートメニューから `capsicum` を起動

アンインストールは「設定 → アプリ」から。証明書も消す場合は `Cert:\LocalMachine\TrustedPeople` から該当エントリを削除します。証明書 import は初回のみで、以降の更新では不要です（[詳細手順](https://github.com/pooza/capsicum/blob/main/packaging/windows/INSTALL.md)）。

なお Store 経由の配布は Microsoft 側で再署名されるため、独自のコード署名証明書はこの直配補助ルートにしか関係しません。

## プラットフォーム別の現状

| | 配布 | 通知 | ナウプレ取得 | ナウプレ共有 | 動画再生 |
| --- | --- | --- | --- | --- | --- |
| macOS | Mac App Store | **v1.34 で対応（共通経路 [#569](https://github.com/pooza/capsicum/issues/569) + ネイティブ APNs [#468](https://github.com/pooza/capsicum/issues/468)）** | [v1.37 で対応予定（Apple Music #668）](https://github.com/pooza/capsicum/issues/668) | Share Extension | ○ |
| Linux | AppImage | **v1.34 で対応（3 OS 共通経路 [#569](https://github.com/pooza/capsicum/issues/569)）** | **v1.33 で対応（MPRIS [#466](https://github.com/pooza/capsicum/issues/466)）** | 対応外 | ○ (v1.30 で [media_kit 移行 #492](https://github.com/pooza/capsicum/issues/492)) |
| Windows | Microsoft Store | **v1.34 で対応（共通経路 [#569](https://github.com/pooza/capsicum/issues/569)）**。ネイティブ WNS は保留 ([#474](https://github.com/pooza/capsicum/issues/474)) | **v1.33 で対応（SMTC [#484](https://github.com/pooza/capsicum/issues/484)）** | 対応外 | ○ (v1.30 で [media_kit 移行 #492](https://github.com/pooza/capsicum/issues/492)) |

「ナウプレ取得」は投稿フォームの ♪ ボタンから、OS が把握している再生中の曲を直接取得して挿入する機能です（v1.33 でデスクトップに追加）。「ナウプレ共有」は他アプリの「共有」メニューから capsicum を呼び出して投稿する機能で、OS の共有 API が必要なため現状は macOS のみで完成しています。詳しくは [ナウプレについて](/now-playing) を参照してください。

## 設計について

デスクトップ展開にあたっては、プラットフォーム分岐を増やさない方針で進めています。

- **UI の分岐軸はプラットフォームではなく画面幅**。iPad で広いウィンドウならデスクトップ風レイアウトに、デスクトップで狭めればモバイル風に切り替わります
- **OS 固有機能は抽象層を経由**。通知・バックグラウンドタスク・メディア選択は v1.23 でプラットフォーム抽象化レイヤを導入済み
- **OAuth はシステムブラウザ経由**（Linux / Windows）。`flutter_web_auth_2` の制約を回避しつつ、Bitwarden / 1Password 等のパスワードマネージャ統合も副次的に達成

## ロードマップ（デスクトップ関連）

- **v1.34** — **デスクトップ 3 OS の通知本配線** — Mastodon `user` stream / Misskey `main` channel を WebSocket で受けて OS のローカル通知に流す共通経路（[#569](https://github.com/pooza/capsicum/issues/569)）と、macOS のネイティブ push 通知（APNs 経由、[#468](https://github.com/pooza/capsicum/issues/468)）を同テーマで実装
- **v1.36** — Misskey チャット / ページの続編機能と、投げ銭（サポーター）の macOS / Windows 横展開
- **v1.37** — [ナウプレ取得](/now-playing)を iOS / macOS の Apple Music へ横展開（[#668](https://github.com/pooza/capsicum/issues/668)）
- **v1.38** — [ナウプレ取得](/now-playing)を Spotify 連携（OAuth 経由）へ拡大（[#570](https://github.com/pooza/capsicum/issues/570)）

直近の達成: v1.27 で Windows の Microsoft Store 公開（Partner Center 手動 publish ルート、2026-05-20 審査通過）、v1.28 で Misskey のグループチャット対応、v1.29 で[プリセットサーバー](/preset-servers)向けのお知らせ通知配信。Linux 配布は Flathub 提出を断念し AppImage 単独運用に確定（2026-05-29、[#604](https://github.com/pooza/capsicum/issues/604)）。v1.30 で Linux / Windows の動画再生に対応（[media_kit 移行 #492](https://github.com/pooza/capsicum/issues/492)）し、あわせて Linux AppImage のデスクトップ統合インストール（[#640](https://github.com/pooza/capsicum/issues/640)）・直配チャネルの新版通知（[#641](https://github.com/pooza/capsicum/issues/641)）・ドラッグ＆ドロップ添付などのデスクトップ UX を強化。v1.32 でデスクトップ / パッケージング周りの構造整理（リファクタ集約）を完了。**v1.33 で[ナウプレ取得](/now-playing)（再生中の曲を投稿フォームに挿入）に対応しました — Linux は MPRIS（[#466](https://github.com/pooza/capsicum/issues/466)）、Windows は SMTC（[#484](https://github.com/pooza/capsicum/issues/484)）。**整形はクライアント側で行うため、モロヘイヤ未導入のサーバーでも動作します。

詳細は [GitHub Milestones](https://github.com/pooza/capsicum/milestones) を参照してください。
