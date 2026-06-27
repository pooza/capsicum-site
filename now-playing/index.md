---
title: ナウプレについて - capsicum
---

# ナウプレ

capsicum は、いま再生している曲を `#nowplaying` 付きの投稿としてワンアクションで作成できる「ナウプレ」機能を備えています。
capsicumのナウプレには、2 つの経路があります。

## 経路1. ナウプレ共有

Apple Music や Spotify など、音楽再生アプリの「共有」メニューから capsicum を選ぶ方式です。再生アプリ側が渡してくる曲名や URL を受け取り、投稿フォームに流し込みます。

- 対応: iOS / Android / macOS（macOS は Share Extension を同梱、v1.24〜）
- OS の共有機能を使うため、対応は共有シート / 共有インテントを持つプラットフォームに限られます。
- サーバー側に[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)が必要です。

## 経路2. ナウプレ取得

capsicum の投稿フォームにある ♪ ボタンを押すだけで、OS が把握している「いま再生中の曲」を取得して挿入します。
再生アプリに切り替えません。共有操作も不要です。

OS ごとに標準のメディア情報の仕組みを使って取得します。

| プラットフォーム | 仕組み | 状態 |
| --- | --- | --- |
| Linux | MPRIS（D-Bus。Spotify / VLC / Rhythmbox / Elisa など対応プレイヤーを横断） | v1.33 で対応 |
| Windows | SMTC（System Media Transport Controls） | v1.33 で対応 |
| iOS / macOS | Apple Music（再生中の曲を直接取得） | v1.37 で対応 |

再生中の曲が無いときは「現在再生中の曲がありません」と表示され、投稿は作られません。

> **Spotify について**: Linux / Windows では、上記の OS メディア連携（MPRIS / SMTC）が Spotify アプリの再生中の曲も拾えます。一方、全プラットフォーム横断の Spotify 専用連携（OAuth）は、Spotify の API 提供条件の都合により見送っています。

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

## プリセットサーバーでの強化

[プリセットサーバー](/preset-servers)（[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)導入済み）では、URL を持たない源（Linux MPRIS / Windows SMTC など）から取得した曲でも、サーバー側が曲名・アーティストを手がかりに**共有可能な URL を補完**します（v1.37〜、[#669](https://github.com/pooza/capsicum/issues/669)）。
これにより、デスクトップで取得したナウプレにも音楽サービスへのリンクが付きます。補完が無くても投稿自体は成立します。

---

[capsicum](/)
