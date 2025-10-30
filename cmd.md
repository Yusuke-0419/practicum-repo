
# Git/GitHubの基本操作をひと通り行う

本稿では、コマンドプロンプト操作を中心にGitおよびGitHubを利用する手順を説明する。
完全な初心者向けであり、初級者諸氏についてはコマンド備忘録的に利用されたい。
中級者以上の諸先輩方はブラウザバック推奨である。

<details>
  <summary>コマンドプロンプトの基本操作</summary>

  ## コマンドプロンプトを起動する
  
  まずはコマンドプロンプトを起動する。マウスなどを利用して起動してもよいが、プログラマっぽくキーボード操作で起動してみる。
  スタートボタン &rArr; `cmd`と入力してEnterとすれば起動でき、下のような表示がでれば問題ない。

  ```
  C:\Users\<ユーザ名>>
  ```
  
  ## ディレクトリの移動
  

  次にディレクトリ（ほぼフォルダと同義）の移動をする。入力できるのは">"の右側だが、左の"C:"以下は現在開いているエクスプローラの場所、
  と覚えればよい。試しに現在開いているフォルダの中身を確認する。その場合は、`dir`と入力する。

  ```
  C:\Users\<ユーザ名>>dir
  ```

  するとファイルやディレクトリがいくつか表示される。つぎに適当なディレクトリ（ここではDesktop）に移動してみる。
  
  ```
  C:\Users\<ユーザ名>>cd desktop  #実行する行
  
  C:\Users\<ユーザ名>\Desktop>  #実行した後、次のコマンドを入力するための行
  ```
  
  `cd`とは、Change Directionの略である。これでエクスプローラでデスクトップをダブルクリックし移動したような状態となる。
  試しに`dir`と入力すると、デスクトップに存在するファイルやディレクトリが表示されることがわかる。

  また、ひとつ上のディレクトリ、ここでは`C:\Users\<ユーザ名>`に戻ることを考える。
  ここでは絶対パスと相対パスを用いた移動をそれぞれ例示する。
 
  ```
  C:\Users\<ユーザ名>\Desktop>cd C:\Users\<ユーザ名>  #指定のディレクトリに移動する（絶対パス）
  
  C:\Users\<ユーザ名>\Desktop>cd ..  #ひとつ上のディレクトリに移動する（相対パス）
  ```

  さて、次に異なるドライブへの移動をする。今回の実習では現在のCドライブとは異なるドライブのZドライブに移動する必要があるため、
  `/d`というオプションが必要になる。
  
  ```
  C:\Users\<ユーザ名>>cd /d Z:
  ```

  ## ディレクトリの作成
  

  ディレクトリの作成を行う。先ほど移動したZドライブ内に`実習`ファイルを作成する。
  また、これ以降の操作では、コマンド部分のみコマンドラインに示す。

  ```
  >mkdir "実習"
  ```
  
  ダブルクォーテーションで囲わなくても動作はするが、特に日本語で入力する際は囲う方が親切だろう（完全に私見）。
  ここで、実際に作成できたか`dir`を用いて確認しておく。誤ってディレクトリを作成した場合は、`rd <ファイル名>`とすれば削除できる。
  問題なければ同様にして"実習"ディレクトリに移動し、"git"ディレクトリを作成、移動を行う。
  （補足：`cls`コマンドを実行するとログが消去され一番上に戻ることができる。適当なタイミングでつかうと便利かも）

</details>

<details>
  <summary>#1432 ローカルリポジトリ作成</summary>

  &nbsp;  
  ローカルリポジトリ作成のチケットを行っていく。
  ここで、本章では配布資料内でGitの初期設定等を終えている前提で説明を行う。

  ## ローカルリポジトリの作成

  `Z:\実習\git`にいることを確認する。
  `git init`を用いてローカルリポジトリを作成する。このコマンドは現在のディレクトリに.gitという隠しフォルダが作成される。
  `git init <ディレクトリ>`と指定することで、指定したディレクトリに作成することも可能。
  
  ```
  >git init <ディレクトリ（省略可）>
  ```
  
  つぎに`dir`コマンドを用いて.gitフォルダが作成されているかを確認する。.gitは隠しフォルダのため、`-a`オプションを利用する。

  ```
  >dir -a
  ```
  
  .gitがログに表示されていれば問題なく作成できている。

  ## cmd.mdファイルの作成
  

  今回は`echo`コマンドを用いてファイルの作成を行う。

  ```
  >echo hogehoge >cmd.md
  ```

  特に.mdファイルに入力をしない場合は`hogehoge`を`.`とすれば空の.mdファイルが作成できる。
  cmdからファイルを開く場合は、ファイル名を入力すれば開くことができる。

</details>

