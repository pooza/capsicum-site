---
title: プッシュ通知について - capsicum
---

# プッシュ通知について

## 概要

capsicum v1.18 より、Mastodon / Misskey サーバーからのプッシュ通知に対応しました。開発者が運営するリレーサーバーを経由して、リアルタイムの通知を端末に届けます。
v1.20 では、Misskey ネイティブの通知ペイロード対応、バックグラウンド / キル状態での通知内容の個別表示など残課題を消化し、プッシュ通知機能を「完成」状態に仕上げました。

## 利用対象

プッシュ通知は、capsicum の[プリセットサーバー](/preset-servers)にアカウントをお持ちの方に無償で提供します。capsicum は本来[プリセットサーバー](/preset-servers)のユーザーに向けて開発されたアプリで、プッシュ通知もこの方針に沿い、[プリセットサーバー](/preset-servers)のアカウントをひとつでも登録しているユーザーを対象とします。[プリセットサーバー](/preset-servers)以外のユーザーに対しては、将来的に有償での提供を予定しています。

現在[プリセットサーバー](/preset-servers)にアカウントをお持ちでない方も、サーバーに登録すれば対象になります。プリセットサーバーの一覧と登録方法は[プリセットサーバーについて](/preset-servers)をご覧ください。

## Mastodon と Misskey の違い

Mastodon はサードパーティアプリからのプッシュ通知登録を公式にサポートしており、capsicum からそのまま利用できます。

Misskey には本来、プッシュ通知の登録 API がサードパーティアプリから行えないという制約があります。capsicum では v1.20 より、[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)導入済みサーバー（[ダイスキー](https://misskey.delmulin.com)・[きゅあすきー](https://mk.precure.fun)等）において、[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)側のプロキシエンドポイント経由でこの制約を回避し、Misskey でもプッシュ通知を受け取れるようにしました。[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)未導入の Misskey サーバーや、[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)が古いバージョンのサーバーでは有効化できない場合があります。

## デスクトップ版の通知（v1.34〜、Windows ネイティブは v1.40〜）

上記のリレー方式は、iOS / Android のモバイル版で、アプリを終了していても通知を届けるための仕組みです。v1.34 では、[デスクトップ版](/desktop)（macOS / Linux / Windows）にも通知を導入しました。

デスクトップ版では、アプリの起動中に各サーバーへ常時 WebSocket 接続し（Mastodon の `user` ストリーム / Misskey の `main` チャンネル）、届いた通知を OS のローカル通知（macOS の通知センター / Linux の libnotify / Windows のトースト）に表示します。タイムラインを前面に出していなくても、ウィンドウを開いてさえいれば通知が届きます。この方式はサーバー標準の streaming API の上で動作するため、[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)の有無を問わず、ログイン中のすべてのアカウントで利用できます。

macOS ではこれに加えて、モバイルと同じリレー経由の APNs によるネイティブ push 通知に対応しています。**v1.40 では Windows のネイティブ通知（WNS）にも対応しました** — リレーサーバーから Windows 通知サービス（WNS）経由で通知を送り、アプリを完全に終了している間でも、バックグラウンドタスクが受信・復号してトースト通知を表示します。あわせて、ウィンドウを閉じてもトレイに常駐して通知を受け続ける「常駐」と、ログイン時の自動起動にも対応しました（詳しくは[デスクトップ版について](/desktop)、いずれも Windows で先行・macOS / Linux は後続）。

## プライバシー

プッシュ通知に関する情報の取り扱いについては、[プライバシーポリシー](/privacy-policy)をご確認ください。

---

[capsicum](/)
