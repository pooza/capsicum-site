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
- **Linux**: ワンライナー `curl -fsSL https://capsicum.shrieker.net/install.sh | bash` で、AppImage のダウンロードからアプリメニュー登録までを一括で導入できます（手動で [GitHub Releases](https://github.com/pooza/capsicum/releases/latest) から AppImage を入手することもできます）
- **Windows**: [Microsoft Store](https://apps.microsoft.com/detail/9np2gr7m2w6p) から無償で配信中です（v1.27 で公開）。Windows の公式配布は Microsoft Store 単独です

各プラットフォームの導入方法・既知の制約は [デスクトップ版について](/desktop) を参照してください。

## Windows 版のインストールがうまくいきません

Windows の公式配布は [Microsoft Store](https://apps.microsoft.com/detail/9np2gr7m2w6p) 単独です。証明書 import の手間なく一般の Windows ユーザーがそのまま導入できます。うまくいかない場合は、Windows のバージョン（10 は 1809 以降 / 11）をご確認のうえ、[PieFed コミュニティ](https://pf.korako.me/c/capsicum) または GitHub Issues にご報告ください。

## Linux 版で日本語入力ができません

`ibus-mozc` 等の ibus 経路は動作確認済みです。`fcitx5` 経路も外部ユーザーから動作報告をいただいています。`uim` 用の immodule も AppImage に同梱していますが、開発環境外のため **best-effort** とさせてください。動作しない場合は ibus か fcitx5 経由でご利用ください。

ibus 経路で動作しない場合は、`~/.local/share/capsicum/logs/` のログとあわせて [PieFed コミュニティ](https://pf.korako.me/c/capsicum) または GitHub Issues にご報告ください。

## Linux 版で絵文字が白黒（モノクロ）で表示されます

お使いの環境に**カラー絵文字フォントが入っていない**可能性が高いです。Linux ではアプリがフォントの選択をシステム（fontconfig）に任せるため、カラー絵文字フォントが見つからないと白黒の字形で描画されます。

まず、ウェブブラウザで絵文字がカラー表示されるかご確認ください。**ブラウザでも白黒であれば、capsicum 固有の問題ではなくシステム全体でカラー絵文字フォントが不足しています**。次のいずれかでインストールできます（インストール後は capsicum を再起動してください）。

- **Debian / Ubuntu 系**: `sudo apt install fonts-noto-color-emoji`
- **Fedora 系**: `sudo dnf install google-noto-color-emoji-fonts`
- **Arch 系**: `sudo pacman -S noto-fonts-emoji`

これはシステム全体のフォント設定なので、capsicum だけでなくブラウザや他のアプリの絵文字もカラー表示になります。

なお、capsicum 側で設定 →「表示」→「**カラー絵文字を使う**」がオンになっている必要があります（Linux のみに表示される項目で、既定はオンです）。

ブラウザではカラーなのに capsicum だけ白黒、という場合は上記とは別の原因（フォントの優先順位）が考えられますので、`fc-match -s emoji | head` の結果とあわせて [PieFed コミュニティ](https://pf.korako.me/c/capsicum) または GitHub Issues にご報告ください。

## Linux 版で半角数字などの文字幅が崩れて見えます

設定 →「表示」→「**カラー絵文字を使う**」を**オフ**にすると解消します（Linux のみに表示される項目です）。

capsicum は Linux でカラー絵文字を表示するためにカラー絵文字フォント（Noto Color Emoji）を使いますが、このフォントは数字（0〜9）などの字形も内部に持っているため、環境によっては半角数字やドットまでこのフォントで描かれ、文字幅が広がって不揃いに見えることがあります（バージョン表記・文字数カウンタ・URL 内の数字など）。

「カラー絵文字を使う」をオフにするとカラー絵文字フォントを使わなくなり、文字幅は正しく表示されます。ただし一部の Unicode 絵文字は白黒（モノクロ）になります。カラー絵文字と文字幅のどちらを優先するか、環境に合わせてお選びください。

## iOS で ATOK を使うと文字が二重に入力されます

ATOK（iOS）の「インライン入力」と相性問題があり、文字が二重に入力されることがあります。以下のいずれかで回避できます。

- ATOK の設定で **「従来のカーソル位置入力を使用」を ON** にする（インライン入力は ON のままで使えます。おすすめ）
- ATOK の **「インライン入力」を OFF** にする
- 一時的に標準キーボードに切り替える

Flutter 本体側の不具合のため、根本解決は上流の対応待ちです（[#54](https://github.com/pooza/capsicum/issues/54)）。

## macOS 版と iOS 版は別々に買う必要がありますか？

capsicum はそもそも無料アプリですが、Universal Purchase に対応しているため購入履歴は iOS / iPadOS / macOS で共有されます。同じ Apple ID でログインしていれば、いずれかのプラットフォームから入れたものが他のプラットフォームでもインストール可能になります。

## サーバー側の機能が増えた／変わったのにアプリに反映されません

capsicum は、サーバーの拡張機能（番組表連携や劇中ワードのサジェストなど）の対応状況を、**アプリ起動時に一度だけ**確認します。起動したまま使い続けていると、その後にサーバー側が更新されても自動では反映されません。

次のいずれかで最新の状態を取り込めます。

- **アプリを再起動する**（新しいバージョンへ更新した場合も、更新後の初回起動で再確認されます）
- **サーバー情報画面で「再検出」をタップする**

通常はアプリ更新（≒再起動）のタイミングで自然に追従するため意識する必要はありませんが、長時間起動しっぱなしのときなどにお試しください。

---

[capsicum](/)
