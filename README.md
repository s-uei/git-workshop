# git-workshop

## gitの設定

1. vscodeとgitは適当にインストールする(初回のみ)

1. githubのアカウントを適当に作る

1. gitの設定をする

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

1. githubにssh-key登録する

   秘密鍵の作成。ed25519は楕円曲線暗号でめっちゃ安全。

   ```sh
   ssh-keygen -t ed25519 -C ""
   ```

   作った`id_ed25519.pub`をgithubにコピペ。

   ```sh
   cat ~/.ssh/id_ed25519.pub #出てくる文字列をコピー
   ```

   貼り付け方は以下を見る。

   https://docs.github.com/ja/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account

## gitの基本の流れ

1. git cloneする

   ```bash
   # ssh URLで
   git clone git@github.com:s-uei/git-workshop.git
   # codeでフォルダを開く
   code git-workshop
   ```

1. vscodeでターミナルを開く

   `Ctrl+Shift+@`

1. ファイル編集とかする

1. git addする

   ```sh
   # -A ないと削除したファイルはそのままになる
   git add . -A
   ```

1. git commit する

   ```sh
   git commit -m '修正１'
   ```

1. git push　する

   ```sh
   git push
   ```

githubに変更が反映されていたら成功。

## その他

- 複雑な修正はissueに概要を書き専用のブランチを作って対応する
- mainブランチに他の人の進捗が先に入ったときは`git rebase`してから`git push`する
- コミットメッセージにissue番号入れると勝手にリンクがはられる
- fix: なんとかを修正 #14 とかいうコミットメッセージにするとissueの#14が勝手に閉じる
