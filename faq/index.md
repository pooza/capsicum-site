---
title: FAQ - capsicum
---

# よくある質問

## プリセットサーバーとは何ですか？

「プリセットサーバー」とは、capsicum にあらかじめ登録されている、開発者 pooza が運営・参加するコミュニティの Mastodon / Misskey サーバー群です。capsicum はもともとこれらのサーバーのユーザーに向けて開発されたアプリで、[プッシュ通知]((/push-notification))などの一部機能はプリセットサーバーのアカウントをお持ちの方を対象としています。一覧と登録方法は[プリセットサーバーについて](/preset-servers)をご覧ください。

## プッシュ通知は誰でも使えますか？

プッシュ通知は、[プリセットサーバー](/preset-servers)にアカウントをお持ちの方に無償で提供します。現在アカウントをお持ちでない方も、プリセットサーバーに登録することで利用できます。詳しくは[プッシュ通知について](/push-notification)をご覧ください。

## デスクトップ版はどこからインストールできますか？

- **macOS**: [Mac App Store](https://apps.apple.com/jp/app/capsicum/id6760206608) から無償で配信中です。macOS 11.5 以降が必要です
- **Linux**: [GitHub Releases](https://github.com/pooza/capsicum/releases/latest) から AppImage をダウンロードしてご利用ください。
- **Windows**: [Microsoft Store](https://apps.microsoft.com/detail/9np2gr7m2w6p) から無償で配信中です（v1.27 で公開）。Store 公開前の先行配布や証明書 import を厭わない上級者向けに、[GitHub Releases](https://github.com/pooza/capsicum/releases/latest) からの自己署名 MSIX 直配も継続しています

各プラットフォームの導入方法・既知の制約は [デスクトップ版について](/desktop) を参照してください。

## Windows 版のインストールがうまくいきません

通常は [Microsoft Store](https://apps.microsoft.com/detail/9np2gr7m2w6p) からインストールしてください。証明書 import の手間なく一般の Windows ユーザーがそのまま導入できます。

GitHub Releases の自己署名 MSIX 直配を使う場合（Store 公開前の先行検証など）は、インストール前に自己署名証明書を信頼ストアに import する必要があります。PowerShell を管理者として実行し、`capsicum-signing.cer` を import してから `capsicum.msix` をインストールしてください。詳細な手順は [packaging/windows/INSTALL.md](https://github.com/pooza/capsicum/blob/main/packaging/windows/INSTALL.md) を参照してください。

## Linux 版で日本語入力ができません

`ibus-mozc` 等の ibus 経路は動作確認済みです。`fcitx5` 経路も外部ユーザーから動作報告をいただいています。`uim` 用の immodule も AppImage に同梱していますが、開発環境外のため **best-effort** とさせてください。動作しない場合は ibus か fcitx5 経由でご利用ください。

ibus 経路で動作しない場合は、`~/.local/share/capsicum/logs/` のログとあわせて [PieFed コミュニティ](https://pf.korako.me/c/capsicum) または GitHub Issues にご報告ください。

## iOS で ATOK を使うと文字が二重に入力されます

ATOK（iOS）の「インライン入力」と相性問題があり、文字が二重に入力されることがあります。以下のいずれかで回避できます。

- ATOK の設定で **「従来のカーソル位置入力を使用」を ON** にする（インライン入力は ON のままで使えます。おすすめ）
- ATOK の **「インライン入力」を OFF** にする
- 一時的に標準キーボードに切り替える

Flutter 本体側の不具合のため、根本解決は上流の対応待ちです（[#54](https://github.com/pooza/capsicum/issues/54)）。

## macOS 版と iOS 版は別々に買う必要がありますか？

capsicum はそもそも無料アプリですが、Universal Purchase に対応しているため購入履歴は iOS / iPadOS / macOS で共有されます。同じ Apple ID でログインしていれば、いずれかのプラットフォームから入れたものが他のプラットフォームでもインストール可能になります。
