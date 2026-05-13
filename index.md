---
title: capsicum
---

<img src="/logo.png" alt="capsicum" width="256" height="128">

# capsicum

Mastodon / Misskey 対応の Fediverse クライアントアプリです。コードの大半は [Claude Code](https://claude.ai/claude-code) によって書かれています。

capsicum が提案するのは、アプリ単体の体験ではなく、サーバーとの一体感です。開発者自身が運営するサーバーでは、サーバーサイド拡張との連携により、アニメ実況支援をはじめとした独自機能が利用できます。この一体感こそが capsicum の存在意義です。

どなたでもお使いいただけますが、開発の優先順位は開発者のサーバーのメンバーにとっての利便性が最優先です。外部サーバーのユーザーに対するサポートや、開発者のサーバーで使用していないバージョン・フォークへの対応は保証しません。

## モロヘイヤ連携

capsicum の開発動機の中心にあるのは、自分のサーバーで運用している [mulukhiya-toot-proxy](https://github.com/pooza/mulukhiya-toot-proxy)（モロヘイヤ）への対応です。

モロヘイヤは利用者数の少ないサーバーサイド拡張であり、これに対応した既存のクライアントアプリは存在しません。それは利用者数を考えれば当然のことですが、自分にとっては最も欲しい機能です。capsicum は、まずその不足を埋めるために作られました。

モロヘイヤ導入済みサーバーでは、以下の拡張機能が自動的に有効になります。

- **エピソードブラウザ** — 放送中のアニメからエピソードを選んで実況投稿
- **タグセット** — 作品名・放送枠などのハッシュタグをワンタップで挿入
- **実況支援** — アニメ実況に特化した投稿フロー
- **メディアカタログ** — サーバーに投稿されたメディアを一覧・検索できるギャラリー機能
- **デフォルトハッシュタグ** — プリセットサーバーでは、サーバーが提供するハッシュタグが自動的に投稿に付与されます

## 主な機能

- **ナウプレ共有** — Apple Music や Spotify など音楽アプリの「共有」から capsicum を選ぶだけで、`#nowplaying` 付きの投稿を作成。聴いている曲をワンアクションでタイムラインに流せます
- 複数サーバー・アカウントの切り替え
- 引用投稿の表示・作成（Mastodon / Misskey）
- Misskey リアクション・クリップ・ドライブ・チャンネル・Misskey Play
- アンケート作成・投票
- 予約投稿・投稿の翻訳・言語選択
- 絵文字ピッカー・カスタム絵文字・MFM 描画
- ハッシュタグフォロー・タブ固定
- テーマカラー・フォントサイズ・表示カスタマイズ（絶対時間・画像ぼかし・投稿前確認）
- リアルタイム更新（WebSocket ストリーミング）

## 開発の優先順位について

capsicum は個人開発のアプリです。開発の最優先事項は、作者自身が運用するサーバーと、プリセットに含まれるサーバーのメンバーにとっての使い勝手です。

それ以外のサーバーのユーザーにもお使いいただけますが、機能要望やバグ報告の優先順位は、上記のコミュニティに直接関わるものが先になります。ご了承ください。

## プッシュ通知について

v1.18 で、Mastodon / Misskey サーバーが発行する Web Push を APNs / FCM に変換する専用の中継サーバーを経由するプッシュ通知方式に移行しました。従来のバックグラウンドポーリング方式と異なり、iOS でも実用的に通知が届きます。v1.20 では Misskey ネイティブのペイロード対応や、バックグラウンド / キル状態での通知内容の個別表示などを完成させました。Misskey はサードパーティアプリからのプッシュ通知登録に上流側の制約がありますが、モロヘイヤ導入済みサーバー（ダイスキー等）では専用経路でプッシュ通知を受け取れます。

プリセットに含まれるサーバーのメンバーには無償で提供しますが、それ以外のサーバーのユーザーに対しては、インフラ維持費を賄うために有償での提供を予定しています。詳しくは[プッシュ通知について](/push-notification)をご覧ください。

## サーバー互換性の方針

capsicum は最新の Mastodon / Misskey の API に対して実装しています。古いバージョンのサーバーに対する互換処理は行いません。

ソフトウェアの更新を怠っているサーバーは、セキュリティや安定性の面でも信頼性に欠けると考えています。capsicum がそうしたサーバーへの対応に開発リソースを割くことはありません。

フォーク（Mastodon / Misskey の派生ソフトウェア）についても、本家 API との互換性を維持するのはフォーク側の責任です。capsicum 側でフォーク固有の対応は行いません。

## 開発について

capsicum のコードの大半は [Claude Code](https://claude.ai/claude-code)（Anthropic の AI コーディングツール）によって書かれています。設計の出発点は、アーカイブされた Fediverse クライアント [Kaiteki](https://github.com/Kaiteki-Fedi/Kaiteki) の Adapter パターンとモデル構造です。

ライセンスは [AGPL-3.0](https://www.gnu.org/licenses/agpl-3.0.html) です。

## ダウンロード

[![Get it on Google Play](https://img.shields.io/badge/GET_IT_ON-Google_Play-000000?style=for-the-badge&logo=googleplay&logoColor=white)](https://play.google.com/store/apps/details?id=net.shrieker.capsicum)
[![Download on the App Store](https://img.shields.io/badge/Download_on_the-App_Store-000000?style=for-the-badge&logo=apple&logoColor=white)](https://apps.apple.com/jp/app/capsicum/id6760206608)
[![Download on the Mac App Store](https://img.shields.io/badge/Download_on_the-Mac_App_Store-000000?style=for-the-badge&logo=apple&logoColor=white)](https://apps.apple.com/jp/app/capsicum/id6760206608)
[![Linux AppImage](https://img.shields.io/badge/Linux-AppImage-000000?style=for-the-badge&logo=linux&logoColor=white)](https://github.com/pooza/capsicum/releases/latest)
[![Windows MSIX](https://img.shields.io/badge/Windows-MSIX-000000?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/pooza/capsicum/releases/latest)

## 最新リリース

**v1.25.0**（2026-05-12） Android 製品版・iOS App Store・macOS Mac App Store すべて公開済み、Linux 版は AppImage を継続配布中、**Windows 版を初公開**

v1.25 では、デスクトップ展開の第3段階の続きとして **Windows 版を初公開** しました。Microsoft Store 公開は法人化対応待ちのため、当面は GitHub Releases 経由の **自己署名 MSIX 直配** で配信します。インストールには PowerShell から自己署名証明書を信頼ストアに import する手順が必要です（[詳細はインストール手順](https://github.com/pooza/capsicum/blob/main/packaging/windows/INSTALL.md)）。中期的には OV コード署名証明書を取得し、SmartScreen 通過する形式に格上げ予定です。

あわせて v1.22 で導入した **Misskey メッセージ機能の改善**（レンダリング要素の反映、動線改善、細かなバグ修正）と、v1.24.x で重ねた Linux / macOS の followup を取り込みました。

## デスクトップ版について

iOS / Android のモバイル版に加え、macOS / Linux / Windows のデスクトップ版にも段階的に展開しています。

- **macOS** — Mac App Store で配信中。Universal Purchase により iOS / iPadOS と同一の App として提供しています
- **Linux** — AppImage を GitHub Releases から即時配布、Flathub への配信も準備中
- **Windows** — v1.25 で初公開、GitHub Releases 経由の自己署名 MSIX 直配

各プラットフォームの導入方法・既知の制約・ロードマップは [デスクトップ版について](/desktop) を参照してください。

## ロードマップ

- [**v1.26**](https://github.com/pooza/capsicum/milestone/32) — v1.25 / v1.24 review followup の集約 + Windows 仕上げ（OV cert / アイコン / ウィンドウ位置記録）
- [**v1.27**](https://github.com/pooza/capsicum/milestone/33) — サポーターサブスクリプション（投げ銭）— 大更新の単独配置
- [**v1.28**](https://github.com/pooza/capsicum/milestone/34) — Misskey グループチャット対応 + ナウプレ取得の抽象化（Linux MPRIS）
- [**v1.29**](https://github.com/pooza/capsicum/milestone/37) — お知らせ通知（プリセットサーバー向け push 配信、モロヘイヤ + capsicum-relay 拡張）— 大更新の単独配置
- [**v1.30**](https://github.com/pooza/capsicum/milestone/38) — v1.26 リファクタ overflow + macOS push 通知の本配線

v1.18〜v1.19 でプッシュ通知リレーを導入・ホットフィックスを経て実運用に乗せ、v1.20 では Misskey ネイティブペイロード対応・バックグラウンド / キル状態での通知内容の個別表示・中継サーバー側の観測性強化などを完了し、プッシュ通知機能を「完成」状態に仕上げました。v1.21 で macOS ネイティブビルドの土台が完成し、v1.22 で Misskey の新メッセージ機能に対応、v1.23 でデスクトップ展開のための通知・タスク・メディア抽象化を完了、v1.24 で Linux 版を初公開、v1.25 で Windows 版を初公開しました。

これからは、v1.27 で投げ銭型サポーターサブスクリプション、v1.28 で Misskey グループチャットと NowPlaying 抽象化、v1.29 でプリセットサーバー向けのお知らせ通知配信、v1.30 で macOS push 通知の本配線を予定しています。

詳細は [GitHub Milestones](https://github.com/pooza/capsicum/milestones) をご覧ください。

## コミュニティ

capsicum についてのご意見・ご要望・不具合報告は、[PieFed コミュニティ](https://pf.korako.me/c/capsicum)で受け付けています。

Fediverse 上の任意のアカウントから `@capsicum@pf.korako.me` にメンションすると、コミュニティに投稿が届きます。[mulukhiya-toot-proxy](https://github.com/pooza/mulukhiya-toot-proxy)（モロヘイヤ）導入済みサーバーでは、このメンションに対して自動的に `#capsicum` ハッシュタグが付与されます。

## リンク

- 開発・運営: [有限会社ビーショック](https://www.b-shock.co.jp)
- 開発者: [@pooza@mstdn.b-shock.org](https://mstdn.b-shock.org/deck/@pooza)
- [GitHub](https://github.com/pooza/capsicum)
- [お問い合わせ](https://contact.capsicum.shrieker.net)
- [FAQ](/faq)
- [利用規約](/terms)
- [プライバシーポリシー](/privacy-policy)
- [子どもの安全基準](/child-safety-standards)
