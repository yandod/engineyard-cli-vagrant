# 概要

なんらかの理由でローカル上にgemをインストールする環境が作れない場合に<code>engineyard</code>gemを使う為の踏み台環境を作るVagrantfileです。

## 事前条件

- VirtualBox 4.2.12+
- Vagrant 1.3.x

## 使い方

このリポジトリをクローンし、クローンしたディレクトリ内でVagrantを起動すれば<code>ey</code>コマンドの使えるUbuntu環境が起動します。初回利用時はey loginでWebで登録したメールアドレスとパスワードを入力してください。

<pre>
git clone https://github.com/yandod/engineyard-cli-vagrant.git
cd engineyard-cli-vagrant
vagrant up
vagrant ssh
ey login
</pre>

SSH接続を必要とするデプロイなどを行うには秘密鍵と公開鍵の設定が必要になります。まだWebに登録した鍵が無い場合や、新しい鍵を使いたい場合は仮想マシン内で鍵ペアを作成し、公開鍵をWebに登録してください。

<pre>
ssh-keygen
cat ~/.ssh/id_rsa.pub
(ここに表示される鍵をWebから登録する)
</pre>

すでにEngine Yardのダッシュボードで登録した公開鍵がある場合は対応する秘密鍵をVagrantの仮想マシン内にコピーすることもできます。。

<pre>
cd engineyard-cli-vagrant
cp ~.ssh/id_rsa .
vagrant ssh
cp /vagrant/id_rsa ~.ssh/
</pre>

## FAQ

- 仮想マシンが起動しない
	- 32ビットOSの場合はpresice64ではなくpresice32を使うようにVagrantfileを修正してください。
- 処理が遅い
	- 本来はローカル環境にRubyを導入して<code>engineyard</code>Gemを導入するのが本道です。Gemの導入ができるようにする適切な方法はお使いのOSや開発ツールによって非常に多彩です。解消方法がわからない場合の避難措置がこの仮想マシンと考えて下さい。 