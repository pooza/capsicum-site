---
title: FAQ - capsicum
---

# よくある質問

## プッシュ通知は誰でも使えますか？

プッシュ通知は、プリセットサーバーにアカウントをお持ちの方に無償で提供します。現在アカウントをお持ちでない方も、プリセットサーバーに登録することで利用できます。詳しくは[プッシュ通知について](/push-notification)をご覧ください。

## デスクトップ版はどこからインストールできますか？

- **macOS**: [Mac App Store](https://apps.apple.com/jp/app/capsicum/id6760206608) から無償で配信中です。macOS 11.5 以降が必要です
- **Linux**: [GitHub Releases](https://github.com/pooza/capsicum/releases/latest) から AppImage をダウンロードしてご利用ください。Flathub への配信も準備中です
- **Windows**: [GitHub Releases](https://github.com/pooza/capsicum/releases/latest) から MSIX をダウンロードしてご利用ください

各プラットフォームの導入方法・既知の制約は [デスクトップ版について](/desktop) を参照してください。

## Windows 版のインストールがうまくいきません

Windows 版は自己署名 MSIX 形式で配布しており、インストール前に自己署名証明書を信頼ストアに import する必要があります。PowerShell を管理者として実行し、`capsicum-signing.cer` を import してから `capsicum.msix` をインストールしてください。詳細な手順は [packaging/windows/INSTALL.md](https://github.com/pooza/capsicum/blob/main/packaging/windows/INSTALL.md) を参照してください。

⚠️ 配布対象は「証明書 import を厭わない上級ユーザー」です。中期的には OV コード署名証明書を取得し、SmartScreen 通過する形式に格上げ予定です。Microsoft Store 公開は法人化対応待ちで当面保留しています。

## Linux 版で日本語入力ができません

`ibus-mozc` 等の ibus 経路は動作確認済みです。`fcitx5` 経路も外部ユーザーから動作報告をいただいています。`uim` 用の immodule も AppImage に同梱していますが、開発環境外のため **best-effort** とさせてください。動作しない場合は ibus か fcitx5 経由でご利用ください。

ibus 経路で動作しない場合は、`~/.local/share/capsicum/logs/` のログとあわせて [PieFed コミュニティ](https://pf.korako.me/c/capsicum) または GitHub Issues にご報告ください。

## macOS 版と iOS 版は別々に買う必要がありますか？

capsicum はそもそも無料アプリですが、Universal Purchase に対応しているため購入履歴は iOS / iPadOS / macOS で共有されます。同じ Apple ID でログインしていれば、いずれかのプラットフォームから入れたものが他のプラットフォームでもインストール可能になります。
