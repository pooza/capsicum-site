---
title: capsicum
---

<img src="/logo.png" alt="capsicum" width="256" height="128">

# capsicum

Mastodon / Misskey 対応の Fediverse クライアントアプリです。コードの大半は [Claude Code](https://claude.ai/claude-code) によって書かれています。

capsicum が提案するのは、アプリ単体の体験ではなく、サーバーとの一体感です。[開発者自身が運営するサーバー](/preset-servers)では、サーバーサイド拡張との連携により、アニメ実況支援をはじめとした独自機能が利用できます。この一体感こそが capsicum の存在意義です。

どなたでもお使いいただけますが、開発の優先順位は開発者のサーバーのメンバーにとっての利便性が最優先です。外部サーバーのユーザーに対するサポートや、開発者のサーバーで使用していないバージョン・フォークへの対応は保証しません。

## ダウンロード

[![Get it on Google Play](https://img.shields.io/badge/GET_IT_ON-Google_Play-000000?style=for-the-badge&logo=googleplay&logoColor=white)](https://play.google.com/store/apps/details?id=net.shrieker.capsicum)
[![Download on the App Store](https://img.shields.io/badge/Download_on_the-App_Store-000000?style=for-the-badge&logo=apple&logoColor=white)](https://apps.apple.com/jp/app/capsicum/id6760206608)
[![Download on the Mac App Store](https://img.shields.io/badge/Download_on_the-Mac_App_Store-000000?style=for-the-badge&logo=apple&logoColor=white)](https://apps.apple.com/jp/app/capsicum/id6760206608)
[![Linux AppImage](https://img.shields.io/badge/Linux-AppImage-000000?style=for-the-badge&logo=linux&logoColor=white)](https://github.com/pooza/capsicum/releases/latest)
[![Get it from Microsoft](https://img.shields.io/badge/Get_it_from-Microsoft-000000?style=for-the-badge&logo=microsoft&logoColor=white)](https://apps.microsoft.com/detail/9np2gr7m2w6p)

## モロヘイヤ連携

capsicum の開発動機の中心にあるのは、[自分のサーバー](/preset-servers)で運用している [mulukhiya-toot-proxy](https://github.com/pooza/mulukhiya-toot-proxy)（モロヘイヤ）への対応です。

モロヘイヤは利用者数の少ないサーバーサイド拡張であり、これに対応した既存のクライアントアプリは存在しません。それは利用者数を考えれば当然のことですが、自分にとっては最も欲しい機能です。capsicum は、まずその不足を埋めるために作られました。

モロヘイヤ導入済みサーバーでは、以下の拡張機能が自動的に有効になります。

- **エピソードブラウザ** — 放送中のアニメからエピソードを選んで実況投稿
- **タグセット** — 作品名・放送枠などのハッシュタグをワンタップで挿入
- **実況支援** — アニメ実況に特化した投稿フロー
- **メディアカタログ** — サーバーに投稿されたメディアを一覧・検索できるギャラリー機能
- **デフォルトハッシュタグ** — [プリセットサーバー](/preset-servers)では、サーバーが提供するハッシュタグが自動的に投稿に付与されます

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

## プッシュ通知について

v1.18 で、Mastodon / Misskey サーバーが発行する Web Push を APNs / FCM に変換する専用の中継サーバーを経由するプッシュ通知方式に移行しました。従来のバックグラウンドポーリング方式と異なり、iOS でも実用的に通知が届きます。v1.20 では Misskey ネイティブのペイロード対応や、バックグラウンド / キル状態での通知内容の個別表示などを完成させました。Misskey はサードパーティアプリからのプッシュ通知登録に上流側の制約がありますが、[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)導入済みサーバー（ダイスキー等）では専用経路でプッシュ通知を受け取れます。

プリセットに含まれるサーバーのメンバーには無償で提供しますが、それ以外のサーバーのユーザーに対しては、インフラ維持費を賄うために有償での提供を予定しています。詳しくは[プッシュ通知について](/push-notification)をご覧ください。

## デスクトップ版について

iOS / Android のモバイル版に加え、macOS / Linux / Windows のデスクトップ版にも段階的に展開しています。

- **macOS** — Mac App Store で配信中。Universal Purchase により iOS / iPadOS と同一の App として提供しています
- **Linux** — AppImage を GitHub Releases から即時配布、Flathub への配信も準備中
- **Windows** — [Microsoft Store](https://apps.microsoft.com/detail/9np2gr7m2w6p) から配信中（v1.27 で公開）。先行配布・上級者向けには GitHub Releases 経由の自己署名 MSIX 直配も継続

各プラットフォームの導入方法・既知の制約・ロードマップは [デスクトップ版について](/desktop) を参照してください。

## 開発の優先順位について

capsicum は個人開発のアプリです。開発の最優先事項は、[プリセットサーバー](/preset-servers)のメンバーにとっての使い勝手です。

それ以外のサーバーのユーザーにもお使いいただけますが、機能要望やバグ報告の優先順位は、上記のコミュニティに直接関わるものが先になります。ご了承ください。

## サーバー互換性の方針

capsicum は最新の Mastodon / Misskey の API に対して実装しています。古いバージョンのサーバーに対する互換処理は行いません。

ソフトウェアの更新を怠っているサーバーは、セキュリティや安定性の面でも信頼性に欠けると考えています。capsicum がそうしたサーバーへの対応に開発リソースを割くことはありません。

フォーク（Mastodon / Misskey の派生ソフトウェア）についても、本家 API との互換性を維持するのはフォーク側の責任です。capsicum 側でフォーク固有の対応は行いません。

## 開発について

capsicum のコードの大半は [Claude Code](https://claude.ai/claude-code)（Anthropic の AI コーディングツール）によって書かれています。設計の出発点は、アーカイブされた Fediverse クライアント [Kaiteki](https://github.com/Kaiteki-Fedi/Kaiteki) の Adapter パターンとモデル構造です。

ライセンスは [AGPL-3.0](https://www.gnu.org/licenses/agpl-3.0.html) です。

## 最新リリース

**v1.27.0**（2026-05-22） Android 製品版・iOS App Store・Linux AppImage・Windows MSIX 自己署名直配は公開済み、macOS Mac App Store と Windows Microsoft Store は審査提出済み

v1.27 の主目的機能は、**サポーターサブスクリプション（投げ銭）** です。iOS / Android で 3 段階の投げ銭（¥100 / ¥500 / ¥800）を実装しました。**機能差別化はなく**、購入いただいた方には装飾としてのサポーターバッジが付くのみです。capsicum をご利用いただいているメンバーからの「機能差別化なしでよいので投げ銭させてほしい」という声に応える形で導入しました。

加えて、Windows の [Microsoft Store](https://apps.microsoft.com/detail/9np2gr7m2w6p) を Partner Center の Web UI 手動 publish ルートで **初回公開達成しました**（2026-05-20 審査通過）。証明書 import なしで一般の Windows ユーザーがそのままインストールできます。先行配布や証明書 import を厭わない上級ユーザー向けには、GitHub Releases 経由の **自己署名 MSIX 直配** も継続しています（[インストール手順](https://github.com/pooza/capsicum/blob/main/packaging/windows/INSTALL.md)）。

スワイプによるカラム移動（[#573](https://github.com/pooza/capsicum/issues/573)）も v1.30 から前倒しで取り込みました。投げ銭の購入導線は iOS / Android のみで、デスクトップ版（macOS / Windows）には含めていません（Linux は技術的に課金を提供できません）。

## ロードマップ

- [**v1.28**](https://github.com/pooza/capsicum/milestone/34) — Misskey グループチャット対応 — 大更新の単独配置。Misskey テーマで Pages（ページ機能）の読み取り対応・ドライブの複数選択一括移動を同梱
- [**v1.29**](https://github.com/pooza/capsicum/milestone/37) — お知らせ通知（[プリセットサーバー](/preset-servers)向け push 配信、[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy) + capsicum-relay 拡張）— 大更新の単独配置
- [**v1.30**](https://github.com/pooza/capsicum/milestone/38) — macOS push 通知の本配線、デスクトップ 3 OS 共通の通知経路、Linux / Windows での動画再生改善、ユーザー要望の UX 改善（ドラッグ＆ドロップ添付・メディアダウンロード等）
- [**v1.31**](https://github.com/pooza/capsicum/milestone/39) — タイムライン上の各投稿へのタッチ操作の段階的有効化 — 大更新の単独配置
- [**v1.32**](https://github.com/pooza/capsicum/milestone/40) — デスクトップ / パッケージング周りの構造整理（リファクタ集約）
- [**v1.33**](https://github.com/pooza/capsicum/milestone/41) — プレイヤー横断ナウプレ取得（Linux MPRIS / Windows SMTC / Spotify 連携）

v1.18〜v1.19 でプッシュ通知リレーを導入・ホットフィックスを経て実運用に乗せ、v1.20 では Misskey ネイティブペイロード対応・バックグラウンド / キル状態での通知内容の個別表示・中継サーバー側の観測性強化などを完了し、プッシュ通知機能を「完成」状態に仕上げました。v1.21 で macOS ネイティブビルドの土台が完成し、v1.22 で Misskey の新メッセージ機能に対応、v1.23 でデスクトップ展開のための通知・タスク・メディア抽象化を完了、v1.24 で Linux 版を初公開、v1.25 で Windows 版を初公開、v1.26 で番組表・エピソードブラウザからの Annict 感想投稿に対応、**v1.27 で Windows の [Microsoft Store 公開達成](https://apps.microsoft.com/detail/9np2gr7m2w6p)とサポーターサブスクリプション（投げ銭）の導入を完了**しました。

これからは、v1.28 で Misskey グループチャット、v1.29 で[プリセットサーバー](/preset-servers)向けのお知らせ通知配信、v1.30 で macOS push 通知の本配線とデスクトップの通知・動画・UX 改善を予定しています。その先では、タイムラインへのタッチ操作の段階的有効化（v1.31）、プレイヤー横断のナウプレ取得（v1.33）にも取り組みます。

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
- [特定商取引法に基づく表記](/tokushoho)
- [子どもの安全基準](/child-safety-standards)
