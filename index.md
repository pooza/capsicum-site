---
title: capsicum
---

<img src="/logo.png" alt="capsicum" width="256" height="128">

# capsicum

Mastodon / Misskey 対応の Fediverse クライアントアプリです。コードの大半は [Claude Code](https://claude.ai/claude-code) によって書かれています。

capsicum が提案するのは、アプリ単体の体験ではなく、サーバーとの一体感です。[プリセットサーバー](/preset-servers)では、サーバーサイド拡張との連携により、アニメ実況支援をはじめとした独自機能が利用できます。この一体感こそが capsicum の存在意義です。

どなたでもお使いいただけますが、開発の優先順位は[プリセットサーバー](/preset-servers)のメンバーにとっての利便性が最優先です。外部サーバーのユーザーに対するサポートや、[プリセットサーバー](/preset-servers)で使用していないバージョン・フォークへの対応は保証しません。

## ダウンロード

[![Get it on Google Play](https://img.shields.io/badge/GET_IT_ON-Google_Play-000000?style=for-the-badge&logo=googleplay&logoColor=white)](https://play.google.com/store/apps/details?id=net.shrieker.capsicum)
[![Download on the App Store](https://img.shields.io/badge/Download_on_the-App_Store-000000?style=for-the-badge&logo=apple&logoColor=white)](https://apps.apple.com/jp/app/capsicum/id6760206608)
[![Download on the Mac App Store](https://img.shields.io/badge/Download_on_the-Mac_App_Store-000000?style=for-the-badge&logo=apple&logoColor=white)](https://apps.apple.com/jp/app/capsicum/id6760206608)
[![Linux AppImage](https://img.shields.io/badge/Linux-AppImage-000000?style=for-the-badge&logo=linux&logoColor=white)](/desktop#linux)
[![Get it from Microsoft](https://img.shields.io/badge/Get_it_from-Microsoft-000000?style=for-the-badge&logo=microsoft&logoColor=white)](https://apps.microsoft.com/detail/9np2gr7m2w6p)

## モロヘイヤ連携

capsicum の開発動機の中心にあるのは、[プリセットサーバー](/preset-servers)で運用している [mulukhiya-toot-proxy](https://github.com/pooza/mulukhiya-toot-proxy)（モロヘイヤ）への対応です。

モロヘイヤは利用者数の少ないサーバーサイド拡張であり、これに対応した既存のクライアントアプリは存在しません。それは利用者数を考えれば当然のことですが、自分にとっては最も欲しい機能です。capsicum は、まずその不足を埋めるために作られました。

モロヘイヤ導入済みサーバーでは、以下の拡張機能が自動的に有効になります。

- **エピソードブラウザ** — 放送中のアニメからエピソードを選んで実況投稿
- **タグセット** — 作品名・放送枠などのハッシュタグをワンタップで挿入
- **実況支援** — アニメ実況に特化した投稿フロー
- **メディアカタログ** — サーバーに投稿されたメディアを一覧・検索できるギャラリー機能（※サーバー側のバッチ処理の負荷が高く現状では実用性が低いと判断し、現在すべてのプリセットサーバーで本番運用を停止しています）
- **デフォルトハッシュタグ** — [プリセットサーバー](/preset-servers)では、サーバーが提供するハッシュタグが自動的に投稿に付与されます

## 主な機能

- **劇中ワードサジェスト**（v1.35〜） — アニメ実況などで IME の変換候補に出てこない専門用語（必殺技名・キャラクター名など）を、ひらがなの読みから検索して投稿フォームに挿入できます。辞書を用意した[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)導入サーバーで利用できる、実況の即時性を支える独自機能です
- **[ナウプレ](/now-playing)** — 聴いている曲を `#nowplaying` 付きの投稿としてワンアクションで作成。音楽アプリの「共有」から作るほか、デスクトップ（Linux / Windows、v1.33〜）では投稿フォームの ♪ ボタンから再生中の曲を直接取得できます
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

v1.18 で、Mastodon / Misskey サーバーが発行する Web Push を APNs / FCM に変換する専用の中継サーバーを経由するプッシュ通知方式に移行しました。従来のバックグラウンドポーリング方式と異なり、iOS でも実用的に通知が届きます。v1.20 では Misskey ネイティブのペイロード対応や、バックグラウンド / キル状態での通知内容の個別表示などを完成させました。Misskey は本来、サードパーティアプリからのプッシュ通知登録は制限されていますが、[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)導入済みサーバー（[ダイスキー](https://misskey.delmulin.com)等）では専用経路でプッシュ通知を受け取れます。

v1.34 では、デスクトップ版（macOS / Linux / Windows）でも通知を受け取れるようにしました。アプリの起動中に各サーバーへ WebSocket で接続し、届いた通知を OS のローカル通知に表示します（macOS ではあわせて APNs 経由のネイティブ push 通知にも対応）。

[プリセットサーバー](/preset-servers)のメンバーには無償で提供しますが、それ以外のサーバーのユーザーに対しては、インフラ維持費を賄うために有償での提供を予定しています。詳しくは[プッシュ通知について](/push-notification)をご覧ください。

## デスクトップ版について

iOS / Android のモバイル版に加え、macOS / Linux / Windows のデスクトップ版にも段階的に展開しています。

- **macOS** — Mac App Store で配信中。Universal Purchase により iOS / iPadOS と同一の App として提供しています
- **Linux** — AppImage を GitHub Releases から即時配布
- **Windows** — [Microsoft Store](https://apps.microsoft.com/detail/9np2gr7m2w6p) から配信中（v1.27 で公開）。証明書 import 不要でそのままインストールできます（GitHub Releases 経由の自己署名 MSIX 直配も残していますが、証明書登録が必要な上級者向けの補助です）

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

**v1.36.0**（2026-06-12） Android（Google Play）・macOS Mac App Store で公開済み、iOS App Store・[Windows Microsoft Store](https://apps.microsoft.com/detail/9np2gr7m2w6p)・Linux AppImage は順次公開中

v1.36 は、Misskey の**チャット**と**ページ**の続編機能を中心に、投げ銭（サポーター）を macOS にも広げたリリースです。Misskey チャットではメッセージへのリアクションとファイル添付に、ページでは「いいね」と『人気』セクションに対応しました。あわせて macOS の Mac App Store でもサポーター（投げ銭）を購入できるようになり、サポーター状態をサーバー側で保持することで、複数端末や再インストール後もサポーターであることを引き継げるようにしています。

Linux 版の導入はワンライナーで完結します。

```bash
curl -fsSL https://capsicum.shrieker.net/install.sh | bash
```

導入手順は [デスクトップ版について](/desktop) をご覧ください。

## ロードマップ

- [**v1.37**](https://github.com/pooza/capsicum/milestone/47) — [ナウプレ取得](/now-playing)を iOS / macOS の Apple Music へ横展開
- [**v1.38**](https://github.com/pooza/capsicum/milestone/48) — [ナウプレ取得](/now-playing)を Spotify 連携（OAuth 経由）へ拡大

v1.18〜v1.19 でプッシュ通知リレーを導入・ホットフィックスを経て実運用に乗せ、v1.20 では Misskey ネイティブペイロード対応・バックグラウンド / キル状態での通知内容の個別表示・中継サーバー側の観測性強化などを完了し、プッシュ通知機能を「完成」状態に仕上げました。v1.21 で macOS ネイティブビルドの土台が完成し、v1.22 で Misskey の新メッセージ機能に対応、v1.23 でデスクトップ展開のための通知・タスク・メディア抽象化を完了、v1.24 で Linux 版を初公開、v1.25 で Windows 版を初公開、v1.26 で番組表・エピソードブラウザからの Annict 感想投稿に対応、v1.27 で Windows の [Microsoft Store 公開達成](https://apps.microsoft.com/detail/9np2gr7m2w6p)とサポーターサブスクリプション（投げ銭）の導入を完了、v1.28 で Misskey のグループチャットに対応、v1.29 で[プリセットサーバー](/preset-servers)向けのお知らせ通知配信を実現、v1.30 で Linux / Windows の動画再生対応（`media_kit` 移行）とデスクトップ配布体験の補強を完了し、v1.31 でタイムライン上の各投稿へのタッチ操作の段階的有効化を実現、v1.32 でデスクトップ / パッケージング周りの構造整理（リファクタ集約）を完了し、**v1.33 でデスクトップ（Linux / Windows）の[ナウプレ取得](/now-playing)に対応**、**v1.34 でデスクトップ 3 OS の通知本配線（アプリ起動中の WebSocket streaming → OS のローカル通知 + macOS のネイティブ APNs）を完了**し、**v1.35 で投稿フォームのワードサジェスト（劇中ワードをひらがなの読みから引いて挿入）を実現**、**v1.36 で Misskey チャット / ページの続編機能（リアクション・ファイル添付・いいね・人気セクション）と投げ銭の macOS 横展開・サポーター状態のサーバー側保持を完了**しました。

これからは、[ナウプレ取得](/now-playing)を Apple Music（v1.37）・Spotify（v1.38）へと源を広げていきます。

なお、Linux 配布は **AppImage 単独**で運用します。Flathub への配信は一度準備しましたが断念しました。今後は AppImage の体験改善に集中します。

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
