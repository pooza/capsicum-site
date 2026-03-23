---
title: capsicum
---

<img src="/logo.png" alt="capsicum" width="256" height="128">

# capsicum

Mastodon / Misskey 対応の Fediverse クライアントアプリです。iPhone / iPad / Android に対応しています。

## 特徴

- 複数のサーバー・アカウントを登録して切り替え
- タイムライン閲覧（ホーム / ローカル / 連合 / リスト / ハッシュタグ）と無限スクロール
- テキスト・メディア・投票付き投稿（公開範囲選択、CW 対応、絵文字ピッカー）
- リプライ・ブースト・お気に入り・ブックマーク
- 投稿削除・削除して再編集
- Misskey リアクション（絵文字ピッカー付き）
- リアルタイム更新（WebSocket ストリーミング）
- MFM / HTML / カスタム絵文字 / プレビューカードの描画
- ハッシュタグ・メンションのリンク化とプロフィール遷移
- 引用投稿の表示
- 通知一覧・検索・プロフィール表示・編集
- リスト管理（作成・名前変更・削除・メンバー管理）
- フォロー / フォロワー一覧・ミュート / ブロック操作
- ピン留め投稿・タイムライン既読位置の保存と復元
- NSFW ぼかし・ワードフィルタ
- [mulukhiya-toot-proxy](https://github.com/pooza/mulukhiya-toot-proxy)（モロヘイヤ）連携 — タグセット・エピソードブラウザ等

## モロヘイヤ連携について

capsicum の開発動機の中心にあるのは、自分のサーバーで運用している [mulukhiya-toot-proxy](https://github.com/pooza/mulukhiya-toot-proxy)（モロヘイヤ）への対応です。

モロヘイヤは利用者数の少ないサーバーサイド拡張であり、これに対応した既存のクライアントアプリは存在しません。それは利用者数を考えれば当然のことですが、自分にとっては最も欲しい機能です。capsicum は、まずその不足を埋めるために作られました。

モロヘイヤ導入済みサーバーでは、タグセットや実況支援、エピソードブラウザなどの拡張機能が自動的に有効になります。

## 開発の優先順位について

capsicum は個人開発のアプリです。開発の最優先事項は、作者自身が運用するサーバーと、プリセットに含まれるサーバーのメンバーにとっての使い勝手です。

それ以外のサーバーのユーザーにもお使いいただけますが、機能要望やバグ報告の優先順位は、上記のコミュニティに直接関わるものが先になります。ご了承ください。

## 通知サーバーについて

プッシュ通知の実装には、Mastodon / Misskey の Web Push を APNs / FCM に変換する中継サーバーが必要です。将来的にこのサーバーを立てる予定はあります。

プリセットに含まれるサーバーのメンバーには無償で提供しますが、それ以外のサーバーのユーザーに対しては、インフラ維持費を賄うために有償での提供を予定しています。

## サーバー互換性の方針

capsicum は最新の Mastodon / Misskey の API に対して実装しています。古いバージョンのサーバーに対する互換処理は行いません。

ソフトウェアの更新を怠っているサーバーは、セキュリティや安定性の面でも信頼性に欠けると考えています。capsicum がそうしたサーバーへの対応に開発リソースを割くことはありません。

フォーク（Mastodon / Misskey の派生ソフトウェア）についても、本家 API との互換性を維持するのはフォーク側の責任です。capsicum 側でフォーク固有の対応は行いません。

## 開発について

capsicum のコードの大半は [Claude Code](https://claude.ai/claude-code)（Anthropic の AI コーディングツール）によって書かれています。設計の出発点は、アーカイブされた Fediverse クライアント [Kaiteki](https://github.com/Kaiteki-Fedi/Kaiteki) の Adapter パターンとモデル構造です。

ライセンスは [AGPL-3.0](https://www.gnu.org/licenses/agpl-3.0.html) です。

## ロードマップ

- [**v1.7**](https://github.com/pooza/capsicum/milestone/10) — 追加機能（通知統合一覧・Misskey ドライブ・メディアカタログ 等）
- [**v1.6**](https://github.com/pooza/capsicum/milestone/9) — ユーザー要望の継続消化（翻訳・ハッシュタグフォロー・Misskey Play/ギャラリー 等）
- [**v1.5**](https://github.com/pooza/capsicum/milestone/7) — ユーザー要望の消化（簡易投稿バー・rel=me バッジ・Misskey クリップ/絵文字パレット 等）
- [**v1.4**](https://github.com/pooza/capsicum/milestone/6) — UX 改善（テーマカラー・タブ順序カスタマイズ・フォントサイズ・URL 短縮表示 等）
- [**v1.3**](https://github.com/pooza/capsicum/milestone/5) — 補完的機能（引用操作・ピン留め・インスタンスティッカー 等）

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
