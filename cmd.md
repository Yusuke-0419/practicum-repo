# Git/GitHub実習

## 目次

  1. [ローカルリポジトリー作成](#ローカルリポジトリー作成)  
    1. ["Z:\実習\git"にローカルリポジトリを作成する](#z実習gitにローカルリポジトリを作成する)  
    2. [リポジトリが作成されているか確認する](#リポジトリが作成されているか確認する)  
    3. ["cmd.md"ファイルを作成し、使用したコマンドをMarkDown形式でわかりやすく記載する](#"cmd.md"ファイルを作成し、使用したコマンドをMarkDown形式でわかりやすく記載する)  
  2. [コミット](#コミット)  
    1. ["main.c"ファイルを作成し、下記プログラムを作成する](#maincファイルを作成し下記プログラムを作成する)  
    2. ["main.c"をインデックスに追加する](#maincをインデックスに追加する)  
    3. ["main.c"がステージングされていることを確認する](#maincがステージングされていることを確認する)  
    4. [メッセージ"create main.c"を付加し"main.c"をコミットする](#メッセージcreate-maincを付加しmaincをコミットする)  
    5. ["main.c"がコミットされていることを確認する](#maincがコミットされていることを確認する)  
    6. ["main.c"を下記のように修正してください](#maincを下記のように修正してください)  
    7. ["sub"フォルダを作成する](#subフォルダを作成する)  
    8. ["sub"フォルダ内に"sub.h"ファイルを作成し、下記プログラムを作成する](#subフォルダ内にsubhファイルを作成し下記プログラムを作成する)  
    9. ["sub"フォルダ内に"sub.c"ファイルを作成し、下記プログラムを作成する](#subフォルダ内にsubcファイルを作成し下記プログラムを作成する)  
    10. [main.c、sub.h、sub.cファイルを何かコミットメッセージを付けてコミットする](#maincsubhsubcファイルを何かコミットメッセージを付けてコミットする)  
  3. [ファイルを元に戻す](#ファイルを元に戻す)  
    1. [main.cファイル削除する](#maincファイル削除する)  
    2. [main.cファイルを復活する](#maincファイルを復活する)  
    3. [再度main.cファイル削除する](#再度maincファイル削除する))  
    4. [コミットメッセージを付けてコミットする](#コミットメッセージを付けてコミットする)  
    5. [main.cファイルを復活する](#maincファイルを復活する-1)  
  4. [ブランチ](#ブランチ)  
    1. ["hoge"ブランチを作成する](#hogeブランチを作成する)  
    2. ["hoge"ブランチに切り替える](#hogeブランチに切り替える)  
    3. ["hoge"ブランチに切り替り替わったことを確認する](#hogeブランチに切り替り替わったことを確認する)  
    4. ["test.txt"ファイルを作成(中身は空)する](#testtxtファイルを作成中身は空する)  
    5. ["test.txt"ファイルを何かコミットメッセージを付けてコミットする](#testtxtファイルを何かコミットメッセージを付けてコミットする)  
    6. ["hoge"ブランチを"feature"に名称を変更する](#hogeブランチをfeatureに名称を変更する)  
    7. ["main"ブランチに切り替える](#mainブランチに切り替える)  
    8. ["test.txt"ファイルが存在しないことを確認する](#testtxtファイルが存在しないことを確認する)  
  5. [マージ](#マージ)  
    1. ["feature"ブランチの内容を"main"ブランチへマージする](#featureブランチの内容をmainブランチへマージする)  
    2. ["test.txt"ファイルが存在することを確認する](#testtxtファイルが存在することを確認する)  
    3. ["feature"ブランチを削除する](#featureブランチを削除する)  
    4. ["feature"ブランチが存在しないことを確認する](#featureブランチが存在しないことを確認する)  
  6. [コンフリクト](#コンフリクト)  
    1. ["feature"ブランチを作成し切り替える。](#featureブランチを作成し切り替える)  
    2. ["main.c"ファイルの先頭行に"/* main */"を挿入し、何かコミットメッセージを付けてコミットする。](#maincファイルの先頭行に-main-を挿入し何かコミットメッセージを付けてコミットする)  
    3. ["main"ブランチに切り替える。](#mainブランチに切り替える-1)  
    4. ["main.c"ファイルの先頭行に"// main"を挿入し、何かコミットメッセージを付けてコミットする。](#maincファイルの先頭行に-mainを挿入し何かコミットメッセージを付けてコミットする)  
    5. ["feature"ブランチの内容を"main"ブランチへマージする。](#featureブランチの内容をmainブランチへマージする-1)  
    6. [エラーが表示されマージできないことを確認する。](#エラーが表示されマージできないことを確認する)  
    7. ["main.c"ファイルを開き、"<<<<<<< HEAD"行から"======="行と">>>>>>> feature"を削除する。](#maincファイルを開き-head行から行と-featureを削除する)  
    8. ["main.c"ファイルを何かコミットメッセージを付けてコミットする。](#maincファイルを何かコミットメッセージを付けてコミットする)  
    9. [マージが完了したことを確認する。](#マージが完了したことを確認する)  
  7. [フォーク/クローン](#フォーククローン)  
    1. ["Z:\実習\github"フォルダを作成する](#z実習githubフォルダを作成する)  
    2. [上記フォルダにフォークしたリポジトリをクローンする](#上記フォルダにフォークしたリポジトリをクローンする)  
  8. [プッシュ](#プッシュプルリクエスト)  
    1. [自身のWindowsログイン名のブランチを作成し切り替える。](#自身のwindowsログイン名のブランチを作成し切り替える)  
    2. [自身の名前(フルネーム)のMarkDownファイルを作成し、自己紹介を記入する。](#自身の名前フルネームのmarkdownファイルを作成し自己紹介を記入する)  
    3. [リポジトリへプッシュする。](#リポジトリへプッシュする)  



## ローカルリポジトリー作成

[目次 へ](#目次)

### "Z:\実習\git"にローカルリポジトリを作成する

コマンドプロンプトを起動する。
特に設定しなければ'C:\Users\<ユーザ名>'にいるはずなので、まずZドライブに移動する。
ドライブ間を移動する場合は`/d`オプションを指定する必要がある。

```
>cd /d Z:
```

つぎに、実習ディレクトリを作成し、移動する。

```
>mkdir "実習" #実習ディレクトリの作成
>cd 実習 #実習ディレクトリに移動
```

同様にして、gitディレクトリを作成し移動する。

```
>mkdir git  
>cd ./git #./とすると今いるディレクトリを参照する
```

ローカルリポジトリの作成を行う。

```
>git init
```

[ローカルリポジトリー作成 へ](#ローカルリポジトリー作成)

### リポジトリが作成されているか確認する

ローカルリポジトリの状態を確認するためのコマンド`git status`を利用する。

```
>git status
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

上記のようなログが表示されていれば問題ない。  
.gitがない（`git init`が失敗した）場合、下記のようなログが表示される。

```
Initialized empty Git repository in <address>
```

[ローカルリポジトリー作成 へ](#ローカルリポジトリー作成)

### "cmd.md"ファイルを作成し、使用したコマンドをMarkDown形式でわかりやすく記載する

今回は`echo`コマンドを用いてファイルの作成、編集を行う。

```
>echo. > cmd.md #ファイルの作成
>cmd.md #ファイルを開く
```

記載内容や方法については省略する。

[ローカルリポジトリー作成 へ](#ローカルリポジトリー作成)


## コミット

[目次 へ](#目次)

### "main.c"ファイルを作成し、下記プログラムを作成する

main.cファイルを作成し開く。

```
>echo. > main.c
>main.c
```

指定の内容を入力し、保存して閉じる。

[コミット へ](#コミット)

### "main.c"をインデックスに追加する

インデックスに追加する作業をステージングという。ステージングには`git add`コマンドを利用する。

```
>git add main.c
```

[コミット へ](#コミット)

### "main.c"がステージングされていることを確認する

ステージングの確認には`git status`コマンドを利用する。

```
>git status
```

実行すると、下記のようなログが出力される。

```
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   main.c

#cmd.mdを同ディレクトリに作成した場合は下記のログも出力される。
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        cmd.md
```

[コミット へ](#コミット)

### メッセージ"create main.c"を付加し"main.c"をコミットする

コミットには`git commit`コマンドを使う。`-m`オプションを利用してメッセージを追加してコミットできる。

```
>git commit -m "create main.c"
```

[コミット へ](#コミット)

### "main.c"がコミットされていることを確認する

`git log`コマンドでコミットの履歴が確認できる。`--stat`と指定すると、ファイルの追加、変更内容をまとめて表示できる。

```
>git log --stat
```

確認できたら`q`を入力すると脱出可能。

[コミット へ](#コミット)

### "main.c"を下記のように修正してください

main.cを起動し、ファイルの内容を更新する。

```
>main.c
```

[コミット へ](#コミット)

### "sub"フォルダを作成する

```
>mkdir sub
```

[コミット へ](#コミット)

### "sub"フォルダ内に"sub.h"ファイルを作成し、下記プログラムを作成する

subフォルダに移動し、sub.hファイルを作成して開く。
指定内容は各自入力。

```
>cd sub
>echo. > sub.h
>sub.h
```

[コミット へ](#コミット)

### "sub"フォルダ内に"sub.c"ファイルを作成し、下記プログラムを作成する

同様にしてsub.cファイルを作成する。

```
>echo. > sub.c
>sub.c
```

[コミット へ](#コミット)

### main.c、sub.h、sub.cファイルを何かコミットメッセージを付けてコミットする

現在、Z:/実習/gitフォルダにいない場合はフォルダを移動する。

```
>cd Z:/実習/git
```

つぎに前回のコミット同様、まずはステージングを行う。
変更したファイルも追加と同様、`git add`をつかう。

```
>git add main.c sub #複数のファイル/フォルダを同時にステージング
>git status
```

`git status`で確認を行い、問題なければコミットする。
今回はコメントを「change main.c, add sub_folder」とした。
メッセージのコメント例は[参考へ](#コミットの際のコメント)。

```
>git  commit -m "docs main.cの仕様を変更, sub_folderの追加"
>git log --stat
```

コミットできているか確認して終了する。

[コミット へ](#コミット)

## ファイルを元に戻す

[目次 へ](#目次)

### main.cファイル削除する

`git rm`コマンドでファイル名を指定することで削除できる。
また、削除された内容はステージングされる。

```
>git rm main.c
```

[ファイルを元に戻す へ](#ファイルを元に戻す)

### main.cファイルを復活する

コミットする前に復元する場合、以下のように行う。

```
>git checkout HEAD main.c
```

`HEAD`は直近のコミットを示しており、そこからmain.cを復元するよう命令した。

[ファイルを元に戻す へ](#ファイルを元に戻す)

### 再度main.cファイル削除する

同様にしてmain.cを削除する。

```
>git rm main.c

```


[ファイルを元に戻す へ](#ファイルを元に戻す)

### コミットメッセージを付けてコミットする

`git status`で削除されていることがステージングされているか確認し、
問題なければコメントを付してコミットする。

```
>git status
>git commit -m "delete main.c"
```

[ファイルを元に戻す へ](#ファイルを元に戻す)

### main.cファイルを復活する

コミットした場合、`HEAD`からは指定できないため、
復活したいmain.cの存在するコミットを特定する必要がある。

```
>git log --oneline  #一行で簡潔に表示
>git log --stat #ファイルの変更や追加などの情報がわかる
```

`--oneline`でコメント内容から特定できなかった場合に`--stat`を使うとよいだろう
（そうならないよう、簡潔にコメントへ内容を記載できるとよい）。  
特定したコミットハッシュをコピーし、下記コマンドで復元する。

```
>git restore -s <コミットハッシュ> main.c
```

コミットハッシュは40文字あるが、上7,8文字でも一意であれば指定して復元できる。

[ファイルを元に戻す へ](#ファイルを元に戻す)

## ブランチ

[目次 へ](#目次)

### "hoge"ブランチを作成する

ブランチを作成するコマンドは`git branch`を用いる。

```
>git branch hoge
>git branch
```

また、単に`>git branch`とすることで、ブランチの内容を確認できる。

[ブランチ へ](#ブランチ)

### "hoge"ブランチに切り替える

ブランチの移動には`git checkout`と`git seitch`がある。個人的には後者が好み。

```
>git checkout hoge
>git switch hoge  #どちらかを実行
```

[ブランチ へ](#ブランチ)

### "hoge"ブランチに切り替り替わったことを確認する

`git branch`で現在のブランチを確認する。

```
>git branch
```

`* hoge`となっていればよい。

[ブランチ へ](#ブランチ)

### "test.txt"ファイルを作成(中身は空)する

`echo`コマンドを使う。

```
>echo. > test.txt
```

[ブランチ へ](#ブランチ)

### "test.txt"ファイルを何かコミットメッセージを付けてコミットする

まず、ステージングとその確認を行う。

```
>git add test.txt
>git status
```

問題なければコミットする。

```
>git commit -m "docs: add test.txt"
```

[ブランチ へ](#ブランチ)

### "hoge"ブランチを"feature"に名称を変更する

ブランチ名の変更を行う。

```
>git branch -m hoge feature #hogeブランチにいるのでhogeは省略可
>git branch
```

`>git branch`でブランチ名の変更が確認できればよい。

[ブランチ へ](#ブランチ)

### "main"ブランチに切り替える

mainブランチに切り替え、確認する。

```
>git switch main
>git branch
```

[ブランチ へ](#ブランチ)

### "test.txt"ファイルが存在しないことを確認する

より容易に確認できるコマンドがありそうだが、今回は`git ls-tree`を使用する。

```
>git ls-tree main
>git ls-tree feature  #ついでにfeatureと比較
```

`>git ls-tree main`にtest.txtが存在しなければ終了。

[ブランチ へ](#ブランチ)

## マージ

[目次 へ](#目次)

### "feature"ブランチの内容を"main"ブランチへマージする

featureブランチにいるとマージできないため、どのブランチにいるか確認する。

```
>git branch
```

マージには`git merge`を使う。`-m`でコメントを付すと後で確認しやすい。

```
>git merge feature -m "merge feature"
```

[ファイルを元に戻す へ](#ファイルを元に戻す)

### "test.txt"ファイルが存在することを確認する

`git ls-tree`でmainブランチのファイルを確認する。

```
>git ls-tree main
```

[ファイルを元に戻す へ](#ファイルを元に戻す)

### "feature"ブランチを削除する

ブランチの削除には`git branch`の`-d`オプションを利用する。

```
>git branch -d feature
```

[ファイルを元に戻す へ](#ファイルを元に戻す)

### "feature"ブランチが存在しないことを確認する

`git branch`でブランチの確認をする。

```
>git branch
```

featureブランチが存在しなければ終了。

[ファイルを元に戻す へ](#ファイルを元に戻す)

## コンフリクト

[目次 へ](#目次)

### "feature"ブランチを作成し切り替える

featureブランチを作成、切り替えを行う。

```
>git branch feature
>git switch feature
```

[コンフリクト へ](#コンフリクト)

### "main.c"ファイルの先頭行に"/* main */"を挿入し、何かコミットメッセージを付けてコミットする

mein.cを開いて追記する。

```
>main.c
```

ステージング、コミットを行う。

```
>git add main.c
>git status
>git commit -m "main.c: add title"
```

[コンフリクト へ](#コンフリクト)

### "main"ブランチに切り替える

切り替える

```
>git switch main
```

[コンフリクト へ](#コンフリクト)

### "main.c"ファイルの先頭行に"// main"を挿入し、何かコミットメッセージを付けてコミットする

mainブランチでmain.cを開く。

```
>main.c
```

ステージング、コミット。
見やすさを考慮してコメント内容を若干変更。

```
>git add main.c
>git status
>git commit -m "main.c: add title @main branch"
```

[コンフリクト へ](#コンフリクト)

### "feature"ブランチの内容を"main"ブランチへマージする

マージしてみる。

```
>git merge feature
```

[コンフリクト へ](#コンフリクト)

### エラーが表示されマージできないことを確認する

確認した。参考までに下記にログを記載。

```
Auto-merging main.c
CONFLICT (content): Merge conflict in main.c
Automatic merge failed; fix conflicts and then commit the result.
```

[コンフリクト へ](#コンフリクト)

### "main.c"ファイルを開き、"<<<<<<< HEAD"行から"======="行と">>>>>>> feature"を削除する

開いて修正する。

```
>main.c
```

[コンフリクト へ](#コンフリクト)

### "main.c"ファイルを何かコミットメッセージを付けてコミットする

ステージング、コミット

```
>git add main.c
>git status
>git commit -m "resolved conflict"
```

[コンフリクト へ](#コンフリクト)

### マージが完了したことを確認する

確認する。

```
>git log --stat
```

一番上のコミット結果に`Merge: ～～`となっていれば成功。

[コンフリクト へ](#コンフリクト)

## フォーク/クローン

フォークについてはGitHub上での操作のため、ここでは省略する。  
[目次 へ](#目次)

### "Z:\実習\github"フォルダを作成する

"Z:\実習"フォルダに移動する。

```
>cd /d Z:/実習  #絶対パスでの指定
>cd ..  #Z:/実習/gitにいる場合の相対パス指定
```

"github"フォルダを作成する。

```
>mkdir github
>dir
```

ディレクトリが作成できているか確認して終了。

[フォーク/クローン へ](#フォーククローン)

### 上記フォルダにフォークしたリポジトリをクローンする

フォークしたGitHubのURLを取得する。そのURLを指定して`git clone`コマンドでクローンする。

```
>git clone <URL>
>git remote -v
```

`git remote`コマンドでURLを確認することも可能。
`origin`以下のURLは自身のGitHubの、`upstream`以下にはフォーク元のURLが表示される。

[フォーク/クローン へ](#フォーククローン)

## プッシュ/プルリクエスト

プルリクエストは省略する。

[目次 へ](#目次)

### 自身のWindowsログイン名のブランチを作成し切り替える

`Z:/実習/github/git-exercises`フォルダへ移動する。

```
>cd /d Z:/実習/github/git-exercises  #絶対パスでの指定
>cd git-exercises  #Z:/実習/githubにいる場合
```

自身の名前のブランチを作成し、切り替える。

```
>git branch <ログイン名>
>git switch <ログイン名>
```

[プッシュ へ](#プッシュ)

### 自身の名前(フルネーム)のMarkDownファイルを作成し、自己紹介を記入する

MarkDownファイルを作成し、開く。

```
>echo. > <氏名>.md
><氏名>.md
```

自己紹介の記入は省略する。

[プッシュ へ](#プッシュ)

### リポジトリへプッシュする

ステージング、コミットを行う。

```
>git add <氏名>.md
>git status 
>git commit -m "add <氏名>.md"
```

ローカルリポジトリへプッシュする。

```
>git push origin main
```

[プッシュ へ](#プッシュ)



## 参考

### コミットの際のコメント

やれファイルを追加しただのデバッグしただの色々ありますが、都度書き方が変わると見返してわかりづらいです。
組織に合わせるのが前提だと思いますが、参考としてどういったワードが適切かを下記サイト参考に自分で決めておくとよいと思います。  
参考：[僕が考える最強のコミットメッセージの書き方](https://qiita.com/konatsu_p/items/dfe199ebe3a7d2010b3e)

[リンク元へ戻る](#maincsubhsubcファイルを何かコミットメッセージを付けてコミットする)

<!-- 
<details><summary>おまけ</summary>

ブランチ操作で遊んでいたらgit側から怒られました。その時のエラーや対処の諸々を下記に記しておきます。
最終的に過去のコミット時点に戻すことで無理やり突破しましたが、コミット時点を使用して戻す際の参考にどうぞ。

### 起きたこと
`main`内にsubブランチ作成して適当なファイルを入れて動作の確認をしていたところ、`git push`でエラーを吐くようになりました。

```
$ >git push origin main

To https://github.com/<ユーザ名>/<ブランチ名>.git
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/Yusuke-0419/practicum-repo.git'
hint: Updates were rejected because the remote contains work that you do not
hint: have locally. This is usually caused by another repository pushing to
hint: the same ref. If you want to integrate the remote changes, use
hint: 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

リモートリポジトリにローカルにないファイルがある、原因は～（略）と書いている。
とりあえず`git pull`してみろ的なことが書いてあるので実行>ステージングしてコミットを行ったができない。
`git status`のログは以下。

```
$ >git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        practicum-repo/

nothing added to commit but untracked files present (use "git add" to track)
```

ネットで調べたが有力そうな過去のコミットを参照して戻す方法を試しました。
今回は`git reset`を用いて実行した。バージョンを戻すコマンドはいくつかある様だが、
使い分けは下記リンクを参照。

参考）[Gitバージョンの戻し方 - 3つのコマンドと使い分け](https://zenn.dev/yutabeee/articles/034fb9383f441c)

```
$ >git push origin main
To https://github.com/<ユーザ名>/<リポジトリ名>.git
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'https://github.com/<ユーザ名>/<リポジトリ名>.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

ということで怒られたわけですが、エラーの内容が異なります。色々調べましたが、どうやらGitのバージョンを戻そうとしたときに、リポジトリの履歴が一致しないため反映ができないとのこと。そこで先述のサイトにたどり着き、`git push origin <ブランチ名> --force`で無理やりpushしたながれになります。

ちなみに` ! [rejected]        main -> main (non-fast-forward)`で検索すると分岐ブランチを設定してクリアしているページなども見つかりましたがうまくいきませんでした。

</details>
 -->
