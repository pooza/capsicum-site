---
title: ナウプレについて - capsicum
---

# ナウプレ（今聴いている曲の投稿）

capsicum は、いま再生している曲を `#nowplaying` 付きの投稿としてワンアクションで作成できる「ナウプレ」機能を備えています。アニメ実況と同じノリで、BGM や作業中の曲をタイムラインに流せます。

ナウプレには **2 つの経路**があります。源（どこから曲情報を得るか）が違うだけで、最終的に作られる投稿は同じ形式です。

## 1. 共有から作る（共有経路）

Apple Music や Spotify などの音楽アプリの**「共有」メニュー**から capsicum を選ぶ方式です。音楽アプリ側が渡してくる曲名や URL を受け取り、投稿フォームに流し込みます。

- **対応**: iOS / Android / macOS（macOS は Share Extension を同梱、v1.24〜）
- OS の共有機能を使うため、対応は共有シート / 共有インテントを持つプラットフォームに限られます。

## 2. 再生中の曲を取得する（取得経路 / v1.33〜）

音楽アプリに切り替えず、capsicum の投稿フォームにある **♪ ボタン**を押すだけで、OS が把握している「いま再生中の曲」を取得して挿入します。共有シートを開く必要がありません。

OS ごとに標準のメディア情報の仕組みを使って取得します。

| プラットフォーム | 仕組み | 状態 |
| --- | --- | --- |
| Linux | MPRIS（D-Bus。Spotify / VLC / Rhythmbox / Elisa など対応プレイヤーを横断） | v1.33 で対応 |
| Windows | SMTC（System Media Transport Controls） | v1.33 で対応 |
| iOS / macOS | Apple Music（再生中の曲を直接取得） | [v1.37 で対応](https://github.com/pooza/capsicum/issues/668) |
| 各 OS | Spotify（OAuth 連携で再生中の曲を取得） | [v1.38 で対応予定](https://github.com/pooza/capsicum/issues/570) |

再生中の曲が無いときは「現在再生中の曲がありません」と表示され、投稿は作られません。

## 投稿の体裁

取得した曲情報は、capsicum 側で次のような複数行テキストに整形して本文へ挿入します。

```text
Title: シュビドゥビ☆スイーツタイム
Album: スイート☆エチュード☆アラモード
Artist: 宮本佳那子
#nowplaying
```

- 取れた項目（Title / Album / Artist）だけを並べます。
- 共有可能な URL（Spotify のトラック URL 等）が得られた場合は `#nowplaying` 行に続けて載せ、SNS 側でリンクカードとして展開されます。
- 整形は **capsicum 側（クライアント）で行う**ため、モロヘイヤ未導入のサーバーでもそのまま動作します。挿入後は投稿前に自由に編集できます。

## プリセットサーバーでの強化（任意）

[プリセットサーバー](/preset-servers)（[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)導入済み）では、URL を持たない源（Linux MPRIS / Windows SMTC など）から取得した曲でも、サーバー側が曲名・アーティストを手がかりに**共有可能な URL を補完**します（v1.37〜、[#669](https://github.com/pooza/capsicum/issues/669)）。これにより、デスクトップで取得したナウプレにも音楽サービスへのリンクが付きます。補完が無くても投稿自体は成立します。

## 関連

- [デスクトップ版について](/desktop)
- [GitHub Milestones](https://github.com/pooza/capsicum/milestones)
