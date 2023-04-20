# git-workshop

## git の設定

1. vscode と git は適当にインストールする(初回のみ)

1. github のアカウントを適当に作る

1. git の設定をする。シェルに以下を打つ。

   ```sh
   GITHUB_ACCOUNT=??? # 自分のアカウント名に変更
   git config --global user.name $GITHUB_ACCOUNT
   git config --global user.email $GITHUB_ACCOUNT@users.noreply.github.com
   git config --global core.autocrlf false # crlf,lfの自動変換を無効
   git config --global core.ignorecase false # 大文字小文字の自動修正を無効
   git config --global pull.ff only # pullの自動マージを無効
   git config --global push.default current # 現在の作業ブランチをプッシュ
   ```

   その他適宜設定をする。

1. github に ssh-key 登録する

   秘密鍵の作成。ed25519 は楕円曲線暗号でめっちゃ安全。

   ```sh
   ssh-keygen -t ed25519 -C ""
   ```

   作った`id_ed25519.pub`を github にコピペ。

   ```sh
   cat ~/.ssh/id_ed25519.pub #出てくる文字列をコピー
   ```

   貼り付け方は以下を見る。

   https://docs.github.com/ja/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account

## git の基本の流れ

1. git clone する

   ```bash
   # ssh URLで
   git clone git@github.com:s-uei/git-workshop.git
   # codeでフォルダを開く
   code git-workshop
   ```

1. vscode でターミナルを開く

   `Ctrl+Shift+@`

1. ファイル編集とかする

1. git add する

   ```sh
   # -A ないと削除したファイルはそのままになる
   git add . -A
   ```

1. git commit する

   ```sh
   git commit -m '修正１'
   ```

1. git push 　する

   ```sh
   git push
   ```

github に変更が反映されていたら成功。

## その他

- 複雑な修正は issue に概要を書き専用のブランチを作って対応する
- main ブランチに他の人の進捗が先に入ったときは`git rebase`してから`git push`する
- コミットメッセージに issue 番号入れると勝手にリンクがはられる
- fix: なんとかを修正 #14 とかいうコミットメッセージにすると issue の#14 が勝手に閉じる

henkou
