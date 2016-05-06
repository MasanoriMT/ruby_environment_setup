ruby_environment_setup
===============

rbenvのセットアップとかをメモ

## 本家サイト

https://github.com/rbenv/rbenv

## インストール

インストールにはHomebrewを利用した。  
ruby-buildも一緒にインストールされるようです。rbenv root

    $ brew update
    $ brew install rbenv

http://takatoshiono.hatenablog.com/entry/2015/01/09/012040

## .bash_profileを編集

以下を追加。  
こうすることで、`~/.rbenv/shims`にパスが通る。

    eval "$(rbenv init -)"

## rubyのインストール

インストール可能なバージョンを調べて、

    $ rbenv install -l

適当なバージョンのrubyをインストール。

    $ rbenv install 2.3.1

## gemのインストール

以上の手順を踏むと、gemコマンドは、以下のパスのものが使われるようになる。

    $ which gem
    /Users/matoh/.rbenv/shims/gem

例えば、bundlerをインストールすると、

    $ gem install bundler
    Fetching: bundler-1.11.2.gem (100%)
    Successfully installed bundler-1.11.2
    Parsing documentation for bundler-1.11.2
    Installing ri documentation for bundler-1.11.2
    Done installing documentation for bundler after 3 seconds
    $ which bundler
    /Users/matoh/.rbenv/shims/bundler

というように、shims配下にインストールされる。

## rbenv-binstubsの導入

bundlerを利用する際、`bundle exec`を付与しないで済むように、 rbenv-binstubsを導入します。

    $ mkdir -p ~/.rbenv/plugins
    $ cd ~/.rbenv/plugins
    $ git clone https://github.com/ianheggie/rbenv-binstubs.git
