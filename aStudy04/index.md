%%%%%
% Slide Show Headers

title: 俺様の考えた最強のCUI環境
author: hoshina85

%%%%%%%%%%%

% Slides Start Here

#別に最強じゃないです

デザイナや他のエンジニアにこのツール使えよ捗るぞ。って言いたいだけです。

#zsh

ご存知z shell。bashの拡張版みたいなもん

* zshはじめました
* なんでもできるよ！
* なんでも設定しないといけないよ

#zsh / auto-fu.zsh

https://github.com/hchbaw/auto-fu.zsh

自動補完プラグイン

* Tabすら押さない横着プラグイン
* hoge/とhoge-2/があると後者まで一気に補完しやがる憎めない奴
* クォーてションや設定で回避してください

#zsh / z

https://github.com/rupa/z

cdの拡張。過去に移動したとこに飛べるコマンド

* z config -> cd /home/User/webapps/app/protected/config
* コマンドの1〜2割はcd
* autojumpもいいけどインストール面倒だよねアレ

#tig

https://github.com/jonas/tig

gitのコミットログツール

* gitを使うことを強いられているんだ！
* きれい！
* *tig blame*{: style="color: red"}で捗る犯人探し


#hub
http://defunkt.io/hub/

github専用コマンド

~~~~~~
$hub clone hoshina85/dotfiles
  -> git clone git://www.github.com/hoshina85/dotfiles
~~~~~~

* *hub create*{: style="color: red"}でリモートリポジトリ作れるのは便利だなー


#weechat

http://www.weechat.org/

CUIで使えるIRCクライアント

* プラグインが豊富！
* 軽い！
* 使いやすいかはまあ置いておく

#余談:githubでdotfiles管理

ホームにdotfiles/とかつくって.vimrcや.zshrcやらをgitで管理すると捗る

#余談:githubでdotfiles管理/リポジトリ作成

例えばホームの.vimrcをdotfiles/vimrcに移す

~~~~~~
mkdir ~/dotfiles
mv ~/.vimrc ~/dotfiles/vimrc
ln -s ~/dotfiles/vimrc ~/.vimrc
hub create
~~~~~~

#余談:githubでdotfiles管理/リモートに

リポジトリ初期化したらhubコマンドでガッといける

~~~~~~
cd ~/dotfiles
git init
git add .;git commit -m "initial commit"
hub clone
~~~~~~

#余談:githubでdotfiles管理/捗る
* .bashrcや.jslintや.screenecやらたくさんできるのでどんどんぶち込みましょう
* とりあえず設定して失敗してもgitなら戻せるよ
* ちなみにbashrcとかの設定失敗してsshログインした瞬間落とされるようなときってどうしたらいいんでしょうね。怖い。
* .ssh/\*系はちょっとセキュアな内容なので含めちゃだめよ。
* べつにDropBoxとかでもいいけど


#余談2:markdownでスライド

今回のスライドはgemのslideshowでつくりました

https://github.com/geraldb/slideshow

markdownで書けるのが素晴らしいですね。
deck.jsやshower、html5slide等のJSスライドにも吐き出せます

#おしまい

スライドはgithubで公開してます

https://www.github.com/hoshina85/slide/

