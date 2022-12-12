---
title: お知らせ
---

# お知らせ --- milter managerの歴史

## 2.2.5: 2022-12-12 {#release-2-2-5}

### milter manager

#### 修正

  * `netstat`関連のエラーが発生する問題を修正しました。
    [GH-176] [Christianさんが報告]

### milter client

#### 改良

  * `milter.run_gc_on_maintain=`という設定を追加しました。

#### 修正

  * 生きている`Milter::ClientSession`がGCされるかもしれない問題を修正しました。

### 感謝

  * Christianさん

## 2.2.4: 2022-12-10 {#release-2-2-4}

### パッケージ

#### 修正

  * deb: manの場所が間違っていた問題を修正しました。

  * deb: `Conflicts`の設定を修正しました。

### ドキュメント

#### 改良

  * AlmaLinux 8: 漏れていた`dnf module -y enable ruby:3.0`を追加しました。
    [milter-manager-users-ja]
    [ymatsukiさんが報告]

  * AlmaLinux 8: 不要な`milter_mail_macros`の変更を削除しました。
    [milter-manager-users-ja 61]
    [ymatsukiさんが報告]

### milter manager

#### 改良

  * libevとの連携を改良しました。

### 感謝

  * ymatsukiさん

## 2.2.3: 2022-10-04 {#release-2-2-3}

### Python

#### 改良

* <code>milter.client.SessionContext</code>に<code>fallback_status</code>を設定す    るようにしました。

#### 修正

* エラー発生時に<code>fallback_status</code>が使われないことがある問題を修    正しました。

## 2.2.2: 2022-10-04 {#release-2-2-2}

### パッケージ

#### 修正

* deb: アップグレードが失敗する問題を修正しました。

### milter server

#### 改良

* 警告を抑制するために漏れていた<code>NULL</code>チェックを追加しました。

### Python

#### 修正

* ロガーの例外出力機能がPython 3.8で動かない問題を修正しました。

## 2.2.1: 2022-09-29 {#release-2-2-1}

### パッケージ

#### 修正

