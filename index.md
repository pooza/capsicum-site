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

現在の capsicum はバックグラウンドポーリングによるローカル通知方式ですが、iOS ではバックグラウンド通知が事実上機能していないことが確認されています。

v1.18 で、Mastodon / Misskey の Web Push を APNs / FCM に変換する専用の中継サーバーによるプッシュ通知に移行します。

プリセットに含まれるサーバーのメンバーには無償で提供しますが、それ以外のサーバーのユーザーに対しては、インフラ維持費を賄うために有償での提供を予定しています。詳しくは[プッシュ通知について](/push-notification)をご覧ください。

## サーバー互換性の方針

capsicum は最新の Mastodon / Misskey の API に対して実装しています。古いバージョンのサーバーに対する互換処理は行いません。

ソフトウェアの更新を怠っているサーバーは、セキュリティや安定性の面でも信頼性に欠けると考えています。capsicum がそうしたサーバーへの対応に開発リソースを割くことはありません。

フォーク（Mastodon / Misskey の派生ソフトウェア）についても、本家 API との互換性を維持するのはフォーク側の責任です。capsicum 側でフォーク固有の対応は行いません。

## 開発について

capsicum のコードの大半は [Claude Code](https://claude.ai/claude-code)（Anthropic の AI コーディングツール）によって書かれています。設計の出発点は、アーカイブされた Fediverse クライアント [Kaiteki](https://github.com/Kaiteki-Fedi/Kaiteki) の Adapter パターンとモデル構造です。

ライセンスは [AGPL-3.0](https://www.gnu.org/licenses/agpl-3.0.html) です。

## ダウンロード

<a href="https://play.google.com/store/apps/details?id=net.shrieker.capsicum"><img alt="Google Play で手に入れよう" src="https://play.google.com/intl/ja/badges/static/images/badges/ja_badge_web_generic.png" height="80"></a>
<a href="https://apps.apple.com/jp/app/capsicum/id6760206608"><img alt="Download on the App Store" src="https://developer.apple.com/assets/elements/badges/download-on-the-app-store.svg" height="80"></a>

## 最新リリース

**v1.18.0**（2026-04-21）Google Play 公開済み・App Store 審査中

## ロードマップ

- [**v1.19**](https://github.com/pooza/capsicum/milestone/23) — プッシュ通知の完成（ペイロード復号・耐性強化・登録失敗可視化等）
- [**v1.20**](https://github.com/pooza/capsicum/milestone/24) — macOS ネイティブビルド化（デスクトップ対応 第1段階）
- [**v1.21**](https://github.com/pooza/capsicum/milestone/25) — 通知モデル再設計 + 抽象化層（デスクトップ対応 第2段階）
- [**v1.22**](https://github.com/pooza/capsicum/milestone/26) — Linux / Windows 対応（デスクトップ対応 第3段階）

v1.18 でプッシュ通知リレーの基盤を導入しましたが、実運用で明らかになった残課題を v1.19 で完成させます。その後、v1.20 以降はデスクトップ環境への段階的な展開が主軸になります。iOS 版を Mac 上で実況用途に使い手応えを得たことが動機です。macOS ネイティブ化からスタートし、通知モデルの再設計を経て、Linux / Windows に広げていきます。

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
