---
title: capsicum
---

<img src="/logo.png" alt="capsicum" width="256" height="128">

# capsicum

## capsicumとは？

Mastodon / Misskey 対応の Fediverse クライアントアプリです。

capsicum が提案するのは、アプリ単体の体験ではなく、サーバーとの一体感です。[プリセットサーバー](/preset-servers)では、サーバーサイド拡張との連携により、アニメ実況支援をはじめとした独自機能が利用できます。この一体感こそが capsicum の存在意義です。

どなたでもお使いいただけますが、開発の優先順位は[プリセットサーバー](/preset-servers)のメンバーにとっての利便性が最優先です。外部サーバーのユーザーに対するサポートや、[プリセットサーバー](/preset-servers)で使用していないバージョン・フォークへの対応は保証しません。

コードの大半は [Claude Code](https://claude.ai/claude-code) によって書かれています。

[![Get it on Google Play](https://img.shields.io/badge/GET_IT_ON-Google_Play-000000?style=for-the-badge&logo=googleplay&logoColor=white)](https://play.google.com/store/apps/details?id=net.shrieker.capsicum)
[![Download on the App Store](https://img.shields.io/badge/Download_on_the-App_Store-000000?style=for-the-badge&logo=apple&logoColor=white)](https://apps.apple.com/jp/app/capsicum/id6760206608)
[![Download on the Mac App Store](https://img.shields.io/badge/Download_on_the-Mac_App_Store-000000?style=for-the-badge&logo=apple&logoColor=white)](https://apps.apple.com/jp/app/capsicum/id6760206608)
[![Linux AppImage](https://img.shields.io/badge/Linux-AppImage-000000?style=for-the-badge&logo=linux&logoColor=white)](/desktop#linux)
[![Get it from Microsoft](https://img.shields.io/badge/Get_it_from-Microsoft-000000?style=for-the-badge&logo=microsoft&logoColor=white)](https://apps.microsoft.com/detail/9np2gr7m2w6p)

- [プリセットサーバー](/preset-servers)
- [プッシュ通知](/push-notification)
- [ナウプレ](/now-playing)
- [デスクトップ版](/desktop)

## モロヘイヤ連携

capsicum の開発動機の中心にあるのは、[プリセットサーバー](/preset-servers)で運用している [mulukhiya-toot-proxy](https://github.com/pooza/mulukhiya-toot-proxy)（以下、「モロヘイヤ」）への対応です。

モロヘイヤは利用者数の少ないサーバーサイド拡張であり、これに対応した既存のクライアントアプリは存在しません。それは利用者数を考えれば当然のことですが、自分にとっては最も欲しい機能です。capsicum は、まずその不足を埋めるために作られました。

## 特徴的な機能

### Mastodon/Misskeyの本来機能

日常的に使用する基本機能は概ね完備しています。

- 予約投稿
  - MastodonではWebUIから投稿できませんが、capsicumを使えば投稿できます。
- 引用投稿
  - Mastodon ・ Misskey 両対応
- 絵文字ピッカー
  - カスタム絵文字・Unicode絵文字共に、キーワード検索に対応
- 複数ハッシュタグのAND検索タイムライン（Mastodon「上級者」WebUIの機能）
- 削除して再編集
  - 元の投稿の設定（返信先・公開範囲・「ローカルのみ」・言語・投票・引用許可）を引き継いで書き直せます。
- 一覧と管理
  - ブロック・ミュート、フォローリクエスト、フォロー中のハッシュタグ、お気に入り、引用など、これまで WebUI を開く必要のあった一覧をアプリ内で確認・操作できます（一部は Mastodon のみ）。
- 設定のバックアップ
  - 表示・動作・履歴などの設定と、使用中のアカウントの一覧をファイルに書き出し、別の端末で読み込めます。スマートフォンでも利用できます。
  - タブの構成・ピン留めしたハッシュタグ・リストの並び・絵文字パレット・アカウントの色といった、アカウントごとの設定も引き継げます。
  - **ログイン情報（トークン）は含みません。** 読み込んだアカウントは「未接続」として一覧に並び、タップしてログインし直すと使えるようになります。
- 相手と投稿の状態が分かる表示
  - 引っ越し済み・凍結・サイレンスされたアカウントに印が出ます。フォローしているのに投稿が届かない相手を、プロフィールを開いた時点で見分けられます。
  - 編集された投稿には鉛筆のアイコンが出ます。
- [プッシュ通知](/push-notification)

### 独自機能

以下は[プリセットサーバー](/preset-servers)等、[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)導入済みサーバーで有効になる主要な機能です。

- 文末ハッシュタグの管理
  - 「削除してタグづけ」「お気に入りタグ」「タグセット」など、投稿の文末に付けるハッシュタグを素早く編集・付け替えできます。アニメ実況での作品名・キャラ名のタグ付けを支える、capsicum の中心的な機能です。
- 劇中ワードサジェスト
  - 管理人が前もって準備したアニメ作品について、その作品特有の固有名詞を高速に入力できます。
- エピソードブラウザ
  - アニメ作品のサブタイトル一覧を表示したり、その回での実況を行ったりできます。
- [ナウプレ](/now-playing)（NowPlaying共有）
  - Apple Music や Spotify など、再生アプリの「共有」から capsicum を選択
  - 投稿画面の「♪」アイコンをタップ
  - モロヘイヤのないサーバーでも、一部の機能は利用可
- 画像トリミング・回転・文字のせ・スタンプ
  - 添付する画像に、カスタム絵文字をスタンプとして重ねられます。
- 絵文字ピッカー
  - MisskeyのWebUIで設定した絵文字パレットを、ワンタッチで同期します。
- 猫化（isCat）
  - Misskey上で猫として設定されたアカウントは、そのサーバーの外でも猫として振る舞います。
- 他、各種実況支援

## 開発の優先順位について

capsicum は個人開発のアプリです。開発の最優先事項は、[プリセットサーバー](/preset-servers)のメンバーにとっての使い勝手です。

それ以外のサーバーのユーザーにもお使いいただけますが、機能要望やバグ報告の優先順位は、上記のコミュニティに直接関わるものが先になります。ご了承ください。

## サーバー互換性

capsicum は最新の Mastodon / Misskey の API に対して実装しています。古いバージョンのサーバーに対する互換処理は行いません。

ソフトウェアの更新を怠っているサーバーは、セキュリティや安定性の面でも信頼性に欠けると考えています。capsicum がそうしたサーバーへの対応に開発リソースを割くことはありません。

フォーク（Mastodon / Misskey の派生ソフトウェア）についても、本家 API との互換性を維持するのはフォーク側の責任です。capsicum 側でフォーク固有の対応は行いません。

## 開発について

- capsicum のコードの大半は [Claude Code](https://claude.ai/claude-code)によって書かれています。
- Fediverse クライアント [Kaiteki](https://github.com/Kaiteki-Fedi/Kaiteki) の Adapter パターンとモデル構造を参考にしています。
  - 開発は終了しており、アーカイブ済み。
- ライセンスは [AGPL-3.0](https://www.gnu.org/licenses/agpl-3.0.html) 

## 最新リリース

**v1.65.0**（2026-09-18） 全プラットフォームで公開済みです。

読む側の実害を潰したリリースです。引っ越し・凍結されたアカウントや編集された投稿が、それと分からないまま表示されていた問題を直しました。

- **引っ越し・凍結・サイレンスされたアカウントに印が出るようになりました。** フォローしているのに投稿が届かない相手が、これまでは何も無かったかのように普通のプロフィールとして表示されていました。Mastodon / Misskey の両方に対応し、Mastodon では引っ越し先へ辿れます。
- **編集された投稿に鉛筆のアイコンが出るようになりました。** 他の人が編集した投稿を、編集されたと知らないまま読むことがなくなります。デスクトップではアイコンにマウスを乗せると編集時刻が表示されます。
- **本文の文字数の数え方を Mastodon に揃えました。** URL は長さに関わらず 23 文字として数え、絵文字などは見た目どおり 1 文字として数えます。これまでは長い URL を 1 本貼るだけで、実際より大幅に多く数えていました。
- **設定のバックアップに、アカウントごとの設定が含まれるようになりました。** タブの構成・ピン留めしたハッシュタグ・リストの並び・絵文字パレット・アカウントの色です。これまでは別の端末へ移すと、アカウントは一覧に並ぶのにこれらが真っさらになっていました。
- **Misskey**: ブーストされた投稿の中身にワードミュートが効いていなかった問題を直しました。
- **Linux**: キーリング（gnome-keyring など）が応答しないとき、アカウントの削除や再ログインで画面が固まる問題を直しました。
- ログインまわりの不具合（同じアカウントが一覧に 2 件並ぶ・承認待ちの案内が届かない）をあわせて直しています。

### ダウンロード

[![Get it on Google Play](https://img.shields.io/badge/GET_IT_ON-Google_Play-000000?style=for-the-badge&logo=googleplay&logoColor=white)](https://play.google.com/store/apps/details?id=net.shrieker.capsicum)
[![Download on the App Store](https://img.shields.io/badge/Download_on_the-App_Store-000000?style=for-the-badge&logo=apple&logoColor=white)](https://apps.apple.com/jp/app/capsicum/id6760206608)
[![Download on the Mac App Store](https://img.shields.io/badge/Download_on_the-Mac_App_Store-000000?style=for-the-badge&logo=apple&logoColor=white)](https://apps.apple.com/jp/app/capsicum/id6760206608)
[![Linux AppImage](https://img.shields.io/badge/Linux-AppImage-000000?style=for-the-badge&logo=linux&logoColor=white)](/desktop#linux)
[![Get it from Microsoft](https://img.shields.io/badge/Get_it_from-Microsoft-000000?style=for-the-badge&logo=microsoft&logoColor=white)](https://apps.microsoft.com/detail/9np2gr7m2w6p)


### Linux 版の導入

ワンライナーで完結します。

```bash
curl -fsSL https://capsicum.shrieker.net/install.sh | bash
```

詳細な導入手順は [デスクトップ版について](/desktop) をご覧ください。


## ロードマップ

直近では信頼性・使い勝手の改善に継続的に取り組んでいます。詳細は [GitHub Milestones](https://github.com/pooza/capsicum/milestones) をご覧ください。

### 次のメジャーバージョン（2.0）

次のメジャーバージョンは設計を終え、実装を進めています。以下の 3 つを柱として予定しています。**提供時期は未定です。**

- **デッキ表示（マルチカラム）**
  - タイムラインを列として横に並べて表示します。列ごとにアカウントを割り当てられるので、別のアカウント・別のサーバーのタイムラインを並べて眺められます。
- **添付画像のレイヤー編集**
  - 画像に重ねた文字やスタンプをレイヤーとして扱い、重ね順の変更やレイヤーごとの編集ができるようにします。
- **外部サーバー向けのプッシュ通知（有償）**
  - [プッシュ通知](/push-notification)は現在、[プリセットサーバー](/preset-servers)のユーザーにのみ無償で提供しています。これを外部サーバーのユーザーにも有償で開放する予定です。
  - **プリセットサーバーのユーザーは、これまでどおり無償です。** 料金は未定です。

いずれも設計と実装に時間がかかるため、その間も 1.x 系のリリース（不具合の修正・ご要望への対応）は並行して続けます。

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