* deb: アップグレードに失敗する問題を修正しました。    [GitHub#176][Kazuhiro NISHIYAMAさんが報告]

### Python

#### 修正

* Python 3.8でmilter clientが動かない問題を修正しました。

### 感謝

* Kazuhiro NISHIYAMA

## 2.2.0: 2022-09-29 {#release-2-2-0}

### パッケージ

#### 修正

* ubuntu: まちがったソースアーカイブを使っていた問題を修正しました。

## 2.1.9: 2022-09-29 {#release-2-1-9}

### Python

#### 改良

* Python 3.8に対応しました。
* client: <code>--version</code>オプションを追加しました。

## 2.1.8: 2022-09-28 {#release-2-1-8}

### パッケージ

#### 修正

* deb: PythonとGObject Introspection関連のモジュールが使えなかった問    題を修正しました。

## 2.1.7: 2022-09-28 {#release-2-1-7}

### パッケージ

#### 改良

* AlmaLinux 8に対応しました。
* AlmaLinux 9に対応しました。
* Ubuntu 18.04の対応をやめました。
* 部分的にMesonに対応しました。
* deb: GObject Intospectionに対応しました。

### すべて

#### 改良

* GLib 2.46から<code>g_mem_set_vtable()</code>が非推奨になっていたのでメモ    リープロファイル機能を削除しました。
* GLib 2.50以降が必須になりました。
* GObject Introspectionに対応しました。
* いくつかAPI/ABI非互換な変更が入りました。そのため、共有ライブラリー    のバージョンを<code>0</code>から<code>2</code>にあげています。
  * <code>milter_macros_requests_foreach()</code>: <code>GHFunc</code>の代わりに      <code>MilterMacrosRequestFunc</code>を使うようになりました。
  * <code>milter_client_processing_context_foreach()</code>: <code>GFunc</code>の      代わりに<code>MilterClientContextFunc</code>を使うようになりました。      （これはAPI非互換なだけです。）
* libevのバンドルをやめました。
* Ruby/GLib2、Ruby/GIO2、Ruby/GObojectIntrospectionのバンドルをやめ    ました。

### milter core

#### 改良

* <code>milter_logger_get_default()</code>を追加しました。
* <code>milter_logger_log_literal()</code>を追加しました。

### milter client

#### 改良

* <code>MilterClientContext</code>:
  * チャンクを<code>GBytes</code>として受け取る<code>body-bytes</code>シグナルと      <code>end-of-message-bytes</code>シグナルを追加しました。
  * ↑の<code>GBytes</code>版シグナルを使うための<code>use-bytes</code>プロパティーを      追加しました。
  * <code>milter_client_context_get_use_bytes()</code>を追加しました。
  * <code>milter_client_context_set_use_bytes()</code>を追加しました。
  * <code>milter_client_context_replace_body_bytes()</code>を追加しました。

### milter server

#### 改良

* <code>milter-server.pc</code>に<code>milter_test_server</code>変数を追加しました。
* <code>milter-test-server</code>:
  * milterに接続できなかった場合は0以外の終了コードを返すようになり      ました。
  * デフォルトで<code>i</code>はPostfixと同じように送るようになりました。
    * 変更前：<code>i</code>を「MAIL」と「end-of-message」のときに送信。
    * 変更後：<code>i</code>を「DATA」と「end-of-header」と「end-of-message」        のときに送信。

### milter-manager-log-analyzer

#### 改良

* Ruby 3.2に対応しました。

### Python

#### 改良

* GObject Introspectionベースのバインディングを追加しました。milter    をPythonで実装できます。

## 2.1.6: 2022-01-13 {#release-2-1-6}

### Document

#### 改善

* packagecloud.ioからの支援を受けているのでブログ記事を公開しました

#### 修正

* milter-regexのWebサイトのURLを修正しました [OBATA Akioさんが報告][GitHub #140]

### Package

#### Improvements

* CentOS 8のサポートをやめました
* Debian stretchのサポートをやめました
* Ubuntu 16.04 (xenial) のサポートをやめました
* Ubuntu 19.04 (disco) のサポートをやめました
* glib2 3.5.0 gem、gobject-introspection 3.5.0 gem、gio 3.5.0 gem、    pkg-config gem、native-package-installer gemをバンドルしました

### milter manager

#### 改善

* <code>--with-bundled-ruby-gobject-introspection</code>: バンドルした    gobject-introspection gemを使えるようにしました
* <code>--with-bundled-ruby-gio2</code>: バンドルした    gio2 gemを使えるようにしました
* <code>milter-performance-check</code>: 複数回<code>--from</code>を指定できるようにしました

#### 修正

* milter-managerがクラッシュする不具合を修正しました [BugbearRさんが報告][GitHub #146]    この不具合は型定義の誤りにより意図せず発生していました。

### 感謝

* OBATA Akioさん
* BugbearRさん

## 2.1.5: 2019-09-10 {#release-2-1-5}

### Document

#### 改善

* CentOS 7でのインストールマニュアルを更新しました
* ClamAV 0.100.0で非推奨となったAllowSupplementaryGroupsの設定を削除しました

#### 修正

* 設定のドキュメントの使用例が "Authentication" となっていた誤記を修正しました [SATOH Kiyoshiさんがパッチ提供][GitHub #138]
* database.host が設定のドキュメントに抜けているのを修正しました [SATOH Kiyoshiさんが報告]

### Package

#### 改善

* CentOS 6のサポートをやめました
* メールの本文を置き換えるRubyのmilterスクリプトのサンプルを追加しました

#### 修正

* パッケージの更新に失敗することがないようにUbuntuのコード名ではなくバージョンをパッケージのバージョンにつけることにしました    [西山さんが報告][GitHub #137]

### 感謝

* 西山和弘さん
* SATOH Kiyoshiさん

## 2.1.4: 2018-07-06 {#release-2-1-4}

### Document

#### Fixes

* 日本語ドキュメントを正しくインストールできるようにした    [Reported by OBATA Akio][GitHub #136]

### 感謝

* おばたさん

## 2.1.3: 2018-07-05 {#release-2-1-3}

### Document

#### Fixes

* 日本語ドキュメントを復活した [Reported by OBATA Akio][GitHub #136]

### 感謝

* おばたさん

## 2.1.2: 2018-07-03 {#release-2-1-2}

### Package

#### 改善

* Ubuntu Yakkety Yak (16.10) のサポートをやめました
* Ubuntu Zesty Zapus (17.04) のサポートをやめました
* Ubuntu Artful Aardvark (17.10) のサポートを追加しました
* Ubuntu Bionic Beaver (18.04) のサポートを追加しました
* Debian Jessie のサポートをやめました
* CentOS6で使うRubyを2.3.5に更新しました

### milter manager

#### 修正

* Rspamd の自動検出に失敗する問題を修正しました [Reported by whyscream][GitHub #128]

### Known issues

* milter-manager の子 milter として rspamd_proxy を使うことができない [GitHub #134]

### 感謝

* whyscreamさん

## 2.1.1: 2017-06-27 {#release-2-1-1}

### Package

#### 改善

* Ubuntu Precise Pangolin (12.04) サポートをやめました
* Ubuntu Zesty Zapus (17.04) サポート追加
* Debian Buster サポート追加

### milter core

#### 改善

* binding ruby: 同梱している ruby-gnome2 を 3.1.1 に更新しました

### milter manager

* [Rmilter](https://rspamd.com/rmilter/)の自動検出をサポートしました (実験的)
  * Rspamd 1.6 以降では非推奨なので[Rspamd proxy](https://rspamd.com/doc/workers/rspamd_proxy.html)を使用してください
* [Rspamd proxy](https://rspamd.com/doc/workers/rspamd_proxy.html)の自動検出をサポートしました (実験的)

## 2.1.0: 2016-11-21 {#release-2-1-0}

2.0.9 のバクフィックスリリースです。

プロジェクトのサイトを sourceforge.net から OSDN に移行しました。

* https://milter-manager.osdn.jp/

OSDN上では、以下の機能を利用します:

* ウェブサイト
  * milter-manager.sourceforge.net から milter-manager.osdn.jp に移行しました
* ファイルリリース
  * 過去に sourceforge.net にリリースしたファイルは全て移行しました
* メーリングリスト
  * 登録済みメンバーの移行は行いました
  * アーカイブの移行は行いません
* ニュース
  * sourceforge.net には無い機能でした

パッケージの配布場所は以下の通りです:

* Ubuntu 向けの deb パッケージ: launchpad.net
* Debian 向けの deb パッケージ: packagecloud
  * 移行方法: https://packagecloud.io/milter-manager/repos/install
* RPMパッケージ: packagecloud
  * 移行方法: https://packagecloud.io/milter-manager/repos/install
* tar ball: OSDN
  * https://osdn.net/projects/milter-manager/releases/

### Package

#### 改善

* Ubuntu Yakkety (16.10) サポート追加

### milter manager

#### 修正

* CentOS7でホストを再起動したときに自動的に起動しない問題を修正した
* FreeBSD で milter-greylist のデフォルトの設定ファイルのパスを修正した    [OBATA AkioさんがPull request][GitHub #99]

#### 改善

* DNSBLを利用する適用条件を追加した    [Yuto HayamizuさんがPull request][GitHub #108]

### milter client

#### 修正

* --n-workers=1 以上を指定すると起動しない問題を修正した

### milter server

#### 改善

* milter-test-server コマンドに --all-timeout オプションを追加した    [HorimotoYasuhiro さんがPull request][GitHub #101]

### 感謝

* おばたさん
* はやみずさん
* 堀本さん

## 2.0.9: 2016-06-15 {#release-2-0-9}

2.0.8 のバグフィックスリリースです。

### milter manager

#### 修正

* CentOS6, CentOS7 上で milter の自動検出を正しく動作するようにした

## 2.0.8: 2016-06-15 {#release-2-0-8}

2.0.7 のバグフィックスリリースです。

すでにmilter-managerをインストールしている場合、パッケージを更新する前に次の作業が必要です。

Debianの場合: /etc/apt/sources.list.d/milter-manager.listを更新する(以下はjessieの例です)

<pre>deb http://downloads.sourceforge.net/project/milter-manager/debian/stable jessie main
deb-src http://downloads.sourceforge.net/project/milter-manager/debian/stable jessie main</pre>

Ubuntuの場合: ppa:milter-manager/ppa を追加する

<pre>% sudo apt-get -y install software-properties-common
% sudo add-apt-repository -y ppa:milter-manager/ppa
% sudo apt-get update</pre>

CentOSの場合: milter-manager-releaseパッケージを1.3.0に更新する

<pre>% sudo yum install -y \
http://sourceforge.net/projects/milter-manager/files/centos/milter-manager-release-1.3.0-1.noarch.rpm</pre>

### Package

#### 修正

* debパッケージのlintianによるチェックで誤検出により警告がでていたの    を修正しました。[佐々木洋平さんがパッチを提供]
* debパッケージのビルド中に、ドキュメントを生成しなおすのに必要なファ    イルをdebian/ディレクトリ以下に保持するようにしました。これはdebパッ    ケージをクリーンビルドするのに必要です。[佐々木洋平さんがパッチを    提供]
* Debian向けのapt-lineを更新しました。SourceForge.netの仕様変更に対    応しています。/etc/apt/sources.list.d/milter-manager.listの更新が    必要です。
* Debian stretch 向けのAPTリポジトリを正しく生成するようにしました
* CentOS向けのmilter-manager-releaseパッケージを更新しました。    SourceForge.netの仕様変更に対応しています。1.3.0より古いバージョ    ンではyum updateでmilter-managerを更新できません。

#### 改善

* Debian wheezy のサポートをやめました
* Ubuntu Xenial (16.04 LTS) のサポートを追加しました
* Ubuntu Wily (15.10) のサポートを追加しました
* Ubuntu Vivid (15.04) のサポートを追加しました
* debパッケージでsystemdをサポートしました (Ubuntu Precise(12.04) 以外)
* CentOS6で使うRubyを2.2.5にしました
* CentOS7でのsystemdサポートは安定しています
* CentOSのビルドスクリプトを整理しました    [Patched by Hiroshi Ohkubo][GitHub #92]

### milter manager

#### 修正

* milter-manager-log-analyzerで未定義の値は0として扱うようにしました。    RRDtool 1.5でエラーになっていた不具合を修正しています。[Dave Doddさんが    報告][milter-manager-users-en]
* milter-manager-log-analyzerでデータソース名に"-"ではなく、"_"を使    うようにしました。これはRRDtool 1.5の不具合を回避するためです。    [Dave Doddさんが報告][milter-manager-users-en]
* configureのオプション--with-bundled-ruby-glib2がBSDで正しく動作し    ない不具合を修正しました。

### libmilter-compatible

#### 修正

* smfi_settimout()でタイムアウト値を正しく設定できない不具合を修正し    ました。

### Ruby milter

#### 修正

* --fallback-statusオプションの値が'temporary-failure'のときにエラー    が発生する問題を修正しました。[Nobuhiko MIYAHARAさんがパッチ提    供][GitHub #87]

### Document

#### 改善

* リファレンスのIntroductionにロシア語に翻訳されたドキュメントへのリ    ンクを追加しました。[Alisa Bagriiさんが翻訳]
* Debian/Ubuntuで最近のclamav-milterでは設定変更が不要になっているの    でそれにあわせてドキュメントを更新しました。[西山和弘さんが報    告][GitHub #90]
* Debian/Ubuntuではソケットを作成するディレクトリーをインストール時    に作成するように手順を追加しました。[西山和弘さんが報告][GitHub #91]

### 感謝

* 佐々木洋平さん
* Nobuhiko MIYAHARAさん
* Alisa Bagriiさん
* 西山和弘さん
* Dave Doddさん
* Hiroshi Ohkuboさん

## 2.0.7: 2015-11-30 {#release-2-0-7}

2.0.6 のバグフィックスリリースです。

### Package

#### 修正

* milter-manager(1)やhtmlのドキュメントの問題を修正しました

## 2.0.6: 2015-11-30 {#release-2-0-6}

2.0.5 のバグフィックスリリースです。

### Package

#### 修正

* debパッケージの依存関係を修正しました    [Christian Useさんが報告][milter-manager-users-en]

#### 改善

* Debian stretch のサポートを追加しました
* Ubuntu Vivid (15.04) のサポートを追加しました
* Ubuntu Wily (15.10) のサポートを追加しました
* Ubuntu Lucid (10.04) のサポートをやめました
* Ubuntu Saucy (13.10) のサポートをやめました
* Ubuntu Utopic (14.10) のサポートをやめました
* CentOS6 で使うRubyを2.2.3にしました
* CentOS7 で systemd サポートを追加しました(実験的)

### milter manager

#### 改善

* バンドルしている libev のバージョンを 4.19 にしました
* バンドルしている ruby-glib2 のバージョンを 2.2.5 にしました

### milter core

#### 改善

* --log-level オプションと--log-itemオプションでパイプで区切って複数の値を指定できるようにしました    [とみたまさひろさんが報告]
* ログの出力先がファイルの場合、デフォルトでは色を付けないようにしました    [とみたまさひろさんが報告][GitHub #58]

### Ruby milter

#### 改善

* Milter::ServerContext#negotiate を追加しました
* Milter::ServerContext#data を追加しました
* Milter::ServerContext#abort を追加しました
* Milter::ServerContext#quit を追加しました
* Milter::ServerContext#reset_message_related_data を追加しました
* Milter::Headers と Milter::Header を追加しました
* Milter::Status#pass? を追加しました
* sample/milter-test-server.rb を追加しました

### Document

#### 修正

* タイポの修正    [佐々木洋平さんがパッチを提供][GitHub #82]

### 感謝

* とみたまさひろさん
* Christian Useさん
* 畑ケ宇宙さん
* Toshio Makiさん
* 佐々木洋平さん

## 2.0.5: 2014-12-09 {#release-2-0-5}

2.0.4 のバグフィックスリリースですが、実験的な機能としてメールトランザクション(STMPコマンドのMAILからDATAの終わりまで)の間、データを保持できる実験的なAPIを追加しました。

### Package

#### 改善

* CentOS5 のサポートをやめました
* CentOS7 のサポートを追加しました
* Ubuntu Saucy (13.10) のサポートをやめました
* Ubuntu Utopic (14.10) のサポートを追加しました
* debパッケージをクリーンルームビルドするようにしました    [佐々木洋平さんがパッチを提供][milter-manager-users-ja:00224]
* ruby-glib2 の自動検出方法を改善しました    [佐々木洋平さんと西山和弘さんが提案][milter-manager-users-ja:00243]
* libev を必須にしました    [おばたさんが報告][GitHub #48][GitHub #49]
* CentOS6 で使うRubyを2.1.5に更新しました

### milter manager

#### 修正

* milter manager から読み込むファイルを常にUTF-8と見做すようにした    [Panagiotis Skarvelis さんが報告][SF.net #6]

### milter-client

#### 改善

* メールトランザクションの間、データを保持できるAPIを追加しました(実験的)

### Ruby milter

#### 改善

* Ruby1.8のサポートをやめました
* メールトランザクションの間、データを保持できるAPIを追加しました(実験的)

#### 修正

* シングルプロセスで起動したとき、シグナルハンドラがセットアップでき    ていなかった問題を修正 [GitHub #53]

### Document

#### 修正

* FreeBSD で sa-spamd を起動する前に sa-update を実行するようにしました    [川崎さんが報告][milter-manager-users-ja:00250]

### 感謝

* 佐々木さん
* 西山さん
* おばたさん
* Panagiotis Skarvelis さん
* 川崎さん

## 2.0.4: 2014-06-20 {#release-2-0-4}

2.0.3 のバグフィックスリリースです。

### Ruby milter

#### 改善

* Milter::Client::Test::MilterRunner を追加しました
* Milter::Client::EnvelopeAddress を追加しました

#### 修正

* 複数のCPUを使用している環境でRubyで書かれたmilterが正常終了できない問題を修正しました

## 2.0.3: 2014-05-20 {#release-2-0-3}

2.0.2 のバグフィックスリリースです。

### Package

#### 改善

* Ubuntu Quantal (12.10) のサポートをやめました
* Ubuntu Raring (13.04) のサポートをやめました
* Ubuntu Trusty (14.04) のサポートを追加しました
* Debian squeeze のサポートをやめました
* rpm: CentOS6 向けの Ruby を Ruby1.9.3-p545 に更新しました。

### milter manager

#### 改善

* バンドルしている libev のバージョンを 4.15 にしました

#### 修正

* data_stopper が子 milter の適用を止められないバグを修正しました    [GitHub #39]

### Ruby milter

#### 改善

* バンドルしている glib2 のバージョンを 2.2.0 にしました
* Milter::Logger のメソッドがブロックを受け付けるようにしました

### Document

#### 修正

* FreeBSD へのインストールに関するタイポを修正しました    [Dave Dodd さんがパッチを提供]

### 感謝

* Dave Dodd さん

## 2.0.2: 2014-01-27 {#release-2-0-2}

2.0.1 のバグフィックスリリースです。

### パッケージ

#### 修正

* Ubuntu Lucid (10.04) サポートを復活    [荻野 充さんが報告][milter-manager-users-ja:00229]

### 感謝

* 荻野 充さん

## 2.0.1: 2014-01-24 {#release-2-0-1}

2.0.0 のバグフィックスリリースです。

### milter manager

#### 改善

* SIGUSR1 シグナルを受け取るとログファイルを開き直すようにしました。

#### 修正

* 全てのユーザーにとって安全ではないため、クラッシュしたときに    スタックトレースを表示する機能を廃止しました。 [GitHub #38]

### milter-core

#### 改善

* 環境変数 MILTER_LOG_PATH でログファイルのパスを変更できるようにしました。

### milter-client

#### 改善

* --log-path オプションを追加しました。

### Ruby milter

#### 改善

* --log-path オプションを追加しました。
* SIGUSR1 シグナルを受け取るとログファイルを開き直すようにしました。

### パッケージ

#### 改善

* Ubuntu Lucid (10.04) のサポートをやめました。
* Ubuntu Saucy (13.10) のサポートを追加しました。
* deb: Debian 上で Ruby 2.0.0 を検出できるようにしました。
* rpm: CentOS6 向けの Ruby を Ruby1.9.3-p484 に更新しました。
* 自動生成するファイルを配布用アーカイブから削除しました。    [佐々木洋平さんが報告][milter-manager-users-ja:00225]

### ドキュメント

#### 改善

* 最新の milter-greylist の RPM パッケージを使うようにしました。    [Reported by ishizaka tadanoriさん][milter-manager-users-ja:00220]
* 英語版のドキュメントを改善しました。    [GitHub #17]

### 感謝

* 佐々木洋平さん
* ishizaka tadanoriさん

## 2.0.0: 2013-07-25 {#release-2-0-0}

約2年ぶりのメジャーバージョンアップリリースです！

メジャーバージョンアップリリースだからといって非互換があるわけではありません。1.8系とは互換性があるため、設定ファイルを変更せずにそのまま簡単にアップデートできます。

前回のリリースから大きな変更もないのにどうしてメジャーバージョンをあげて2.0.0にしたかというと、開発が継続していることと安定していることをアピールするためです。

milter managerは約25ヶ月前の2011/06/10に前回のマイナーバージョンである1.8.0をリリースしました。そこから、10回目のリリースが今回のメジャーバージョンアップリリースです。長いときでリリースの間が6ヶ月あいたこともありましたが、こつこつと改良を続けてきました。この間のマイナーバージョンがあがるリリースは既存のmilter managerユーザーが見えるところでだけアナウンスしているため、既存のmilter managerユーザー以外には開発の様子が見えづらいものです。しかし、こうしてこつこつと開発を継続しています。メジャーバージョンアップというのは大きなイベントです。これを機に、既存のmiltermanagerユーザー以外にも広くアピールします。milter managerの開発が継続していて、より便利になり、また、より安定したことをアピールします。

より安定したことをアピールすると書いた通り、1.8.0の頃よりさらに安定しました。これは、動作実績が増え、ユーザーのみなさんから問題を報告してもらったおかげです。問題を教えてもらえたのでさまざまな問題を修正できました。milter manager本体はもちろんですが、Rubyでmilterを書くための機能であるRuby/milterはかなり安定しました。Rubyでmilterを実装する機会が増え、さまざまなノウハウが溜まりました。これらのノウハウがRuby/milterに反映されています。

2.0.0は1.8.0よりも確実によくなっていると自信を持って言えます。これまでmilter managerを使ったことがなかったみなさんもぜひ試してみてください！

### milter-test-server

#### 改善

* 複数行のヘッダをサポート。 [GitHub #33]

### Ruby milter

#### 修正

* envelope recipient で reject や temporary failure したときにも    reset を呼んでいた問題を修正。

## 1.8.9: 2013-06-28 {#release-1-8-9}

1.8.8 のバグフィックスリリースです。

### パッケージ

#### 改善

* [rpm] CentOS6 向けに提供している Ruby1.9.3 は 2013-06-27 にリリース    された Ruby1.9.3-p448 に更新。

### milter manager

#### 修正

* [binding][ruby] milter-greylist の自動検出で greylist.conf の    ソケットのパスにパーミッションが書かれているとソケットのパスを検出    できなかった問題を修正。

## 1.8.8: 2013-06-25 {#release-1-8-8}

1.8.7 のバグフィックスリリースです。

### パッケージ

#### 修正

* [rpm] cron の設定ファイルが milter-manager-log-analyzer ではなく    milter-manager に含まれていた問題を修正。    [坂下聡さんが報告][milter-manager-users-ja:00200]
* [deb] 古い設定ファイルが削除されていなかった問題を修正。    [佐々木洋平さんが報告][milter-manager-users-ja:00202]

### 既知の問題

* [test] いくつかの環境で rrdtool を使用しているテストが失敗する問題。    [山口さんが報告][GitHub #29]

### 感謝

* 坂下聡さん
* 佐々木洋平さん
* 山口さん

## 1.8.7: 2013-06-14 {#release-1-8-7}

1.8.6 のバグフィックスリリースです。

### パッケージ

* [rpm] 更新時にユーザーの設定を上書きしないように修正。
* [deb][rpm] milter-manager-log-analyzer を milter-manager から分離。    [西山和弘さんが報告][GitHub #21]
* CentOS6 以降ではRuby1.9を使用するように変更。
* Ubuntu Oneiric Ocelot(11.10) のサポートを削除。
* Ubuntu Raring Ringtail(13.04) のサポートを追加。
* Debian jessie サポートを追加。

### milter manager

#### 改善

* Ruby2.0.0 をサポート。

#### 修正

* [debian] non-ASCII な文字列を含む設定ファイルをサポート。    [西山和弘さんが報告][GitHub #23]

### milter-manager-log-analyzer

#### 修正

* ログに不正なバイト列を含む場合でも処理できるようにした。    [坂下聡さんが報告][GitHub #24]

### Admin

* 削除。

### 感謝

* 西山和弘さん
* 坂下聡さん

## 1.8.6: 2013-03-07 {#release-1-8-6}

1.8.5 のバグフィックスリリースです。

### milter-core

#### 改良

* [core][event-loop] イベントループを独自にカスタマイズするための    APIを提供。

#### 修正

* [core][event-loop] Ruby 1.9でlibevバックエンドが動作しない不具合を    修正。

### milter manager

#### 改良

* 設定項目としてmax-pending-finished-sessionsを追加。    終了したmilterのセッションのうち、リソースの開放待ちになっているも    のが一定数を超えたら強制的に開放できるようにします。

### milter-client

#### 改良

* --max-pending-finished-sessionsオプションを追加。

### Ruby milter

#### 改良

* Rubyからイベントループを独自にカスタマイズするためのAPIをサポート。
* manager.max_pending_finished_sessions設定項目をサポート。
* トランザクション終了のタイミングで呼ばれるリセット用のAPIを追加。    メールのトランザクションごとに作られるインスタンスの情報が    トランザクション間で意図せず共有されないようにするために使用します。

### Document

#### 改良

* manager.max_pending_finished_sessionsのドキュメントを追加。
* トランザクションをリセットするAPIのドキュメントを追加

#### 修正

* manager.maitenance_intervalの既定値を正確な値に修正した

## 1.8.5: 2012-12-03 {#release-1-8-5}

1.8.4 のバグフィックスリリースです。

### Package

* Ubuntu Natty Narwhal サポートを削除。
* ドキュメントが壊れていた問題を修正。

### Ruby milter

* Ruby1.8向けのテストのタイポの修正。    [umq さんが Pull request]

### 感謝

* umq さん

## 1.8.4: 2012-11-21 {#release-1-8-4}

1.8.3 のバグフィックスリリースです。

### Package

* Ubuntu Quantal Quetzal サポートを追加。
* 以下のディストリビューションで Ruby1.9 を使用してビルドしたパッケージを提供。    Debian wheezy, Debian sid, Ubuntu Precise Pangolin, Ubuntu Quantal Quetzal
* ソースコードの tar.gz にテストに必要なフィクスチャファイルを含めるようにした    [山口さんが報告]
* Solaris: ソースコードの tar.gz に SMF のメソッドファイルを追加。    [@ftnk さんが報告]
* yum: yum レポジトリの RPM パッケージ名を変更。    milter-manager-repository -&gt; milter-manager-release
* deb: デフォルトでは Ruby1.9 を使用するようにした
* deb: Ruby binding のパッケージ名を変更した    libmilter-*-ruby1.8 -&gt; ruby-milter-*

### milter manager

#### 改良

* configure: バンドルしている Ruby/GLib2 のバージョンを    --with-bundled-ruby-glib2 オプションで指定できるようにした。

#### 修正

* manager: コンパイラによる型の警告を抑制。    [GitHub #12]    [山口さんが報告]
* debian cron: mail.info ではなく mail.log を使うようにした。    [milter-manager-users-ja:00171]    [西山さん]

### milter-core

#### 改良

* MILTER_DEBUG=fatal-criticals のサポートを追加しました。
* binding ruby: milter のコールバック引数を ASCII_8BIT にした。    [GitHub #3]

#### 修正

* 高負荷で実行時に以下の警告が出力される問題を修正。    "g_io_channel_write_chars: assertion &#96;channel-&gt;is_writeable' failed"

### Admin

#### 改良

* Rails2.3.14 に更新

### Document

#### 修正

* CentOS 上のインストール手順ついて修正。    [GitHub #13]    [Kunkichi さんが報告]

### 感謝

* 山口さん
* 西山さん
* @ftnk さん
* Kunkichi さん

## 1.8.3: 2012-05-22 {#release-1-8-3}

1.8.2 のバグフィックスリリースです。

### Package

* [ubuntu] Ubuntu Precise Pangolin サポートを追加。
* [solaris] pkg-get のかわりに pkgutil を使用するようにした。    [GitHub #6]    [h0lzi さんが報告]

### milter manager

#### 改良

* binding ruby: 同梱している ruby-glib2 を 1.1.3 に更新。

#### 修正

* [manager] CentOS で manager.event_loop_backend = "libev" をサポート。    [塩野さんが報告]
* [manager][children] g_signal_connect() が gulong を返すので    guint ではなく gulong を使用するようにした。

### milter-core

#### 修正

* [libev] 次のIDが使用済みかどうかチェックするようにした。

### Document

#### 修正

* doc install debian ubuntu: postfix グループに関する設定を追加。    milter-manager ユーザは他の milter のソケットにアクセスするために postfix    グループに所属している必要がある。    [milter-manager-users-ja:00163]    [坂下さんが提案]
* doc debian: 最新の squeeze 環境に追従。    [坂下さんが提案]

### 感謝

* 坂下さん
* 塩野さん
* h0lzi

## 1.8.2: 2011-11-29 {#release-1-8-2}

1.8.1 のバグフィックスリリースです。

### milter-core

#### Fixes

* [event-loop][glib] 1.6.6 以降でのメモリリークを修正。
* [core] ヘッダを削除したときのメモリリークを修正。

## 1.8.1: 2011-11-12 {#release-1-8-1}

1.8.0 のバグフィックスリリースです。

manager.event_loop_backend と manager.n_workers は実用できるほどに安定しました!!

### パッケージ

* [ubuntu] Ubuntu Oneiric Ocelotサポートを追加。
* [centos] CentOS 6サポートを追加。
* パッケージの署名に使用する鍵を変更しました。

### milter manager

#### 改良

* sendmail 互換のための applicable-condition で100 IP アドレス処理す    るごとに DNS のキャッシュをクリアするようにした。

#### 修正

* デーモンモードで起動するかどうか判定するために    milter_client_is_run_as_daemon() を使うようにした。    [おばたさんが報告]
* MILTER_MANAGER_RUBY_STOP_TIMER_THREAD_BEFORE_CLEANUP=yes がセットさ    れていたら Ruby の終了処理でクリーンアップの前にタイマースレッドの    処理をスキップするようにした。
* fork(2) の代わりに rb_fork() を使うようにした。    --daemon オプションが *BSD で動かなかった問題を修正。    [おばたさんが報告]
* 同梱している libev がビルドできなかった問題を修正。[川崎さんが報告]

### milter-core

#### 修正

* 空の FD を閉じるときの条件を修正。 [おばたさんが報告]

### milter-client

#### 改良

* 新規接続の受付を優先的に処理するようにした。

#### 修正

* イベントループバックエンドに GLib を使用しているとき、マスタープロ    セスが終了してもワーカプロセスが終了しない問題を修正。

### milter-server

#### 改良

* エラーメッセージに出力する情報を増やした。
* 名前が設定されていないオブジェクトをログ出力するときの表記を    "(unknown)"に統一した。

#### 修正

* 同一セッションで二番目以降の RCPT を受け付けない問題を修正。

### Ruby milter

#### 改良

* Milter::Client::Configuration::MilterConfiguration#name を追加。

#### 修正

* event_loop_created フックでイベントループを取得できなかった問題を修    正。
* 本文が 8bit の Shift_JIS であるメールを与えた場合に例外が発生する問    題を修正。
* 同梱している test-unit のファイルリストを更新した。[山口さんが報告]
* 同梱している Ruby/GLib2 では Ruby1.9 + Solaris10 の組合せで SEGV す    る問題を修正。

### milter-test-server

#### 修正

* クオートされた charset の検出方法を修正。[中田さんが報告]
* 複数行ヘッダのパースを修正。
* --mail-file オプションで与えたメールの改行コードを変換しないように    した。

### ドキュメント

#### 改良

* 出力するログの説明を追加。
* タイポを修正。[鈴木さんが Pull request]

### milter manager admin

#### 改良

* Accept-Language が "ja" 以外のときは "en" をロケールとして使用する    ようにした。[Larry G. Wapnitsky さんが報告]

### 感謝

* 荻野充さん
* おばたさん
* 川崎さん
* 中田さん
* 山口さん
* 鈴木さん
* Larry G. Wapnitsky さん

## 1.8.0: 2011-06-10 {#release-1-8-0}

安定版1.8.x系最初のリリースです。

### 全体

#### 改良

* 使用していない変数を削除。

### パッケージ

#### 改良

* [debian] Debian GNU/Linux lennyサポートを削除。
* [debian] Debian GNU/Linux wheezyサポートを追加。
* [ubuntu] Ubuntu Hardy Heronサポートを削除。
* [ubuntu] Ubuntu Maverick Meerkatサポートを削除。
* [ubuntu] Ubuntu Natty Narwhalサポートを追加。
* [redhat] initファイル中で明示的にPIDファイルを指定するよ    うにした。
* [freebsd] /etc/rc.conf.local対応。    [川崎さんがパッチ提供]

#### 修正

* [debian] milter.rbが含まれていない問題を修正。    [荻野充さんが報告]

### milter manager

#### 改良

* [trust適用条件] ドメイン名を正規化するようにした。
* trust.clear設定項    目を追加。
* trust.load_envelope_from_domains    設定項目を追加。
* [trust適用条件] 組み込みの信用するドメインにezweb.ne.jpと    docomo.ne.jpを追加。
* negotiateのときでもfallback statusを使うようにした。
* manager.chunk_size    設定項目を追加。

#### 修正

* 子milter起動用プロセスが終了しない問題を修正。    [おばたさんが報告]
* 同一セッションで複数のメッセージを送った場合、子milterが    最初のメッセージでreject/temporary failure/discardを返す    と、2通目以降のメッセージが子milterに渡らない問題を修正。

### milter-core

#### 改良

* debugレベルよりも多くのログを出力するtraceレベルを追加。
* MILTER_LOG_LEVEL環境変数でのログレベルの指定時に+/-でロ    グレベルを追加・削除できるようにした。

#### 修正

* 読み込めるデータが残っているのにブロックしてしまう問題を    修正。

### Ruby milter

#### 改良

* [設定ファイル] エラー時に返すステータスのデフォルト値を    acceptにした。

### milter-performance-check

#### 改良

* CentOS 5対応。

### ドキュメント

#### 修正

* Ruby milterのバージョン確認にはMilter::TOOLKIT_VERSIONで    はなくMilter::VERSIONを使うようにした。    [荻野充さんが報告]

### 感謝

* 荻野充さん
* おばたさん
* 川崎さん

## 1.6.9: 2011-04-26 {#release-1-6-9}

1.6.8のバグフィックスリリースです。

### 全体

#### 改良

* bashでもautogen.shを動くようにした。    [Kenji Shionoさんが報告]

### ドキュメント

#### 改良

* Ruby milterの仕様変更に追従。    [akira yamadaさんが報告]

### milter manager

#### 改良

* database.extra_options    設定項目を追加。
* コールバック内で例外が発生した場合はログに出力するように    した。

#### 修正

* define_connection_checkerが例外を発生する問題を修正。    [Kenji Shionoさんが報告]

### milter-client

#### 改良

* UNIXドメインソケットのモードの変更に失敗したときにエラー    を通知するようにした。

### milter-performance-check

#### 改良

* --starttlsオプションの追加。
* --auth-userオプションの追加。
* --auth-passwordオプションの追加。
* --auth-mechanismオプションの追加。
* --auth-mapオプションの追加。

#### 修正

* --smtp-portが無視される問題を修正。

### 感謝

* Kenji Shionoさん
* akira yamadaさん

## 1.6.8: 2011-04-15 {#release-1-6-8}

1.6.7のバグフィックスリリースです。

### 全体

#### 改良

* インストール時に必要のないディレクトリを作成しないように    した。    [OBATA Akioさんが報告]

### ドキュメント

#### 改良

* CentOS 5.6向けの記述にした。

#### 修正

* 内部リンクを修正した。

### milter-manager

#### 改良

* manager.event_loop_created    設定項目を追加。

### Ruby milter

#### 改良

* milter.event_loop_created    設定項目を追加。
* Milter::ClientSession#worker_idを追加。
* Milter::ClientSession#[]を追加。

### milter-core

#### 改良

* ヘッダー追加時の挙動をPostfixではなくSendmailと同様の挙    動になるようにした。

### milter-server

#### 改良

* 必要になるまでRubyのヘッダーファイルを要求しないようにし    た。

#### 修正

* milter-test-serverの検出に失敗する問題を修正

### 感謝

* OBATA Akioさん

## 1.6.7: 2011-04-08 {#release-1-6-7}

1.6.6のバグフィックスリリースです。

### 全体

#### 改良

* インストール時に必要のないディレクトリを作成しないように    した。    [OBATA Akioさんが報告]

#### 修正

* システムにインストールされているRuby/GLib2を検出できない    問題を修正。    [OBATA Akioさんが報告]

### パッケージ

#### 修正

* [RPM] 依存関係を修正。
* [Debian] 依存関係を修正。
* [Debian] 起動スクリプト内での非推奨のオプションの使用を    やめた。
* [RPM] 起動スクリプト内での非推奨のオプションの使用を    やめた。

### milter-manager

#### 修正

* [S25R] 常にmilterを実行してしまう問題を修正。

### milter-core

#### 改良

* ログレベルを追加する"+LEVEL1|LEVEL2|..."構文を追加。
* ログレベルを削除する"-LEVEL1|LEVEL2|..."構文を追加。

### milter-client

#### 改良

* --log-levelオプションの追加。
* --quietオプションの追加。

### 感謝

* OBATA Akioさん

## 1.6.6: 2011-04-07 {#release-1-6-6}

RubyサポートとSolarisサポートを強化したリリースです。

### 全体

#### 改良

* 必ずバンドルしているRuby/GLib2を使う    --with-bundled-ruby-glib2 configureオプションを追加。
* Solaris対応。

### ドキュメント

#### 修正

* [Debian] 設定からGROUP=postfixが抜けていたことを修正。    [Jordaoさんが報告]

### パッケージ

#### 改良

* Solaris対応。
* Fedoraのバージョンを13から14へアップ

### milter-core

#### 改良

* デフォルトでwarningレベルもログ出力するようにした。
* デフォルトでstatisticsレベルもログ出力するようにした。
* デフォルトでmessageレベルもログ出力するようにした。
* 統計ログをsyslogに出力するときはLOG_INFOレベルではなく、    LOG_NOTICEレベルを使うようにした。

#### 修正

* 読み込みエラー時のメモリリークを修正。

### milter-manager

#### 改良

* データベース接続対応。
* 接続元がIPv6を利用している場合はデフォルトではS25Rを無効    にするようにした。s25r.check_only_ipv4=でカスタマイズ可    能。
* --n-workersオプションの追加。
* --event-loop-backendオプションの追加。
* 設定ファイル内でのログ関連の設定に対応。

#### 修正

* 設定ファイルを再読みするとクラッシュする問題を修正。    [Kenji Shionoさんが報告]

### libmilter-compatible

#### 改良

* 環境変数でのイベントループバックエンドのカスタマイズに対    応。
  * MILTER_EVENT_LOOP_BACKEND=libev -&gt; libevを使用
  * MILTER_EVENT_LOOP_BACKEND=glib -&gt; GLibを使用（既定値）

### milter-test-client

#### 改良

* --pid-fileオプションの追加。
* SIGTERMによる終了に対応。

### milter-test-server

#### 改良

* --envelope-fromオプションの追加。
* --fromオプションを非推奨にした。
* --envelope-recipientオプションの追加。
* --recipientオプションを非推奨にした。
* --connect-macroオプションの追加。
* --helo-macroオプションの追加。
* --envelope-from-macroオプションの追加。
* --envelope-recipient-macroオプションの追加。
* --data-macroオプションの追加。
* --end-of-header-macroオプションの追加。
* --end-of-message-macroオプションの追加。
* 日本語の結果本文出力に対応。

### milter-report-statistics

#### 改良

* Solaris対応。
* --pidオプションの追加。
* --pid-directoryオプションの追加。

### Ruby milter

#### 改良

* --maintenance-intervalオプションの追加。
* --run-gc-on-maintainオプションの追加。
* --environmentオプションの追加。
* --max-file-descriptorsオプションの追加。
* --pid-fileオプションの追加。
* Milter::ClientSession#delete_headerの追加。
* Milter::ClientSession#insert_headerの追加。
* Milter::ClientSession#replace_bodyの追加。
* Milter::ClientSession#change_fromの追加。
* Milter::ClientSession#add_recipientの追加。
* Milter::ClientSession#delete_recipientの追加。
* Milter::ClientSession#delay_responseの追加。
* Milter::ClientSession#progressの追加。
* Milter::ClientSession#discardの追加。
* Milter::EventLoopの追加。
* 設定ファイル対応。
* Milter::SocketAddress#ipv4?の追加。
* Milter::SocketAddress#ipv6?の追加。
* Milter::SocketAddress#unix?の追加。

#### 修正

* 終了時にクラッシュする問題を修正。

### 感謝

* Jordaoさん
* Kenji Shionoさん

## 1.6.5: 2011-01-26 {#release-1-6-5}

1.6.4のバグフィックスリリースです。

### milter manager

#### 修正

* 「Sendmail Compatible」適用条件でif_addrとid_nameに    Sendmailの場合と同じ値を設定していなかった問題を修正。    [Kenji Shionoさんがパッチ作成]
* SMTPクライアントの切断を検出した時にクラッシュする問題を    修正。 [Kenji Shionoさんが報告]

### milter-manager-log-analyzer

#### 改良

* ENMAの追加するAuthentication-Resultsの解析に対応。

### Ruby milter

#### 改良

* 実行ユーザー・グループの変更に対応。

### 感謝

* Kenji Shionoさん

## 1.6.4: 2011-01-21 {#release-1-6-4}

1.6.3のバグフィックスリリースです。

### milter-client

#### 修正

* イベントループバックエンドとしてGLibを利用する場合のイベ    ントループの利用方法を従来のものに変更。

## 1.6.3: 2011-01-20 {#release-1-6-3}

パフォーマンス改善を目指したリリースです。パフォーマンス改善のための実験的な機能が入っています。これらの機能は1.8.0で正式な機能となる予定です。

### milter manager

#### 改良

* バンドルしているRuby/GLib2を0.19.4から0.90.5へアップグレード。
* Ruby 1.9.2対応。
* milter manager内部で問題があったときにSMTPサーバへ返す    ステータスを指定する設定    manager.fallback_status    を追加。
* 切断検出時にSMTPサーバへ返すステータスを指定する設定    manager.fallback_status_at_disconnect    を追加。 [Kenji Shionoさんが提案]
* SMTPサーバの利用するmilterプロトコルバージョンが4より小    さいときはDATAイベントをエミュレーションするようにした。
* イベントループバックエンドを指定する設定    manager.event_loop_backend    を追加。（実験的）
* ワーカープロセス数を指定する設定    manager.n_workers    を追加。（実験的）
* 送信パケットをバッファリングする量を指定する設定    manager.packet_buffer_size    を追加。（実験的）

#### 修正

* Postfix 2.3で    manager.use_netstat_connection_checker    が誤動作する問題を修正。 [Kenji Shionoさんが報告]
* 複数の子milterがいるときにDATAイベントを送信するタイミン    グが遅かった問題を修正。 [Kenji Shionoさんが報告]

### ドキュメント

#### 改良

* Postfixの{client_addr}について追記。 [Kenji Shionoさんが報告]

### milter-client

#### 改良

* マルチプロセス対応。（実験的）
* イベントループバックエンドのlibev対応。（実験的）
  * libev 4.03を同梱。
* writeの非同期化。
* 送信パケットのバッファリング対応。（実験的）

### milter-server

#### 改良

* イベント発生時の状態チェックを強化。

#### 修正

* タイムアウト検出が誤動作する問題を修正。 [Kenji Shionoさんが報告]

### Ruby milter

#### 改良

* マルチプロセス対応。（実験的）
* ruby-milter.pcの導入。
* 送信パケットをバッファリングする量を指定す    る--packet-buffer-sizeオプションを追加。（実験的）
* ワーカープロセス数を指定する--n-workersオプションを追加。    （実験的）
* イベントループバックエンドを指定する--event-loop-backend    オプションを追加。（実験的）

### milter-test-client

#### 改良

* ワーカープロセス数を指定する    --n-workersオプショ    ンを追加。（実験的）
* イベントループバックエンドを指定する    --event-loop-backend    オプションを追加。（実験的）
* 送信パケットをバッファリングする量を指定する    --packet-buffer-size    オプションを追加。（実験的）

### milter-performance-check

#### 改良

* 本文サイズを大きくする    --n-additional-lines    オプションの追加。
* 失敗したSMTPセッションの結果を報告する    --report-failure-responses    オプションの追加。
* 定期的に統計情報を報告する    --report-periodically    オプションの追加。
* 指定した期間メールを送信し続ける    --flood    オプションの追加。

### milter-report-statistics

#### 改良

* 追加: milter-report-statistics.rd.ja

### パッケージ

* CentOS用パッケージリポジトリRPMを更新: 1.0.0-0 -&gt; 1.0.0-1.

### 感謝

* Kenji Shionoさん

## 1.6.2: 2010-11-23 {#release-1-6-2}

1.6.1のバグフィックスリリースです。

### milter manager

#### 改良

* Debianの起動スクリプトでのPIDファイル保存用ディレクトリ    の準備処理を堅牢化。    [Kenji Shionoさんが報告]
* time_tが必要なところではgint64を使用。    [OBATA Akioさんが提案]

#### 修正

* 一時ファイルをclose忘れを修正。    [Kenji Shionoさんが報告]

### milter manager admin

#### 修正

* CentOSで使用するsqlite3-rubyのバージョンを指定。（ドキュメント）    [Kenji Shionoさんが報告]

### Ruby milter

#### 改良

* milter-tarpit.rb（サンプルmilter）を非同期化。    [Kenji Shionoさんが報告]
* milter作成APIをすべて提供。

#### 修正

* コマンドラインオプションのtypoを修正。    [Kenji Shionoさんが報告]

### 感謝

* Kenji Shionoさん
* OBATA Akioさん

## 1.6.1: 2010-08-21 {#release-1-6-1}

1.6.0のバグフィックスリリースです。

### milter manager

#### 修正

* syslogに統計情報用のログが出力されない問題の修正。    [やまだあきらさんが報告]

### 感謝

* やまだあきらさん

## 1.6.0: 2010-08-11 {#release-1-6-0}

安定版1.6.x系最初のリリースです。

### milter manager

#### 改善

* Postfixのcidr_table(5)とregexp_table(5)のパーサを追加:    PostfixCIDRTable, PostfixRegexpTable

## 1.5.3: 2010-08-03 {#release-1-5-3}

1.5.x最後のリリースです。（予定）

### ドキュメント

#### 改善

* Rubyでmilterを開発するためのチュートリアル    を追加。
* SocketAddress#to_ip_address    の説明を追加。

### milter manager

#### 改善

* ネゴシエーションに失敗した場合にも結果を返すようにした。
* デフォルトのタイムアウト時間を短くした。これまではMTAと    同じ時間になっていたが、それではタイムアウト時にMTAに結    果を返せないため。
* コマンドランチャーをsyslogに対応させた。
* 適用条件追加
  * Trust
* Solaris対応。[さとうふみやすさんがパッチ提供]

### milter manager admin

#### 改善

* Rails 2.3.8対応

### milter-test-server

#### 改善

* --colorオプションの追加。
* --threadsオプションの追加。

### milter-core

#### 改善

* デフォルトでエラーと致命的なログを出力するように変更。

### Ruby milter

#### 改善

* --user, --gorup, --unix-socket-group,    --unix-socket-mode, --syslog, --library-version オプショ    ンを追加。
* サンプルとしてmilter-test-clientのRuby実装を追加。
* サンプルとしてmilter-regexp.rbを追加。

### 感謝

* さとうふみやすさん

## 1.5.2: 2010-05-29 {#release-1-5-2}

1.5.1のバグフィックスリリースです。

NO_REPLY_*を利用するmilterやmilter-greylist 4.3.xと一緒に使っている開発版ユーザはアップデートすることをおすすめします。

### ドキュメント

#### 改善

* 利用可能なmilterの一覧を作成。
* milter-greylistのおすすめ設定を更新

### milter manager

#### 改善

* S25Rのホワイトリストのカスタマイズ    ・ブラッ    クリストのカスタマイズ    をサポート。

### milter-manager-log-analyzer

#### 改善

* milter-greylist 4.3.xに対応

### milter-toolkit

#### 改善

* inet_aton()/inet_ntoa()の代わりにinet_pton()/inet_pton()    を使用。[さとうふみやすさんが提案]
* NO_REPLY_*のサポート。 [ROSSOさんが報告]

### 感謝

* さとうふみやすさん
* ROSSOさん

## 1.5.1: 2010-04-20 {#release-1-5-1}

1.5.0のバグフィックスリリースです。

同梱しているRuby/GLib2を更新したので、Ruby/GLib2内で起こっていたメモリリークが修正されています。同梱しているRuby/GLib2を使っている場合はアップデートを推奨します。

### ドキュメント

#### 改善

* Ubuntu Karmic Koara用の開発版インストールドキュメントを    追加
* 明示的にRackをインストールする記述を追加 [土谷さんが報告]

#### 修正

* FreeBSD: パッケージ名の修正 [土谷さんが報告]

### libmilter-core

#### 改善

* MILTER_LOG_SYSLOG_LEVEL環境変数でsyslogに出力するログの    種類を変更可能にした
* メモリプロファイラを追加

### milter manager

#### 改善

* Solaris対応 [さとうふみやすさんが報告・パッチ提供]
* Ruby/GLib2 0.19.4を同梱

### milter-test-client

#### 改善

* --report-memory-profile    オプションの追加。

### 感謝

* 土谷さん
* さとうふみやすさん

## 1.5.0: 2010-03-29 {#release-1-5-0}

開発版リリースです。

### ドキュメント

#### 改善

* Debian GNU/Linux・Ubuntu用ドキュメント
  * 不必要なグループ変更の記述を削除 [西山さんが提案]
* CentOS用ドキュメント
  * よりインストールの簡単なYumを利用した記述へ変更
* FreeBSD用ドキュメント
  * CFLAGSではなくCPPFLAGSを使うように変更
  * の対象バージョンを7.2-RELEASEから8.0-RELEASEに変更

#### 修正

* FreeBSD用ドキュメント
  * pwコマンドのオプションを修正

### milter manager

#### 改善

* Debian GNU/Linux用のinitスクリプト
  * statusをサポート [西山さんが提案]
  * 必要になるまでパラメータチェックを遅延 [西山さんが提案]
  * 不必要な依存関係を削除 [西山さんが提案]
* [#2921072] 冗長ログモード時に読み込んだ設定ファイルのパ    スを表示 [Antuan Avdioukhineさんが提案]
* [#2921072] 設定を変更したファイルと行を表示    [Antuan Avdioukhineさんが提案]
* [#2921078] 子milterなしの動作をサポート    [Antuan Avdioukhineさんが提案]
* 設定項目追加
  * remove_milter
  * manager.connection_check_interval
  * manager.define_connection_checker
  * manager.use_netstat_connection_checker
  * manager.report_memory_statistics
  * manager.maintained
  * stress.threshold_n_connections
  * stress.threshold_n_connections=
  * remote_network.add_local_address
* 適用条件追加
  * No Stress
  * Stress Notify
* Ruby/GLib 0.19.3を同梱（FreeBSD用）
* /usr/sbin/serviceまたは/sbin/serviceがある場合はそれを利    用するように変更
* CentOSでのOpenDKIM検出に対応
* Syslogのfacility変更に対応: MILTER_LOG_SYSLOG_FACILITY環境変数を指定
* manager.max_file_descriptors:    ソフトリミットだけではなく、ソフトリミットとハードリミットの両方を変更
* [Munin](http://munin-monitoring.org/)対応
* 高速化・メモリ使用法の改善

#### バグ修正

* FreeBSD: /etc/rc.confでプロファイルを指定していなかった    場合にOpenDKIMの検出に失敗する問題の修正 [土谷さんが報告]
* RubyのGCにより適用条件が実行されないことがある問題の修正

#### 実験的

* 条件とmilterを一度に指定できるポリシーフレームワークを追加

### milter-toolkit

* Rubyバインディングによるmilter作成をサポート: Ruby連携
  * configureで--enable-ruby-milterオプションを指定。

### milter-manager-log-analyzer

* 高速化（約2倍）
* SMTPクライアントの途中切断数のグラフ化をサポート

### milter-performance-check

* オプション追加
  * --n-concurrent-connections:      最大同時接続数を指定

### milter-test-client

* オプション追加
  * --no-report-request:      MTAからのリクエストをダンプしない
  * --user:      実効ユーザを指定
  * --group:      実効グループを指定
  * --unix-socket-group:      ソケットの所有グループを指定

### パッケージ

#### CentOS

* パッケージを分割

### テスト

* [Cutter](http://cutter.sourceforge.net/index.html.ja) 1.1.0対応

### 感謝

* 西山さん
* 土谷さん
* Antuan Avdioukhineさん

## 1.4.2: 2010-03-29 {#release-1-4-2}

1.4.1のバグフィックスリリースです。

### ドキュメント

* FreeBSDのビルド時にCFLAGSではなくCPPFLAGSを使うように変更
* FreeBSDの対象バージョンを7.2-RELEASEから8.0-RELEASEに変更
* FreeBSDのpwコマンドのオプションを修正

### milter manager

#### バグ修正

* 実効ユーザとソケットのグループを指定したときにソケットの    グループが反映されない問題の修正
* FreeBSD: OpenDKIMがインストールされていないときにmilter    自動検出が失敗する問題の修正

## 1.4.1: 2009-10-29 {#release-1-4-1}

1.4.0のバグフィックスリリースです。

### ドキュメント

* CentOSの対象バージョンを5.3から5.4に変更
* typoを修正 [はやみずさん]
* typoを修正 [西山さん]

### milter manager

#### 改善

* システムにRuby/GLib2がインストールされていない環境のため    に、Ruby/GLib2をバンドル。CentOSでは別途Ruby/GLib2のRPM    をインストールする必要がなくなった。
* configure時にデフォルトの設定値を指定できるようにした。
  * --with-default-effective-user: 実効ユーザ
  * --with-default-effective-group: 実効グループ
  * --with-default-socket-group: UNIXドメインソケットのグループ
  * --with-default-pid-file: PIDを保存するファイル
  * --with-default-connection-spec: 接続待ち受けアドレス

#### バグ修正

* CentOS用initスクリプトのデフォルト値が設定ファイルの設定    を上書きしてしまう問題を修正 [ゴリ丸さんによる報告]
* 評価モード時に、処理が終了した子milterに余計なコマンドを    送ってしまう問題を修正

### 感謝

* はやみずさん
* ゴリ丸さん
* 西山さん

## 1.4.0: 2009-10-13 {#release-1-4-0}

安定版リリースです。

### ドキュメント

* Debian用インストールドキュメントを追加

### milter-manager

#### 改善

* Debian/Ubuntu/FreeBSD環境でのOpenDKIM検出に対応

#### バグ修正

* 評価モード時にヘッダ追加の統計ログが出力されない問題を修    正

## 1.3.1: 2009-09-16 {#release-1-3-1}

開発版リリースです。評価モードが追加されました。

### milter-manager

#### 改善

* 子milterの結果を利用しない評価モード    の追加
* 設定項目追加:
  * 最大同時接続数:      manager.max_connections
  * 最大ファイルディスクリプタ数:      manager.max_file_descriptors
* EPELに対応 [今間さんによる報告]
* milter-greylistのtarpit設定に応じたタイムアウトの設定に対応

### milter-toolkit

* Rubyバインディングの追加    [はやみずさん]

### milter manager admin

* Rails 2.3.4対応

### milter-test-client

* syslogにログを出力する--syslogオプションの追加

### milter-manager-log-analyzer

* milter-greylistのSPF結果に対応

### 感謝

* はやみずさん
* 今間さん

## 1.3.0: 2009-08-12 {#release-1-3-0}

開発版リリースです。

### milter-manager

#### 改善

* 1セッションで複数のメールを送信する場合の処理を改善

#### バグ修正

* quarantineが無視される問題を修正    [土谷さんによる報告]
* discardが無視される問題の修正    [土谷さんによる報告]
* ヘッダがないメールで落ちる問題の修正    [Павел Гришинさんによる報告]

### milter-test-server

* 不必要なabortを削除
* quarantine時にはcontinueを送るように変更

### milter-manager-log-analyzer

* clamav-milterのウィルス検出結果に対応

### 感謝

* 土谷さん
* Павел Гришинさん

## 1.2.0: 2009-07-17 {#release-1-2-0}

安定版リリースです。

### milter-manager

#### 改善

* MTAのmilterプロトコルのバージョンに関係なくDATA時の停止    判定処理をサポート

#### バグ修正

* メッセージ処理時にすべてのmilterを停止すると処理がタイム    アウト待ちになってしまう問題の修正 [sgykさんによる報告]
* Postfix 2.3.3で動作しない問題の修正 [となかさんによる報告]

### 感謝

* sgykさん
* となかさん

## 1.1.1: 2009-07-03 {#release-1-1-1}

次期安定版1.2.0になる予定のリリースです。

### milter-manager

#### 改善

* 不必要なabortコールバック呼び出しを削減
* 統計ログの削減
* 複数インスタンスのサポート
  * manager.custom_configuration_directory
* MTAからの接続を受け付けられない状態のときに接続受付を何    秒待つかの設定項目を追加
  * manager.suspend_time_on_unacceptable
* Momonga Linuxのサポート [となかさんによる提案]
* 絶対パス指定による設定ファイル読み込みのサポート
* RCPT TOのときにmilter適用を中止した場合、メッセージ全体    の処理を中止するのではなく、その宛先の処理だけ中止するよ    うに変更
* milterがイベントを処理しない場合（SMFIP_NO*を指定してい    るイベント）でも、すべてのイベントで中止判断処理を実行す    るように変更
* 複数のメールトランザクションに対応 [sgykさんによる報告]
* 設定ファイルの読込パスの中にmilter-manager.local.confが    あれば読み込むように変更
* [実験的] 特定のユーザだけmilterを適用するサンプルを追加

#### バグ修正

* 複数milter実行時の競合条件を修正
* milterがメッセージ本文処理中にエラーステータスを返したと    き、MTAにレスポンスを返さない問題の修正 [となかさんによる報告]
* メッセージ本文処理中にmilter適用を中止した場合に他の    milterも中止されてしまう問題を修正 [sgykさんによる報告]

### milter-test-server

* すべての宛先が拒否または一時障害ステータスを返されたと    きは、セッション全体のステータスとして拒否または一時障害    と報告するように変更

### milter-manager-log-analyzer

* milter毎の適用結果グラフの生成
* 迷惑メール対策手法の統計グラフの生成

### 感謝

* となかさん
* sgykさん

## 1.1.0: 2009-06-02

次期安定版1.2.0に向けた開発版です。

### milter-manager

* 不要なログの削減
* FreeBSD上でのENMAの自動検出をサポート
* ClamAV 0.95の自動検出をサポート
* メールのサイズが65535バイトより大きいとき、dkim-filterの    skipが無視される問題の修正
* connect時の未知のアドレスファミリーのサポート
* 子milter毎のエラー時ステータス設定をサポート    （milter.fallback_status）
* デバッグログにmilterのIDを追加
* メモリリークの修正
* 定期的なメンテナンス処理の実行    （manager.maintenance_interval）
* Ruby/GLib 0.17.0での問題回避処理の追加
* クラッシュ時にバックトレースログを出力する機能の追加
* milter適用を中止するコールバックが呼び出されるイベントの    追加
  * condition.define_helo_stopper
  * condition.define_data_stopper
  * condition.define_end_of_header_stopper
  * condition.define_body_stopper
  * condition.define_end_of_message_stopper
* killで関連プロセスが終了しない問題の修正
* ファイルディスクリプタを開きすぎている場合に接続受付を一    時中止する機能を追加

### milter manager admin

* Ruby on Rails 2.3.2対応

### milter-test-server

* reply-codeのサポート
* 認証関連マクロを指定するオプションを追加
  * --authenticated-name=NAME
  * --authenticated-type=TYPE
  * --authenticated-author=AUTHOR

### milter-manager-log-analyzer

* メモリ使用量の削減

### ドキュメント

* リンク先修正: [Павел Гришинさん]

## 1.0.1: 2009-05-14

1.0.0のバグフィックス版です。

### milter-manager

* RPMパッケージアップデート時にmilter-managerが再起動され    ない問題を修正

### milter manager admin

* gemの使用バージョンを明示    [nhisaさんによる報告]

## 1.0.0: 2009-04-16

最初の安定版リリースです。

### ドキュメント

* コマンドのmanページを追加
* clamav-milterの設定に--externalオプションの追加
* UbuntuとCentOSのインストールドキュメントをパッケージを使っ    たものに変更

### milter-manager

* CentOS環境でのENMA検出機能の追加

### milter-performance-check

* --n-mailsオプションと、--period/--intervalオプションを使    えるように改良

## 0.9.0: 2009-03-10

速度と安定性が向上しました。

### milter-manager

* UNIXドメインソケットのグループを指定する機能の追加
* 高速化:
  * 1つのパケットで多くのmilterコマンドを送信するように変更
  * メール本文をできるだけオンメモリで処理するように変更
* configure:
  * --with-rcddir: pkgsrcのrc.dディレクトリを指定するオプ      ションの追加
* バグ修正:
  * ファイルディスクリプタをcloseしすぎていた問題の修正
  * temporary failureをrejectとログに出力していた問題の修      正

### 新適用規則

* sendmail-compatible:    Sendmailのmilter実装とPostfixのmilter実装間にある、マク    ロに関する非互換を回避する機能    （参考: [Postfix before-queue Milterサポート - 回避方法](http://www.postfix-jp.info/trans-2.3/jhtml/MILTER_README.html#workarounds)）
  適用規則ではないが、適用規則の枠組みを使ってMTAからmilterに渡されるマクロを変換している。この機能により、dnsbl-milterがパッチ(*)なしでPostfixでも動くようになる。
  (*) [[2594714] Postfix support](http://sourceforge.net/tracker/?func=detail&atid=1015126&aid=2594714&group_id=210782)
* authentication: 認証時あるいは非認証時のみmilterを適用す    る規則

### milter-performance-check

* ファイルを1通のメールとして送信する機能の追加
* 指定したディレクトリ以下にあるファイルをそれぞれ1通のメー    ルとして送信する機能の追加
* --from, --recipient, --force-from, --force-recipient:    差出アドレス・宛先アドレスの上書き機能の追加
* --interval: 一定間隔でメールを送信する機能の追加
* --period: 指定した期間内に一定の間隔でメールを送信する機    能の追加
* --shuffle: 送信順序をランダムに並び替えてメールを送信す    る機能の追加

### milter-manager-log-analyzer

* [非互換]: 処理メールグラフに「abort」時の項目を追加

## 0.8.0: 2009-02-06

* 新機能
  * 追加ツール
    * milter-manager-log-analyzer:        milter-managerのログをグラフ化
    * milter manager admin:        milter-managerの管理用Webインターフェイス
    * ↑のスクリーンショット:        インストールページの下部
  * pkgsrc用milter検出機能の追加
  * CentOS対応
  * 適用条件
    * 他のmilterのステータス取得対応
    * milterのマクロの取得・書き換え対応
* S25R更新（2009/02/01版）
* バグ修正
  * [#2518782] typo in configure: [OBATA Akio]

## 0.7.0: 2009-01-16

* SF.netでの最初のリリース。


