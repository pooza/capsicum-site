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
- [FAQ](/faq)

## モロヘイヤ連携

capsicum の開発動機の中心にあるのは、[プリセットサーバー](/preset-servers)で運用している [mulukhiya-toot-proxy](https://github.com/pooza/mulukhiya-toot-proxy)（以下、「モロヘイヤ」）への対応です。

モロヘイヤは利用者数の少ないサーバーサイド拡張であり、これに対応した既存のクライアントアプリは存在しません。それは利用者数を考えれば当然のことですが、自分にとっては最も欲しい機能です。capsicum は、まずその不足を埋めるために作られました。

## 特徴的な機能

### デッキ表示（マルチカラム）

v2.0 より、タイムラインを列として横に並べて表示できます。

- ホーム・ローカル・ハッシュタグ・リスト・通知・検索・スレッド・プロフィールなどを、好きな順に並べられます。
- 列ごとにアカウントを割り当てられるので、別のアカウント・別のサーバーのタイムラインを並べて眺められます。
- スマートフォンの画面幅でも利用できます。列は横にスワイプして送るほか、列の一覧から直接移動できます。

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
- 画像トリミング・回転・レイヤー編集
  - 添付する画像に、文字・カスタム絵文字のスタンプ・端末の画像を重ねられます。
  - v2.0 より、重ねたものをレイヤーとして扱えます。位置・大きさ・回転・不透明度・重ね順を後から編集でき、下書きにも残ります。
- 絵文字ピッカー
  - MisskeyのWebUIで設定した絵文字パレットを、ワンタッチで同期します。
- 猫化（isCat）
  - Misskey上で猫として設定されたアカウントは、そのサーバーの外でも猫として振る舞います。
- 設定のバックアップ
  - 表示・動作・履歴などの設定と、使用中のアカウントの一覧をファイルに書き出し、別の端末で読み込めます。スマートフォンでも利用できます。
  - タブの構成・ピン留めしたハッシュタグ・リストの並び・絵文字パレット・アカウントの色といった、アカウントごとの設定も引き継げます。
  - **ログイン情報（トークン）は含みません。** 読み込んだアカウントは「未接続」として一覧に並び、タップしてログインし直すと使えるようになります。
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

**v2.0.1**（2026-10-08） iOS・Android・Windows・Linux で公開済みです。macOS は審査中で、通り次第公開されます。

2.0.0 の公開直後に見つかった不具合の修正版です。圏外が続いたあとデスクトップで通知が出なくなる問題、Windows で「サポート」の入口が出ない問題、通知の一覧が丸ごとエラーになることがある問題などを直しました。

2.0 はメジャーアップデートで、次の 3 つを加えました。

- **デッキ表示（マルチカラム）**: タイムライン・通知・リスト・検索などを、列として横に並べられます。列ごとに別のアカウントを割り当てられるので、複数のサーバーをひとつの画面で追えます。従来のタブ表示とは、いつでも切り替えられます。
- **プリセットサーバー以外へのプッシュ通知**: [プリセットサーバー](/preset-servers)以外のサーバーでも、月額の利用権をご購入いただくとプッシュ通知を受け取れます。プリセットサーバーをお使いの方は、これまでどおり無償です。詳しくは[プッシュ通知について](/push-notification)をご覧ください。
- **添付画像のレイヤー編集**: 画像に重ねた文字・スタンプ・画像をレイヤーとして扱えます。重ね順・表示と非表示・不透明度を変えられ、あとから編集し直せます。

そのほかの主な変更です。

- 同じ投稿への通知を、ひとつにまとめて表示するようになりました。
- 投稿画面の下のアイコン列を、畳んだり隠したりできるようになりました。
- **Mastodon**: 投稿の既定（公開範囲・言語など）を、サーバーの設定から読むようになりました。プロフィールに掲載するハッシュタグにも対応しています。
- **Linux / Windows**: ブラウザが前回のタブを復元する設定になっていると、ログインに失敗することがある問題を直しました。

すべての変更は GitHub のリリースページ（[v2.0.0](https://github.com/pooza/capsicum/releases/tag/v2.0.0) / [v2.0.1](https://github.com/pooza/capsicum/releases/tag/v2.0.1)）にあります。

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

v2.0 で、予告していた 3 つの柱（デッキ表示・添付画像のレイヤー編集・外部サーバー向けのプッシュ通知）を提供しました。今後は 2.x 系で、不具合の修正・ご要望への対応と、Mastodon / Misskey の機能のうちまだ capsicum から使えないものの追加を続けます。

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
