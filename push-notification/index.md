---
title: プッシュ通知 - capsicum
---

# プッシュ通知

## 概要

capsicum v1.18 より、Mastodon / Misskey サーバーからのプッシュ通知に対応しました。開発者が運営するリレーサーバーを経由して、リアルタイムの通知を端末に届けます。

## 利用対象

プッシュ通知は、capsicum の[プリセットサーバー](/preset-servers)にアカウントをお持ちの方に無償で提供します。capsicum は本来[プリセットサーバー](/preset-servers)のユーザーに向けて開発されたアプリで、プッシュ通知もこの方針に沿い、[プリセットサーバー](/preset-servers)のアカウントをひとつでも登録しているユーザーを対象とします。[プリセットサーバー](/preset-servers)以外のユーザーに対しては、将来的に有償での提供を予定しています。

現在[プリセットサーバー](/preset-servers)にアカウントをお持ちでない方も、サーバーに登録すれば対象になります。プリセットサーバーの一覧と登録方法は[プリセットサーバーについて](/preset-servers)をご覧ください。

## Mastodon と Misskey の違い

Mastodon はサードパーティアプリからのプッシュ通知登録を公式にサポートしており、capsicum からそのまま利用できます。

Misskey には本来、プッシュ通知の登録 API がサードパーティアプリから行えないという制約があります。
capsicum では v1.20 より、[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)導入済みサーバー（[ダイスキー](https://misskey.delmulin.com)・[きゅあすきー](https://mk.precure.fun)等）において、[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)側のプロキシエンドポイント経由でこの制約を回避し、Misskey でもプッシュ通知を受け取れるようにしました。[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)未導入の Misskey サーバーや、[モロヘイヤ](https://github.com/pooza/mulukhiya-toot-proxy)が古いバージョンのサーバーでは有効化できない場合があります。

## デスクトップ版

### WebSocketベース通知

[デスクトップ版](/desktop) はプッシュ通知だけでなく、WebSocketベースの通知機能に対応します。

### macOS版

WebSocketベース通知だけでなく、リレー経由の APNs によるネイティブプッシュ通知（iOSと同じ）にも限定的に対応しています。

### Windows版

WebSocketベース通知だけでなく、ネイティブ通知（WNS）にも対応しました。
リレーサーバーから Windows 通知サービス（WNS）経由で通知を送り、アプリを完全に終了している間でも、バックグラウンドタスクが受信・復号してトースト通知を表示します。

## プライバシー

プッシュ通知に関する情報の取り扱いについては、[プライバシーポリシー](/privacy-policy)をご確認ください。

---

[capsicum](/)