<details>
  <summary>#1433 コミット</summary>
  
  &nbsp;  
  **コミット**はファイルの追加、更新や削除などを行った際に必要な作業であり、**.git内の適当な場所に変更を保存する**イメージである。
  基本的にはコメントとあわせてコミットを行い、変更した内容を簡単に見直すことができるほか、
  コミット時点の変更状態を保存、呼び出しができることが利点である。

  ## ファイルを作成し、コミットする
  
  `echo`コマンドを用いてmain.cファイルを作成する。指定のプログラムを入力し保存した状態から説明を行う。  

  ### ステージング
  
  **ステージング**とは、**インデックスにコミットするファイルを登録する**作業のことである。
  この作業は、`git add`コマンドを用いて行う。今回はmain.cを指定するが、`.`とすることですべてステージングすることも可能である。

  ```
  >git add main.c
  ```

  つぎに`git status`コマンドでローカルリポジトリと作業中のディレクトリの違いを検出する。
  ステージング済の変更、ステージングしていない変更、ローカルリポジトリに存在していないファイルなどが確認できる。
  変更したファイルなどが一目で確認でき、コミットする前にもよく使うコマンドである。

  ```
  >git status
  ```
  
  `new file: main.c`と出力されていれば、main.cがステージングされている状態である。

  ### コミット

  `git commit`コマンドに`-m`オプションを用いることで、コメント付きでコミットする。
  ステージングされている内容（変更）を.gitファイルに書き込みするイメージ。
  
  ```
  >git commit -m "create main.c"
  ```
  
  コミットできているかの確認を`git log`コマンドを用いて行う。
  ここでは説明しないが、便利なオプションもあるので各自確認されたい。
  
  ```
  >git log
  ```

  ## ファイルの変更、追加をコミットする

  ファイルの変更、新規フォルダ/ファイルの作成についての説明は省略する。  
  Z:\実習\gitにいることを確認する。
  つぎに`git add`でステージングを行うが、sub.hとsub.cに関してはフォルダに格納されているため、フォルダを指定する。
  `git status`をセットで行うことも忘れないように。

  ```
  >git add main.c sub
  >git status
  ```
  
  特に問題なければ、適切なコメントを残してコミットすれば本チケットは完了。
  
</details>


<details>
  <summary>#1434 ファイルをもとに戻す</summary>

  &nbsp;    
  Git/GitHubの利点の1つであるファイルのバージョン管理を利用し、削除してしまったファイルの復活を行う。
  ディレクトリ上で削除した場合、削除してコミットした場合の2つの場合で試す。

  ## コミットする前に復活させる

  ### ファイルを削除する

  `del`コマンドでファイル名を指定することで削除できる。
  
  ```
  >del main.c
  >dir
  ```

  `dir`コマンドでmain.cが実際に削除されているか確認する。

  ### ファイルをインデックスから復活させる

  `git checkout`コマンドでファイルを復活させる。
  `git checkout`はインデックスのバージョンと一致するように更新するコマンドである。
  ブランチ移動のためのコマンド（次のチケットで説明する）としても使われることもある。
  
  ```
  >git checkout main.c
  ```

  `dir`コマンドで復元されているか確認する。
  
  ## コミットした後に復活させる
  
  ### ファイルを削除しコミットする

  まず、`del`などを用いてファイルを削除する。
  今回はコミットまで行うため、`git add .`（"."はすべてのファイルを指定）としてもよいが、
  ファイルを削除した情報のみをステージングしたいというモチベーションで実行する。
  その場合は、`git add -u <ファイル名>`とすればよい。
  また、削除とステージングを一括で行うコマンド`git rm`についても記しておく。

  ```
  >del main.c
  >git add -u main.c
  >git rm main.c  #削除とステージングを同時に行う
  >git status
  ```

  `git status`のログに`deleted main.c`が含まれているのを確認し、コミットする。

  ### 復元したいコミット履歴を特定する

  コミット履歴から復元する場合、どのコミット履歴を参照するかをしていなければならない。
  コミット履歴はコミットハッシュという特定するためのIDが設定されている。
  40文字の英数の文字列から構成されるが、重複がなければ上から7,8文字分指定することでも参照可能。
  コミット履歴の確認コマンドは`git log`である。

  ```
  >git log
  >git log --oneline  #1コミット1行にまとめて表示
  ```

  1行目が新しいコミット内容で、順に古いコミットが表示されている。今回は2行目のコミットハッシュをコピーすればよい。

  ### コミットハッシュを用いて復活する

  復活させたいファイルが存在するIDを特定したので、これを用いて復活させる。
  `git checkout`でも復元可能だが、現在は`git restore`が推奨らしいのでこちらで実行する。

  ```
  >git restore -s <コミットハッシュ> main.c
  >dir
  ```
  
  main.cが復活しているか確認する。
  ここで、`git status`で作業ディレクトリの確認をすると、削除したファイルが戻ってきたことを警告されるため、
  `git add`を使ってステージングしておくとよい。
  
</details>

