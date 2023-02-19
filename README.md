# git-workshop

## gitの設定

1. vscodeとgitは適当にインストールする(初回のみ)

1. gitの設定をする

   https://blog.katsubemakito.net/git/git-config-1st

   `git config`コマンドで設定してもいいのだけれど、`~/.gitconfig`にコピペすれば速いと思う。userはgithubと同じものにしておくと便利。

   ```.gitconfig
   [user]
       name = [入力]
       email = [入力]
   [core]
       autocrlf = false
       ignorecase = false
   [pull]
       ff = only
       rebase = false
   [push]
       default = current
   ```
1. githubにssh-key登録する

   秘密鍵の作成。ed25519は楕円曲線暗号でめっちゃ安全。コメントは適宜変更。

   ```sh
   ssh-keygen -t ed25519 -C "comment"
   ```

   作った`id_ed25519.pub`をgithubにコピペ。

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

1. ブランチを切る

   ```bash
   git checkout -b mybranch
   ```

1. ファイル編集とかする

1. git addする

   ```sh
   # -A ないと削除したファイルはそのままになる
   git add . -A
   ```

1. git commit する

   ```sh
   git commit -m 'ファイル全削除'
   ```

1. git push　する

   ```sh
   git push
   ```

githubにブランチmybranchができていたら成功

## 便利機能

- mainブランチに他の人の進捗が先に入ったときは`git rebase`してから`git push`する
- コミットメッセージにissue番号入れると勝手にリンクがはられる
- fix: なんとかを修正 #14 とかいうコミットメッセージにするとissueの#14が勝手に閉じる

追記歓迎！
