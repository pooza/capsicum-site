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

## 最新リリース

**v1.24.1**（2026-05-10） Android 製品版公開済み・iOS / macOS は v1.24.0 のまま継続・Linux は AppImage を即時配布

v1.24 では、デスクトップ展開の第3段階として **Linux 版を初公開** しました。AppImage を [GitHub Releases](https://github.com/pooza/capsicum/releases) から即時ダウンロードできるほか、Flathub への配信も並行して進めています。macOS には、Apple Music などの「共有」メニューから capsicum へ投稿できる Share Extension を追加しました。

v1.24.1 は、Linux AppImage 版で日本語入力（IBus / mozc 等）が効かない不具合の hotfix です。Android / iOS / macOS は v1.24.0 のまま継続しています。

macOS 版は v1.23 から iOS と同じバージョン番号で Mac App Store の審査を順次提出しています。承認されしだい、Universal Purchase により iOS と同一の App として配信を開始します。

## デスクトップ版について

iOS / Android のモバイル版に加え、macOS / Linux / Windows のデスクトップ版にも段階的に展開しています。動機は、iOS 版を Mac 上で実況用途に使って得た手応えです。

- **macOS** — v1.21 でネイティブビルドの土台を完成させ、v1.23 で通知・抽象化層、v1.24 で実機検証と Share Extension まで完了しました。Mac App Store の審査結果しだいで、Universal Purchase により iOS と同一の App として提供します
- **Linux** — v1.24 で初公開しました。AppImage を [GitHub Releases](https://github.com/pooza/capsicum/releases) から即時配布しているほか、[Flathub](https://flathub.org/) への配信も準備中です
- **Windows** — 当初予定していた Microsoft Store 経路が個人開発者アカウントの仕様上の制約で進められず、方針を変更しました。v1.26 で GitHub Releases 経由の MSIX 形式直配により再開予定です。中期的にはコード署名証明書を取得して SmartScreen 警告のないインストールを目指します

デスクトップでも、ナウプレ共有や Finder 起点のメディア添付など、ネイティブな体験を活かした運用を目指しています。

## ロードマップ

- [**v1.25**](https://github.com/pooza/capsicum/milestone/31) — Misskey メッセージ機能の改善 + デスクトップ品質改善（v1.24 リリース前レビュー followup の集約）
- [**v1.26**](https://github.com/pooza/capsicum/milestone/32) — Windows 版の自己署名 MSIX 直配・観測性強化・desktop プッシュ通知の方針決定 ほか
- [**v1.27**](https://github.com/pooza/capsicum/milestone/33) — サポーターサブスクリプション（投げ銭）
- [**v1.28**](https://github.com/pooza/capsicum/milestone/34) — Misskey グループチャット対応 + ナウプレ取得の抽象化（Linux MPRIS）

v1.18〜v1.19 でプッシュ通知リレーを導入・ホットフィックスを経て実運用に乗せ、v1.20 では Misskey ネイティブペイロード対応・バックグラウンド / キル状態での通知内容の個別表示・中継サーバー側の観測性強化などを完了し、プッシュ通知機能を「完成」状態に仕上げました。v1.21 で macOS ネイティブビルドの土台が完成し、v1.22 で Misskey の新メッセージ機能に対応、v1.23 でデスクトップ展開のための通知・タスク・メディア抽象化を完了、v1.24 で Linux 版を初公開しました（macOS 実機検証と Share Extension も同時に完成）。

これからは、v1.25 で v1.22 で導入した Misskey メッセージ機能の改善（レンダリング要素の反映、動線改善、細かなバグ修正）を集約します。v1.26 で Windows 版の配布を MSIX 直配で再開する予定です。v1.27 では、ユーザー要望をきっかけに検討に入った投げ銭型サポーターサブスクリプションの実装を予定しています。

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