<details>
  <summary>#1435 ブランチ</summary>

  &nbsp;  
  1つのソフトウェアに値して複数人でデバッグしたり機能追加を行ったりする場合がある。
  ブランチという分岐をつくることで別々の作業を同時に行い、最終的に1つに統合（マージ）することで開発を行っていく。
  今回はそのブランチ作成や移動などのコマンドを扱う。
  余談だが、ブランチ名を汎用的な名前（fixなになに）などにすると名前が重複する場合があるので、
  _<イニシャル>などを付して重複を避けるのが無難。

  ## ブランチに関する操作

  ### ブランチを作成する
  ブランチ作成のコマンドは`git branch`を用いる。

  ```
  >git branch hoge
  >git branch  #ブランチの内容を確認できる
  ```

  ブランチがmainとhogeの2つあることが確認できた。現在いるブランチはアスタリスクと文字色変更で強調表示されている。

  ### ブランチを移動する

  現在mainブランチにいるはずなので、hogeブランチに移動する。
  先述のとおり、`git checkout`コマンドを使えばよいが、`git switch`コマンドでも移動できる（個人的には`git switch`推奨）。

  ```
  >git checkout hoge
  >git switch hoge  #どちらかを実行
  >git branch
  ```

  `git branch`でhogeブランチにいることを確認する。
  また、次の作業にむけて`test.txt`を作成しコミットしておく。

  ### ブランチ名の変更

  ブランチ名の変更には`git branch`コマンドの`-m`オプションを用いる。
  変更対象のブランチ名と変更後のブランチ名が必要だが、今いるブランチの名前を変更する分には
  変更後のブランチ名のみでも実行可能。

  ```
  >git branch -m hoge feature
  >git branch
  ```
  
  `git branch`でブランチ名がhogeからfeatureに変更されていることを確認する。
  また、mainブランチに切り替え、`dir`コマンドでtest.txtファイルが存在しないことを確認すれば終了とする。  
  補足：他ブランチのファイル内容を確認したいとき、現在のブランチを変えずに確認するコマンドとして、`git ls-tree`がある。
  例えば`>git ls-tree feature`とすれば、mainブランチにいながらfeatureブランチの内容を確認できる。

</details>

<details>
  <summary>#1436 マージ</summary>

  ## マージする

  `git merge`コマンドを用いてfeatureブランチをmainブランチへマージする。
  `git merge`は**現在のブランチ**に指定するブランチを合体させるイメージなので、mainブランチにいるかを確認しておくこと。
  また、コミットまであわせて行われる（マージコミットと呼ぶ）ため、`-m`オプションでコメントを残すとよいだろう。
  `-m`のほかにも有用なオプションが存在しているので確認しておくとよいだろう
  （参考：[[Git] mergeコマンドの復習](https://qiita.com/yam_dev/items/47bd70e7582b14154541)）。

  ```
  >git merge feature -m "fugafuga"
  >dir
  ```

  mainブランチにtest.txtがあることを確認する。

  ## ブランチの削除

  featureブランチで開発したファイルは統合されたので、featureブランチを削除する。
  ブランチの削除は`git branch`コマンドに`-d`オプションを利用すればよい。

  ```
  >git branch -d feature
  >git branch
  ```

  featureブランチが存在しないことを確認して終了。

</details>

<details>
  <summary>#1437 コンフリクト</summary>
  
  &nbsp;  
  開発環境では、複数ブランチで同一のファイルを操作することがある。あるファイルをマージした際に
  別の変更がされていると、どちらの修正を優先すればよいかgitには判断できない。
  その場合、コンフリクトとして解決するようにgit側から注意される。
  今回は意図的にコンフリクトを起こし、対応のデモを行う。

  ## コンフリクトが起きるマージを行う

  チケットのマージ作業までのコマンドは省略する。`git merge feature`とすると、下記のようなログが表示されるはずだ。

  ```
  Auto-merging main.c
  CONFLICT (add/add): Merge conflict in main.c
  Automatic merge failed; fix conflicts and then commit the result.
  ```
  
  ここでmain.cをVSCで開くと、下記のようになっている。

  ```
  <<<<<<< HEAD (現在の変更)
  // main
  =======
  /* main */
  >>>>>>> feature (入力側の変更)
  ```

  HEAD行から=======までがmainブランチの変更、=======からfeature行までがfeatureブランチの変更を示している。
  指示通り当該行を削除し、保存する。
  mainブランチのmain.cを修正したので、これをステージング、コミットし、コミット履歴を確認して終了とする。
  
</details>

<details>
  <summary>#1438 フォーク/ #クローン</summary>

  &nbsp;  
  フォークについては、GitHub上で行う作業のため、ここでは省略する。

  ## フォークしたリポジトリをクローンする
  
  フォークしたGitHubのURLを取得する。そのURLを指定して`git clone`コマンドでクローンする。

  ```
  >git clone <URL>
  >git remote -v
  ```

  `git remote`コマンドでURLを確認することも可能。
  `git remote add`とし、リモート名とURLを指定すると、手動で設定することも可能である。
  リモート名は`origin`と`upstream`が一般に使われる。
  
</details>

&nbsp;  
&nbsp;  

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

ということで怒られたわけですが、エラーの内容が異なります。色々調べましたが、どうやらGitのバージョンを戻す場合、リポジトリの履歴が一致しないため反映ができないとのこと。そこで先述のサイトにたどり着き、`git push origin <ブランチ名> --force`で無理やりpushしたながれになります。

ちなみに` ! [rejected]        main -> main (non-fast-forward)`で検索すると分岐ブランチを設定してクリアしているページなども見つかりましたがうまくいきませんでした。

</details>

