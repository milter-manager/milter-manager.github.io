---
title: NEWS
description: The history of milter manager
---

# NEWS --- The history of milter manager

## 2.2.5: 2022-12-12 {#release-2-2-5}

### milter manager

#### Fixes

  * Fixed a bug that `netstat` related error is happen.
    [GH-176] [Reported by Christian]

### milter client

#### Improvements

  * Added `milter.run_gc_on_maintain=` configuration.

#### Fixes

  * Fixed a GC related bug that running `Milter::ClientSession` may be
    GC-ed.

### Thanks

  * Christian

## 2.2.4: 2022-12-10 {#release-2-2-4}

### Packages

#### Fixes

  * deb: Fixed wrong man locations.

  * deb: Fixed `Conflicts` configuration

### Document

#### Improvements

  * AlmaLinux 8: Added missing `dnf module -y enable ruby:3.0`.
    [milter-manager-users-ja]
    [Reported by ymatsuki]

  * AlmaLinux 8: Removed needless custom `milter_mail_macros`.
    [milter-manager-users-ja 61]
    [Reported by ymatsuki]

### milter manager

#### Improvements

  * Improved libev integration.

### Thanks

  * ymatsuki

## 2.2.3: 2022-10-04 {#release-2-2-3}

### Python

#### Improvements

* Set <code>fallback_status</code> to <code>milter.client.SessionContext</code>.

#### Fixes

* Fixed a bug that <code>fallback_status</code> may not be used on error.

## 2.2.2: 2022-10-04 {#release-2-2-2}

### Package

#### Fixes

* deb: Fixed an upgrade failure.

### milter server

#### Improvements

* Added a missing <code>NULL</code> check to suppress a warning.

### Python

#### Fixes

* Fixed a bug that logger's exception writer doesn't work with    Python 3.8.

## 2.2.1: 2022-09-29 {#release-2-2-1}

### Package

#### Fixes

* deb: Fixed an upgrade failure.    [GitHub#176][Reported by Kazuhiro NISHIYAMA]

### Python

#### Fixes

* Fixed a bug that milter client doesn't work with Python 3.8.

### Thanks

* Kazuhiro NISHIYAMA

## 2.2.0: 2022-09-29 {#release-2-2-0}

### Package

#### Fixes

* ubuntu: Fixed a bug that wrong source archive is used.

## 2.1.9: 2022-09-29 {#release-2-1-9}

### Python

#### Improvements

* Added support for Python 3.8.
* client: Added support for <code>--version</code> option.

## 2.1.8: 2022-09-28 {#release-2-1-8}

### Package

#### Fixes

* deb: Fixed bugs that Python and GObject Introspection related    packages can't be used.

## 2.1.7: 2022-09-28 {#release-2-1-7}

### Package

#### Improvements

* Added support for AlmaLinux 8.
* Added support for AlmaLinux 9.
* Dropped support for Ubuntu 18.04.
* Added support for Meson partially.
* deb: Added support for GObject Intospection.

### All

#### Improvements

* Removed memory profile feature because <code>g_mem_set_vtable()</code> is    deprecated since GLib 2.46.
* Required GLib 2.50 or later.
* Added support for GObject Introspection.
* Introduced some API/ABI incompatible changes. So shared object    version was increased to <code>2</code> from <code>0</code>.
  * <code>milter_macros_requests_foreach()</code>: Use <code>MilterMacrosRequestFunc</code>      instead of <code>GHFunc</code>.
  * <code>milter_client_processing_context_foreach()</code>:      Use <code>MilterClientContextFunc</code> instead of <code>GFunc</code>. (This      is only API incompatible.)
* Stopped bundling libev.
* Stopped bundling Ruby/GLib2, Ruby/GIO2 and Ruby/GObojectIntrospection.

### milter core

#### Improvements

* Added <code>milter_logger_get_default()</code>.
* Added <code>milter_logger_log_literal()</code>.

### milter client

#### Improvements

* <code>MilterClientContext</code>:
  * Added <code>body-bytes</code> and <code>end-of-message-bytes</code> signals to      receive chunk as a <code>GBytes</code>.
  * Added <code>use-bytes</code> property to use the above <code>GBytes</code> signals.
  * Added <code>milter_client_context_get_use_bytes()</code>.
  * Added <code>milter_client_context_set_use_bytes()</code>.
  * Added <code>milter_client_context_replace_body_bytes()</code>.

### milter server

#### Improvements

* Added <code>milter_test_server</code> variable to <code>milter-server.pc</code>.
* <code>milter-test-server</code>:
  * Changed to return non-zero exit code when      it failed to connect to a milter.
  * Changed to use Postfix compatible <code>i</code> macro behavior by default.
    * Before: <code>i</code> is sent on "MAIL" and "end-of-message".
    * After: <code>i</code> is sent on "DATA", "end-of-header" and "end-of-message".

### milter-manager-log-analyzer

#### Improvements

* Added support for Ruby 3.2.

### Python

#### Improvements

* Added GObject Introspection based bindings. You can use Python to    implement your milter.

## 2.1.6: 2022-01-13 {#release-2-1-6}

### Document

#### Improvements

* Added blog entry about sponsorship from packageloud.io.

#### Fixes

* Fixed available milter-regex website URL. [Reported by OBATA Akio][GitHub #140]

### Package

#### Improvements

* Dropped CentOS 8 support.
* Dropped Debian stretch support.
* Dropped Ubuntu 16.04 support.
* Dropped Ubuntu 19.04 support.
* Bundled glib2 3.5.0 gem, gobject-introspection 3.5.0 gem, gio2    3.5.0 gem, pkg-config gem and native-package-installer gem.

#### Fixes

### milter manager

#### Improvements

* <code>--with-bundled-ruby-gio2</code>: Added support for using bundled    gio2 gem.
* <code>--with-bundled-ruby-gobject-introspection</code>: Added support for    using bundled gobject-introspection gem.
* <code>milter-performance-check</code>: Add support for multiple <code>--from</code>.

#### Fixes

* Fix a bug that milter-manager causes a SEGV. [Reported by BugbearR][GitHub #146]    This bug is caused by mismatched type definition unexpectedly.

### Thanks

* OBATA Akio
* BugbearR

## 2.1.5: 2019-09-10 {#release-2-1-5}

### Document

#### Improvements

* Updated installation manual for CentOS 7
* Removed obsolete AllowSupplementaryGroups option because    it was deprecated since ClamAV 0.100.0

#### Fixes

* Fixed to use [Reported by Kazuhiro NISHIYAMA][GitHub #137]
* Fixed "Authentication" typos in configuration document [Patch by SATOH Kiyoshi][GitHub #138]
* Fixed missing database.host in configuration document [Reported by SATOH Kiyoshi]

### Package

#### Improvements

* Dropped CentOS 6 support
* Added a sample Ruby milter script that replaces content

#### Fixes

* Fixed to use Ubuntu version instead of code name not to fail package upgrade.    [Reported by Kazuhiro NISHIYAMA][GitHub #137]

### Thanks

* Kazuhiro NISHIYAMA
* SATOH Kiyoshi

## 2.1.4: 2018-07-06 {#release-2-1-4}

### Document

#### Fixes

* Install Japanese documents properly [Reported by OBATA Akio][GitHub #136]

### Thanks

* OBATA Akio

## 2.1.3: 2018-07-05 {#release-2-1-3}

### Document

#### Fixes

* Revive missing Japanese documents [Reported by OBATA Akio][GitHub #136]

### Thanks

* OBATA Akio

## 2.1.2: 2018-07-03 {#release-2-1-2}

### Package

#### Improvements

* Drop Ubuntu Yakkety Yak (16.10) support
* Drop Ubuntu Zesty Zapus (17.04) support
* Add Ubuntu Artful Aardvark (17.10) support
* Add Ubuntu Bionic Beaver (18.04) support
* Drop Debian Jessie support
* Update Ruby version to 2.3.5 on CentOS6

### milter manager

#### Fixes

* Fix a bug that Rspamd auto detection failure [Reported by whyscream][GitHub #128]

### Known issues

* We cannot use rspamd_proxy as a child milter of milter-manager [GitHub #134]

### Thanks

* whyscream

## 2.1.1: 2017-06-27 {#release-2-1-1}

### Package

#### Improvements

* Drop Ubuntu Precise Pangolin (12.04) support
* Add Ubuntu Zesty Zapus (17.04) support
* Add Debian Buster support

### milter core

#### Improvements

* binding ruby: Update bundled ruby-gnome2 to 3.1.1

### milter manager

* Support auto detection for [Rmilter](https://rspamd.com/rmilter/) (experimental)
  * Rmilter has been obsolete since Rspamd 1.6, use [Rspamd proxy](https://rspamd.com/doc/workers/rspamd_proxy.html)
* Support auto detection for [Rspamd proxy](https://rspamd.com/doc/workers/rspamd_proxy.html) (experimental)

## 2.1.0: 2016-11-21 {#release-2-1-0}

A bug fix release of 2.0.9

Move to OSDN from sourceforge.net

See https://milter-manager.osdn.jp/

We are using following features on OSDN:

* Web site
  * Redirect to milter-manager.osdn.jp from milter-manager.sourceforge.net
* File release
  * We've already copied all released contents to OSDN
* Mailing list
  * We will transfer accounts automatically
  * We will not transfer mailing list archives
* News
  * sourceforge.net does not have this feature

Download packages:

* deb packages for Ubuntu: launchpad.net
  * https://launchpad.net/~milter-manager/+archive/ubuntu/ppa/+packages
* deb packages for Debian: packagecloud
  * https://packagecloud.io/milter-manager/repos/install
* RPM: packagecloud
  * https://packagecloud.io/milter-manager/repos/install
* tar ball: OSDN
  * https://osdn.net/projects/milter-manager/releases/

### Package

#### Improvements

* Add Ubuntu Yakkety (16.10) support

### milter manager

#### Fixes

* Boot automatically after reboot the CentOS7 host
* Fix milter-greylist default config file path for pkgsrc    [Pull request by OBATA Akio][GitHub #99]

#### Improvements

* Add DNSBL applicable condition    [Pull request by Yuto Hayamizu][GitHub #108]

### milter client

#### Fixes

* Fix the bug that milter cannot run with --n-workers=1 or more

### milter serever

#### Improvements

* Add --all-timeout option to milter-test-server command    [Pull request by HorimotoYasuhiro][GitHub #101]

### Thanks

* OBATA Akio
* Yuto Hayamizu
* Horimoto Yasuhiro

## 2.0.9: 2016-06-15 {#release-2-0-9}

A bug fix release of 2.0.8

### milter manager

#### Fixes

* Detect milters properly on CentOS6, CentOS7

## 2.0.8: 2016-06-15 {#release-2-0-8}

A bug fix release of 2.0.7

You need to update /etc/apt/sources.list.d/milter-manager.list beforeyou update packages if you have already installed milter-manager.

For example, on Debian (jessie) /etc/apt/sources.list.d/milter-manager.list:

<pre>deb http://downloads.sourceforge.net/project/milter-manager/debian/stable jessie main
deb-src http://downloads.sourceforge.net/project/milter-manager/debian/stable jessie main</pre>

Ubuntu: Add ppa:milter-manager/ppa

<pre>% sudo apt-get -y install software-properties-common
% sudo add-apt-repository -y ppa:milter-manager/ppa
% sudo apt-get update</pre>

CentOS: Update milter-manager-release to 1.3.0

<pre>% sudo yum install -y \
http://sourceforge.net/projects/milter-manager/files/centos/milter-manager-release-1.3.0-1.noarch.rpm</pre>

### Package

#### Fixes

* Suppress warnings (false detection) by lintian    [Patched by Youhei SASAKI]
* Keep files that is needed when rebuild document under debian    directory while building deb package. We need this for clean    build. [Patched by Youhei SASAKI]
* Update apt-line for Debian to correspond specification change of    SourceForge.net
* Create APT repository for Debian stretch properly
* Update milter-manager-release for CentOS to correspond    specification change of SourceForge.net. You cannot update    milter-manager via yum command If you use milter-manager-release    before 1.3.0.

#### Improvements

* Drop Debian wheezy support
* Add Ubuntu Xenial (16.04 LTS) support
* Drop Ubuntu Wily (15.10) support
* Drop Ubuntu Vivid (15.04) support
* Add systemd support for deb packages (Except Ubuntu Precise(12.04))
* Update Ruby to 2.2.5 on CentOS6
* systemd support is stable on CentOS7
* Arrange build script for CentOS    [Patched by Hiroshi Ohkubo][GitHub #92]

### milter manager

#### Fixes

* Fix milter-manager-log-analyzer errors with RRDtool 1.5    [Reporde by Dave Dodd][milter-manager-users-en]
* Use "_" instead of "-" to avoid bug of RRDtool 1.5    [Reporde by Dave Dodd][milter-manager-users-en]
* Fix a bug that configure option --with-bundled-ruby-glib2 does not    work properly on BSD.

### libmilter-compatible

#### Fixes

* Set timeout properly using smfi_settimeout()

### Ruby milter

#### Fixes

* Fix error when --fallback-status=temporary-failure    [Patched by Nobuhiko MIYAHARA][GitHub #87]

### Document

#### Improvements

* Add link to Russian translation    [Translated by Alisa Bagrii]
* Update document for recent clamav-milter on Debian/Ubuntu    [Reported by Kazuhiro NISHIYAMA][GitHub #90]
* Create socket directory when install on Debian/Ubuntu    [Reported by Kazuhiro NISHIYAMA][GitHub #91]

### Thanks

* Youhei SASAKI
* Nobuhiko MIYAHARA
* Alisa Bagrii
* Kazuhiro NISHIYAMA
* Dave Dodd
* Hiroshi Ohkubo

## 2.0.7: 2015-11-30 {#release-2-0-7}

A bug fix release of 2.0.6

### Package

#### Fixes

* Fix milter-manager(1) and html documents

## 2.0.6: 2015-11-30 {#release-2-0-6}

A bug fix release of 2.0.5.

### Package

#### Fixes

* Add missing dependency for deb Package    [Reported by Christian Use][milter-manager-users-en]

#### Improvements

* Add Debian stretch support
* Add Ubuntu Vivid (15.04) support
* Add Ubuntu Wily (15.10) support
* Drop Ubuntu lucid (10.04) support
* Drop Ubuntu Saucy (13.10) support
* Drop Ubuntu Utopic (14.10) support
* Use Ruby 2.2.3 on CentOS6
* Add systemd support on CentOS7 (experimental)

### milter manager

#### Improvements

* Update bundled libev to 4.19
* Update bundled ruby-glib2 to 2.2.5

### milter core

#### Improvements

* --log-level and --log-item can accepts multiple values separated by pipe "|" such as "info|default"    [Reported by TOMITA Masahiro]
* Don't colorize log by default when output is file    [Reported by TOMITA Masahiro][GitHub #58]

### Ruby milter

#### Improvements

* Add Milter::ServerContext#negotiate
* Add Milter::ServerContext#data
* Add Milter::ServerContext#abort
* Add Milter::ServerContext#quit
* Add Milter::ServerContext#reset_message_related_data
* Add Milter::Headers and Milter::Header
* Add Milter::Status#pass?
* Add sample/milter-test-server.rb

### Document

#### Fixes

* Fix typos    [Patched by Youhei SASAKI][GitHub #82]

### Thanks

* TOMITA Masahiro
* Christian Use
* Hiroshi Hatake
* Toshio Maki
* Youhei SASAKI

## 2.0.5: 2014-12-09 {#release-2-0-5}

A bug fix release of 2.0.4.Add experimental APIs can hold data between the mail transaction.

### Package

#### Improvements

* Drop CentOS5 support
* Add CentOS7 support
* Drop Ubuntu Saucy (13.10) support
* Add Ubuntu Utopic (14.10) support
* Build deb packages in clean room    [Patched by Youhei SASAKI][milter-manager-users-ja:00224]
* Improve auto detection for ruby-glib2    [Suggested by Youhei SASAKI and Kazuhiro NISHIYAMA][milter-manager-users-ja:00243]
* Require libev    [Reported by OBATA Akio][GitHub #48][GitHub #49]

### milter manager

#### Fixes

* Ensure to set UTF-8 encoding to file content    [Reported by Panagiotis Skarvelis][SF.net #6]

### milter-client

#### Improvements

* Add APIs can hold data between the mail transaction. (experimental)

### Ruby milter

#### Improvements

* Drop Ruby1.8 support
* Add APIs can hold data between the mail transaction. (experimental)

#### Fixes

* Setup signal handler when invoke milter in single process mode    [GitHub #53]

### Document

#### Fixes

* Execute sa-update before invoke sa-spamd on FreeBSD    [Reported by moto kawasaki][milter-manager-users-ja:00250]

### Thanks

* Youhei SASAKI
* Kazuhiro NISHIYAMA
* OBATA Akio
* Panagiotis Skarvelis
* moto kawasaki

## 2.0.4: 2014-06-20 {#release-2-0-4}

A bug fix release of 2.0.3

### Ruby milter

#### Improvements

* Add Milter::Client::Test::MilterRunner
* Add Milter::Client::EnvelopeAddress

#### Fixes

* Fix the bug that milter written in Ruby cannot finish properly on multiple CPU environment

## 2.0.3: 2014-05-20 {#release-2-0-3}

A bug fix release of 2.0.2

### Package

#### Improvements

* Drop Ubuntu Quantal (12.10) support
* Drop Ubuntu Raring (13.04) support
* Add Ubuntu Trusty (14.04) support
* Drop Debian squeeze support
* rpm: Update Ruby1.9.3 package for CentOS6 to Ruby1.9.3-p545.

### milter manager

#### Improvements

* Update bundled libev to 4.15

#### Fixes

* Fix a bug that data_stopper cannot stop apply children    [GitHub #39]

### Ruby milter

#### Improvements

* Update bundled glib2 to 2.2.0
* Milter::Logger methods can accept a block

### Document

#### Fixes

* Fix typos in FreeBSD installation    [Patched by Dave Dodd]

### Thanks

* Dave Dodd

## 2.0.2: 2014-01-27 {#release-2-0-2}

A bug fix release of 2.0.1

### Package

#### Fixes

* Add Ubuntu Lucid (10.04) support again    [Reported by Mitsuru Ogino][milter-manager-users-ja:00229]

### Thanks

* Mitsuru Ogino

## 2.0.1: 2014-01-24 {#release-2-0-1}

A bug fix release of 2.0.0.

### milter manager

#### Improvements

* Support SIGUSR1 signal to reopen log file

#### Fixes

* Drop functionality to report stack trace on crash.    Because it is unsafe for all users. [GitHub #38]

### milter-core

#### Improvements

* Support log output by MILTER_LOG_PATH environment variable.

### milter-client

#### Improvements

* Support --log-path option.

### Ruby milter

#### Improvements

* Support --log-path option.
* Support SIGUSR1 signal to reopen log file.

### Package

#### Improvements

* Drop Ubuntu Lucid (10.04) support.
* Add Ubuntu Saucy (13.10) support.
* deb: Support Ruby 2.0.0 detection on Debian.
* rpm: Update Ruby1.9.3 package for CentOS6 to Ruby1.9.3-p484.
* Remove auto-generated files from distribution archive.    [Reported by Youhei SASAKI][milter-manager-users-ja:00225]

### Document

#### Improvements

* Update to the latest milter-greylist RPM.    [Reported by ishizaka tadanori][milter-manager-users-ja:00220]
* Improve English version reference manual.    [GitHub #17]

### Thanks

* Youhei SASAKI
* ishizaka tadanori

## 2.0.0: 2013-07-25 {#release-2-0-0}

The major version up about 2 years!

There are no incompatible changes between 1.8.9 and 2.0.0.  Thisversion is compatible to 1.8.x, so you can upgrade without editingconfig files.

The reasons:

* We are developing milter manager continuously.
* We think milter manager is stable enough.

We released milter manager 1.8.0 at 2011/06/10. There are 10 releasesbetween 1.8.0 and 2.0.0. We have developed milter manager continuously.

milter manager 2.0.0 is more stable than 1.8.0, because users havebeen increased and reported issues. We have been able to fix problems,because users have reported a lot of problems. Of course, miltermanager is very stable, and Ruby/milter (functionality which you canwrite milter in Ruby) is also stable enough. We have reflected ourknowledge that we have developed milter written in Ruby toRuby/milter.

We can say that milter manager 2.0.0 is better than 1.8.0 withconfidence. Let's try milter manager if you haven't used miltermanager yet.

### milter-test-server

#### Improvements

* Support multiline header. [GitHub #33]

### Ruby milter

#### Fixes

* Fix a bug that reject/temporary failure on envelope recipient    calls reset.

## 1.8.9: 2013-06-28 {#release-1-8-9}

A bug fix release of 1.8.8.

### Package

#### Improvements

* [rpm] Update Ruby1.9.3 package for CentOS6 to Ruby1.9.3-p448    released on 2013-06-27

### milter manager

#### Fixes

* [binding][ruby] Fixed a bug that milter-manager couldn't detect    socket path if greylist.conf includes socket path with    permission.

## 1.8.8: 2013-06-25 {#release-1-8-8}

A bug fix release of 1.8.7.

### Package

#### Fixes

* [rpm] milter-manager-log-analyzer should include cron configuration.    [Reported by Satoru Sakashita][milter-manager-users-ja:00200]
* [deb] Remove old configuration file installed by milter-manager.    [Reported by Youhei SASAKI][milter-manager-users-ja:00202]

### Known Issues

* [test] Failed some test cases using rrdtool on some environments.    [Reported by Hirohisa Yamaguchi][GitHub #29]

### Thanks

* Satoru Sakashita
* Youhei SASAKI
* Hirohisa Yamaguchi

## 1.8.7: 2013-06-14 {#release-1-8-7}

A bug fix release of 1.8.6.

### Package

* [rpm] Keep user configuration settings on upgrade.
* [deb][rpm] Separate milter-manager-log-analyzer from milter-manager.    [Reported by Kazuhiro NISHIYAMA][GitHub #21]
* Use Ruby1.9 on CentOS6 or later.
* Drop Ubuntu Oneiric Ocelot(11.10) support.
* Add Ubuntu Raring Ringtail(13.04) support.
* Add Debian jessie support.

### milter manager

#### Improvements

* Support Ruby2.0.0.

#### Fixes

* [debian] Support init file that contains non-ASCII characters.    [Reported by Kazuhiro NISHIYAMA][GitHub #23]

### milter-manager-log-analyzer

#### Fixes

* Process mail log even if it includes invalid byte sequence.    [Reported by Satoru Sakashita][GitHub #24]

### Admin

* Dropped.

### Thanks

* Kazuhiro NISHIYAMA
* Satoru Sakashita

## 1.8.6: 2013-03-07 {#release-1-8-6}

A bug fix release of 1.8.5.

### milter-core

#### Improvements

* [core][event-loop] Add an API to customize event loop on your own.

#### Fixes

* [core][event-loop] Fix to work broken libev backend with Ruby 1.9.

### milter manager

#### Improvements

* Add max-pending-finished-sessions as configuration option.    If the number of current pending finished sessions is larger than    'max-pending-finished-sessions', the current pending finished sessions are    freed immediately.

### milter-client

#### Improvements

* Add --max-pending-finished-sessions command line option.

### Ruby milter

#### Improvements

* Add an API to customize event loop on your own from Ruby.
* Support manager.max_pending_finished_sessions.
* Add API to reset when transaction is finished.    Use this API to avoid not to share instance information for each transaction unexpectedly.

### Document

#### Improvements

* Add documentation about manager.max_pending_finished_sessions
* Add API to reset transaction.

#### Fixes

* Fix the default value of manager.maitenance_interval which is not correct.

## 1.8.5: 2012-12-03 {#release-1-8-5}

A bug fix release of 1.8.4.

### Package

* Drop Ubuntu Natty Narwhal support.
* Fix broken documents.

### Ruby milter

* Fix a typo in test for Ruby1.8.    [Pull requested by umq]

### Thanks

* umq

## 1.8.4: 2012-11-21 {#release-1-8-4}

A bug fix release of 1.8.3.

### Package

* Added Ubuntu Quantal Quetzal support.
* Provided packages built by using Ruby1.9 on following distributions:    Debian wheezy, Debian sid, Ubuntu Precise Pangolin, Ubuntu Quantal Quetzal
* Added missing fixture files into tar.gz.    [Reported by Hirohisa Yamaguchi]
* Solaris: Added missing SMF method file into tar.gz.    [Reported by @ftnk]
* yum: Rename yum repository pacakge.    milter-manager-repository -&gt; milter-manager-release
* deb: Use Ruby1.9 by default.
* deb: Rename packages for Ruby binding.    libmilter-*-ruby1.8 -&gt; ruby-milter-*

### milter manager

#### Improvements

* configure: Specify Ruby/GLib2 version to --with-bundled-ruby-glib2 option

#### Fixes

* manager: Suppressed compiler type warnings.    [GitHub #12]    [Reported by Hirohisa Yamaguchi]
* debian cron: used mail.log instead of mail.info    [milter-manager-users-ja:00171]    [Reported by Kazuhiro NISHIYAMA]

### milter-core

#### Improvements

* Supported MILTER_DEBUG=fatal-criticals.
* binding ruby: milter callback arguments are ASCII_8BIT.    [GitHub #3]

#### Fixes

* Fixed an issue which a following warning is shown when running at high loads.    "g_io_channel_write_chars: assertion &#96;channel-&gt;is_writeable' failed"

### Admin

#### Improvements

* Upgraded to Rails2.3.14

### Document

#### Fixes

* Fixed about install sequence on CentOS.    [GitHub #13]    [Reported by Kunkichi]

### Thanks

* Hirohisa Yamaguchi
* Kazuhiro NISHIYAMA
* @ftnk
* Kunkichi

## 1.8.3: 2012-05-22 {#release-1-8-3}

A bug fix release of 1.8.2.

### Package

* [ubuntu] Added Ubuntu Precise Pangolin support.
* [solaris] Use pkgutil instead of pkg-get.    [GitHub #6]    [Reported by h0lzi]

### milter manager

#### Improvements

* binding ruby: update bundled ruby-glib2 to 1.1.3

#### Fixes

* [manager] support manager.event_loop_backend = "libev" on CentOS.    [Reported by SHIONO Kenji]
* [manager][children] use gulong instead of guint.    g_signal_connect() returns gulong.

### milter-core

#### Fixes

* [libev] check whether the next id is used or not.

### Document

#### Fixes

* doc install debian ubuntu: add missing postfix group related configuration    milter-manager user should belong to postfix group to access a socket    of other milter.    [milter-manager-users-ja:00163]    [Suggested by Satoru Sakashita]
* doc debian: adjust to the latest squeeze environment    [Suggested by Satoru Sakashita]

### Thanks

* Satoru Sakashita
* SHIONO Kenji
* h0lzi

## 1.8.2: 2011-11-29 {#release-1-8-2}

A bug fix release of 1.8.1.

### milter-core

#### Fixes

* [event-loop][glib] fix memory leaks since 1.6.6.
* [core] fix memory leak when delete header.

## 1.8.1: 2011-11-12 {#release-1-8-1}

A bug fix release of 1.8.0.

Now, manager.event_loop_backend and manager.n_workers aren'texperimental!

### Package

* [ubuntu] Added Ubuntu Oneiric Ocelot support.
* [centos] Added CentOS 6 support.
* Changed GPG key to sign packages.

### milter manager

#### Improvements

* [applicable-condition][sendmail] clear DNS cache for each 100 IP    addresses.

#### Fixes

* detach IO for launcher on daemon mode.    use milter_client_is_run_as_daemon() to get whether daemonize or    not. [Reported by OBATA Akio]
* add a workaround for Ruby cleanup.    If environment variable    MILTER_MANAGER_RUBY_STOP_TIMER_THREAD_BEFORE_CLEANUP=yes,    skip timer thread before cleanup.
* use rb_fork() as fork implementation.    This will fix --daemon doesn't work on *BSD.    [Reported by OBATA Akio]
* use INCLUDES to use configured libev include path rather than    CPPFLAGS. [Reported by moto kawasaki]

### milter-core

#### Fixes

* fix missing null FD close by inverted condition.    [Reported by OBATA Akio]

### milter-client

#### Improvements

* use higher priority for accepting connection.

#### Fixes

* fix a bug that workers don't shutdown on master shutdown. It's    GLib evnet loop backend specific problem.

### milter-server

#### Improvements

* add more information to error message.
* [server] unify unknown name logging.

#### Fixes

* fix a bug that all milters can't find on 2nd RCPT in the same    session.

### Ruby milter

#### Improvements

* add Milter::Client::Configuration::MilterConfiguration#name.

#### Fixes

* fix event_loop_created hook can't get event loop.
* do not raise error if process raw shift_jis mail file. Ruby 1.9.
* udpate bundled test-unit file list. [Reported by Hirohisa Yamaguchi]
* [ruby][glib2] fix a SEGV bug on Solaris10.

### milter-test-server

#### Fixes

* fix quoted charset detection. [Reported by nobu]
* fix multiline header parsing.
* --mail-file keeps new line type of the original mail.

### Document

#### Improvements

* add log list to HTML.
* fix typos. [Pull requested by Norio Suzuki]

### Admin

#### Improvements

* use locale "en" if Accept-Language is not "ja".    [Reported by Larry G. Wapnitsky]

### Thanks

* Mitsuru Ogino
* OBATA Akio
* moto kawasaki
* nobu
* Hirohisa Yamaguchi
* Norio Suzuki
* Larry G. Wapnitsky

## 1.8.0: 2011-06-10 {#release-1-8-0}

The first release of stable 1.8.x series.

### All

#### Improvements

* Removed unused variables.

### Package

#### Improvements

* [debian] Removed Debian GNU/Linux lenny support.
* [debian] Added Debian GNU/Linux wheezy support.
* [ubuntu] Removed Ubuntu Hardy Heron support.
* [ubuntu] Removed Ubuntu Maverick Meerkat support.
* [ubuntu] Added Ubuntu Natty Narwhal support.
* [redhat] Specified PID file in init file explicitly.
* [freebsd] Supported /etc/rc.conf.local.    [Patch by moto kawasaki]

#### Fixes

* [debian] Added missing milter.rb.    [Reported by Mitsuru Ogino]

### milter manager

#### Improvements

* [trust applicable condition] Normalized domain name.
* Added trust.clear    configuration item.
* Added    trust.load_envelope_from_domains    configuration item.
* [trust applicable condition] Added ezweb.ne.jp and    docomo.ne.jp to built-in trusted domain list.
* Used fallback status on negotiate.
* Added    manager.chunk_size    configuration item.

#### Fixes

* Fixed a bug that child milter process launcher isn't    exited.    [Reported by OBATA Akio]
* Fixed a bug that child milters that return reject,    temporary failure or discard aren't used in the same    session.

### milter-core

#### Improvements

* Added trace log level that is more verbose than debug    log level.
* Supported +/- log level prefix to add/remove log level    from the current log levels in MILTER_LOG_LEVEL    environment environment.

#### Fixes

* Fixed a read block bug when readable data is available.

### Ruby milter

#### Improvements

* [configuration] Used 'accept' as default value for    fallback status.

### milter-performance-check

#### Improvements

* Supported CentOS 5.

### Document

#### Fixes

* Used Milter::VERSION instead of Milter::TOOLKIT_VERSION    for confirming Ruby milter's version.    [Reported by Mitsuru Ogino]

### Thanks

* Mitsuru Ogino
* OBATA Akio
* moto kawasaki

## 1.6.9: 2011-04-26 {#release-1-6-9}

A bug fix release of 1.6.8.

### All

#### Improvements

* autogen.sh supports bash.    [Reported by Kenji Shiono]

### Document

#### Improvements

* Followed Ruby milter's change.    [Reported by akira yamada]

### milter manager

#### Improvements

* Added    database.extra_options    configuration item.
* Supported exception handling in callback.

#### Fixes

* Fixed a bug that define_connection_checker raises an    exception.    [Reported by Kenji Shiono]

### milter-client

#### Improvements

* Supported error report when UNIX domain socket mode    change is failed.

### milter-performance-check

#### Improvements

* Added --starttls option.
* Added --auth-user option.
* Added --auth-password option.
* Added --auth-mechanism option.
* Added --auth-map option.

#### Fixes

* Fixed a bug that --smtp-port is ignored.

### Thanks

* Kenji Shiono
* akira yamada

## 1.6.8: 2011-04-15 {#release-1-6-8}

A bug fix release of 1.6.7.

### All

#### Improvements

* Don't create needless directories on install.    [Reported by OBATA Akio]

### Document

#### Improvements

* Changed target CentOS version to 5.6.

#### Fixes

* Fixed wrong internal links.

### milter-manager

#### Improvements

* Added    manager.event_loop_created    configuration item.

### Ruby milter

#### Improvements

* Added    milter.event_loop_created    configuration item.
* Added Milter::ClientSession#worker_id.
* Added Milter::ClientSession#[].

### milter-core

#### Improvements

* Followed the Sendmail behavior rather than Postfix    behavior on adding a header.

### milter-server

#### Improvements

* Don't require Ruby's header files until they are needed.

#### Fixes

* Fixed a bug that milter-test-server can't be detected.

### Thanks

* OBATA Akio

## 1.6.7: 2011-04-08 {#release-1-6-7}

A bug fix release of 1.6.6.

### All

#### Improvements

* Don't create needless directories on install.    [Reported by OBATA Akio]

#### Fixes

* Fixed a bug that Ruby/GLib2 in system can't be found.    [Reported by OBATA Akio]

### Package

#### Fixes

* [RPM] Fixed dependencies.
* [Debian] Fixed dependencies.
* [Debian] Don't use deprecated option in init script.
* [RPM] Don't use deprecated option in init script.

### milter-manager

#### Fixes

* [S25R] Fixed a bug that milter is always run.

### milter-core

#### Improvements

* Added "+LEVEL1|LEVEL2|..." syntax to add log levels.
* Added "-LEVEL1|LEVEL2|..." syntax to remove log levels.

### milter-client

#### Improvements

* Added --log-level option.
* Added --quiet option.

### Thanks

* OBATA Akio

## 1.6.6: 2011-04-07 {#release-1-6-6}

This release improves Ruby support and Solaris support.

### All

#### Improvements

* Added --with-bundled-ruby-glib2 configure option for    using bundled Ruby/GLib2 anytime.
* Supported Solaris.

### Document

#### Fixes

* [Debian] add missing GROUP=postfix in configuration.    [Reported by Jordao]

### Package

#### Improvements

* Supported Solaris.
* Fedora 13 -&gt; 14.

### milter-core

#### Improvements

* Set 'warning' log level by default.
* Set 'statistics' log level by default.
* Set 'message' log level by default.
* Changed syslog level for statistics log to LOG_NOTICE    level from LOG_INFO level .

#### Fixes

* Fixed a memory leak on read error.

### milter-manager

#### Improvements

* Supported database connection.
* Disabled S25R applicable condition for IPv6 connection    by default. It's customizable by s25r.check_only_ipv4=.
* Added --n-workers option.
* Added --event-loop-backend option.
* Supported log configuration in configuration file.

#### Fixes

* Fixed a crash bug on reloading.    [Reported by Kenji Shiono]

### libmilter-compatible

#### Improvements

* Supported event loop backend customize by environment    variable:
  * MILTER_EVENT_LOOP_BACKEND=libev -&gt; libev is used
  * MILTER_EVENT_LOOP_BACKEND=glib -&gt; GLib is used (default)

### milter-test-client

#### Improvements

* Added --pid-file option.
* Supported shutdown by SIGTERM.

### milter-test-server

#### Improvements

* Added --envelope-from option.
* Deprecated --from option.
* Added --envelope-recipient option.
* Deprecated --recipient option.
* Added --connect-macro option.
* Added --helo-macro option.
* Added --envelope-from-macro option.
* Added --envelope-recipient-macro option.
* Added --data-macro option.
* Added --end-of-header-macro option.
* Added --end-of-message-macro option.
* Supported result body output in non-ASCII encoding.

### milter-report-statistics

#### Improvements

* Supported Solaris.
* Added --pid option.
* Added --pid-directory option.

### Ruby milter

#### Improvements

* Added --maintenance-interval option.
* Added --run-gc-on-maintain option.
* Added --environment option.
* Added --max-file-descriptors option.
* Added --pid-file option.
* Added Milter::ClientSession#delete_header.
* Added Milter::ClientSession#insert_header.
* Added Milter::ClientSession#replace_body.
* Added Milter::ClientSession#change_from.
* Added. Milter::ClientSession#add_recipient.
* Added Milter::ClientSession#delete_recipient.
* Added Milter::ClientSession#delay_response.
* Added Milter::ClientSession#progress.
* Added Milter::ClientSession#discard.
* Added Milter::EventLoop.
* Supported configuration file.
* Added Milter::SocketAddress#ipv4?.
* Added Milter::SocketAddress#ipv6?.
* Added Milter::SocketAddress#unix?.

#### Fixes

* Fixed a crash bug.

### Thanks

* Jordao
* Kenji Shiono

## 1.6.5: 2011-01-26 {#release-1-6-5}

A bug fix release of 1.6.4.

### milter manager

#### Fixes

* Fixed a bug that "Sendmail Compatible" applicable    condition doesn't set applicable if_addr and id_name    macro value.    [Patch by Kenji Shiono]
* Fixed a crash bug that may be caused SMTP client    disconnection is detected.    [Reported by Kenji Shiono]

### milter-manager-log-analyzer

#### Improvements

* Supported parsing Authentication-Results added by ENMA.

### Ruby milter

#### Improvements

* Supported effective user and group change.

### Thanks

* Kenji Shiono

## 1.6.4: 2011-01-21 {#release-1-6-4}

A bug fix release of 1.6.3.

### milter-client

#### Fixes

* Used event loop usage as before when event loop backend    is GLib.

## 1.6.3: 2011-01-20 {#release-1-6-3}

A performance improvement release. This release includesa few performance improvement features but they are marked'experimental'. They will be 'stable' feature in 1.8.0.

### milter manager

#### Improvements

* Upgraded bundled Ruby/GLib2 to 0.90.5 from 0.19.4.
* Supported Ruby 1.9.2.
* Added    manager.fallback_status    that specifies a status returned to SMTP server on    internal error.
* Added    manager.fallback_status_at_disconnect    that specifies a status returned to SMTP server when    disconnection is detected. [Suggested by Kenji Shiono]
* Added DATA event emuration that is enabled when SMTP    server uses milter protocol version 3 or smaller.
* Added    manager.event_loop_backend    that specifies event loop backend. (experimiental)
* Added    manager.n_workers    that specifies number of worker processes. (experimental)
* Added    manager.packet_buffer_size    that specifies buffer size for send packets. (experimental)

#### Fixes

* Fixed a bug that    manager.use_netstat_connection_checker    doesn't work with Postfix 2.3. [Reported by Kenji Shiono]
* Fixed a DATA event timing when some child milters exist.    [Reported by Kenji Shiono]

### Document

#### Improvements

* Described about Postfix's {client_addr}. [Reported by Kenji Shiono]

### milter-client

#### Improvements

* Supported multi process. (experimental)
* Supported libev as event loop backend. (experimental)
  * Bundled libev 4.03.
* Made write asyncronize.
* Supported send packets buffering. (experimental)

### milter-server

#### Improvements

* Added more condition checks on evnets.

#### Fixes

* Fixed a bug that timeout detection doesn't work.    [Reported by Kenji Shiono]

### Ruby milter

#### Improvements

* Added ruby-milter.pc.
* Added --packet-buffer-size option that specifies send    packet buffer size. (experimental)
* Added --n-workers option thst specifies number of worker    processes. (epxerimental)
* Added --event-loop-backend option that specifies event    loop backend. (experimental)

### milter-test-client

#### Improvements

* Added    --n-workers option    that specifies number of worker processes. (experimental)
* Added    --event-loop-backend    option that specifies event loop backend. (experimental)
* Added    --packet-buffer-size    option that specifies send packets buffer size. (experimental)

### milter-performance-check

#### Improvements

* Added    --n-additional-lines    option that grows body size.
* Added    --report-failure-responses    option that enables failure SMTP sesseion response    report on the last.
* Added    --report-periodically    option that enables periodical statistics report.
* Added    --flood    option that enables flood mood that sends flood of mails    in specified period.

### milter-report-statistics

#### Improvements

* Added: milter-report-statistics.rd.ja

### Packet

* Updated package repository RPM for CentOS: 1.0.0-0 -&gt; 1.0.0-1.

### Thanks

* Kenji Shiono

## 1.6.2: 2010-11-23 {#release-1-6-2}

A bug fix release of 1.6.1.

### milter manager

#### Improvements

* Made PID file directory prepareing process in init    script on Debian robust.    [Reported by Kenji Shiono]
* Used gint64 for time_t.    [Suggested by OBATA Akio]

#### Fixes

* Fixed missing temporary file close.    [Reported by Kenji Shiono]

### milter manager admin

#### Improvements

* Documented required sqlite3-ruby version on CentOS.    [Reported by Kenji Shiono]

### Ruby milter

#### Improvements

* Made milter-tarpit.rb, a sample milter, asynchronous.    [Reported by Kenji Shiono]
* Provided all milter API.

#### Fixes

* Fixed a typo in command line option.    [Reported by Kenji Shiono]

### Thanks

* Kenji Shiono
* OBATA Akio

## 1.6.1: 2010-08-21 {#release-1-6-1}

A bug fix release of 1.6.0.

### milter manager

#### Fixes

* Fixed a bug that no statistics information isn't logged to syslog.    [Reported by akira yamada]

### Thanks

* akira yamada

## 1.6.0: 2010-08-11 {#release-1-6-0}

The first release of stable 1.6.x series.

### milter manager

#### Improvements

* Added parsers for Postfix cidr_table(5) and regexp_table(5):    PostfixCIDRTable, PostfixRegexpTable

## 1.5.3: 2010-08-03 {#release-1-5-3}

The last release of 1.5.x series. (plan)

### Document

#### Improvements

* Added a description for    SocketAddress#to_ip_address.

### milter manager

#### Improvements

* Ensured to reply for negotiation on negotiation failure.
* Reduced the default timeout for reporting timeout error    to MTA. The previous default timeout is the same as MTA    default. With the value, we can't have a time to report    timeout error to MTA.
* command launcher: Supported syslog.
* Added an applicable condition:
  * Trust
* Supported Solaris. [Patched by SATOH Fumiyasu]

### milter manager admin

#### Improvements

* Supported Rails 2.3.8.

### milter-test-server

#### Improvements

* Added --color option.
* Added --threads option.

### milter-core

#### Improvements

* Chanaged default log level to output error and critical message.

### Ruby milter

#### Improvements

* Added --user, --gorup, --unix-socket-group,    --unix-socket-mode, --syslog, --library-version options.
* Added milter-test-client implemented by Ruby as a sample.
* Added milter-regexp.rb as a sample.

### Thanks

* SATOH Fumiyasu

## 1.5.2: 2010-05-29 {#release-1-5-2}

A bug fix release of 1.5.1.

We recommend development version users who use a milter that usesNO_REPLY_* or milter-greylist 4.3.x upgrade to this version.

### Document

#### Improvements

* Created available milters list.
* Updated recommended milter-greylist configuration.

### milter manager

#### Improvements

* Supported S25R whitelist customize     and    blacklist    customize.

### milter-manager-log-analyzer

#### Improvements

* Supported milter-greylist 4.3.x.

### milter-toolkit

#### Improvements

* Used inet_pton()/inet_pton() instead of    inet_aton()/inet_ntoa(). [Suggested by SATOH Fumiyasu]

### Thanks

* SATOH Fumiyasu
* ROSSO

## 1.5.1: 2010-04-20 {#release-1-5-1}

A bug fix release of 1.5.0.

It includes a memory leak fix derived from Ruby/GLib2because bundled Ruby/GLib2 is updated. If bundled Ruby/GLib2is used, upgrade is recommended.

### Document

#### Improvements

* Added install document for development release on Ubuntu    Karmic Koara.
* Added a description that installs Rack    explicitly. [Reported by Tsuchiya]

#### Fixes

* FreeBSD: Fixed package name [Reported by Tsuchiya]

### libmilter-core

#### Improvements

* Supported syslog level change by MILTER_LOG_SYSLOG_LEVEL    environment variable.
* Added memory profiler.

### milter manager

#### Improvements

* Supported Solaris. [Reported and patched by SATOH Fumiyasu]
* Bundled Ruby/GLib2 0.19.4.

### milter-test-client

#### Improvements

* Added    --report-memory-profile option.

### Thanks

* Tsuchiya
* SATOH Fumiyasu

## 1.5.0: 2010-03-29 {#release-1-5-0}

A development release.

### Document

#### Improvements

* For Debian GNU/Linux・Ubuntu:
  * Removed needless group change description [Suggested by ZnZ]
* For CentOS:
  * Used Yum instead of RPM directly.
* For FreeBSD:
  * Upgraded target version: 7.2-RELEASE -&gt; 8.0-RELEASE
  * Changed to use CPPFLAGS instead of CFLAGS for configure.

#### Bug fixes

* For FreeBSD:
  * Fixed pw command options.

### milter manager

#### Improvements

* init script for Debian GNU/Linux:
  * Supported 'status'. [Suggested by ZnZ]
  * Delayed parameter checks until they are needed.      [Suggested by ZnZ]
  * Removed needless dependencies. [Suggested by ZnZ]
* [#2921072] Showed loaded configuration file path on    verbose mode. [Suggested by Antuan Avdioukhine]
* [#2921072] Showed file and line that are changed the    configuration item. [Suggested by Antuan Avdioukhine]
* [#2921078] Supported no child milter work.    [Suggested by Antuan Avdioukhine]
* Added configuration items:
  * remove_milter
  * manager.connection_check_interval
  * manager.define_connection_checker
  * manager.use_netstat_connection_checker
  * manager.report_memory_statistics
  * manager.maintained
  * stress.threshold_n_connections
  * stress.threshold_n_connections=
  * remote_network.add_local_address
* Added new applicable conditions
  * No Stress
  * Stress Notify
* Bundled Ruby/GLib 0.19.3. (For FreeBSD)
* Changed to use /usr/sbin/service or /sbin/service if it    is available.
* Supported OpenDKIM detection on CentOS.
* Supported Syslog facility change:    MILTER_LOG_SYSLOG_FACILITY environment variable is used.
* manager.max_file_descriptors:    Changed both of soft and hard limit not only soft limit.
* Supported [Munin](http://munin-monitoring.org/).
* Speed up and effective memory usage.

#### Bug fixes

* FreeBSD: Fixed OpenDKIM detection when any profiles    aren't used in /etc/rc.conf. [Reported by Tsuchiya]
* Fixed a bug that applicable condition is ignored by    Ruby's GC.

#### Experimental

* Introduced policy framework to specify condition and    milter all together.

### milter-toolkit

* Supported milter development by Ruby bindings: Ruby integration
  * Specify --enable-ruby-milter option in configure.

### milter-manager-log-analyzer

* Speed up (almost 2 times faster)
* Supported visualization about number connections that is    disconnection from SMTP clients.

### milter-performance-check

* New options
  * --n-concurrent-connections:      Specifies maximum number of concurrency connections.

### milter-test-client

* New options:
  * --no-report-request:      Doesn't dump requests from MTA.
  * --user:      Specifies effective user.
  * --group:      Specifies effective group.
  * --unix-socket-group:      Specifies UNIX domain socket's group.

### Package

#### CentOS

* Split to some packages.

### Test

* Supported [Cutter](http://cutter.sourceforge.net/) 1.1.0

### Thanks

* ZnZ
* Tsuchiya
* Antuan Avdioukhine

## 1.4.2: 2010-03-29 {#release-1-4-2}

A bug fix release for 1.4.1.

### Document

* Upgraded target FreeBSD version: 7.2-RELEASE -&gt; 8.0-RELEASE
* Changed to use CPPFLAGS instead of CFLAGS for configure    on FreeBSD.
* Fixed pw command options on FreeBSD.

### milter manager

#### Bug fixes

* Fixed a bug that socket group isn't effected when    both effective user and socket group are specified.
* Fixed a bug that auto milter detection is failed on no    OpenDKIM installed FreeBSD environment.

## 1.4.1: 2009-10-29 {#release-1-4-1}

A bug fix release for 1.4.0.

### Document

* Upgraded target CentOS version: 5.3 -&gt; 5.4.
* Fixed types. [Yuto Hayamizu]
* Fixed typos. [ZnZ]

### milter manager

#### Improvements

* Bundled Ruby/GLib2 for CentOS.
* add configure options for default configuration value:
  * --with-default-effective-user: effective user
  * --with-default-effective-group: effective group
  * --with-default-socket-group: group of UNIX domain socket
  * --with-default-pid-file: PID file
  * --with-default-connection-spec: listen address

#### Bug fixes

* Fixed a bug that init script overwrites default    configuration value on CentOS. [Reported by gorimaru]
* Fixed a bug that needless commands are sent to finished    child milter on evaluation mode.

### Thanks

* Yuto Hayamizu
* gorimaru
* ZnZ

## 1.4.0: 2009-10-13 {#release-1-4-0}

A stable release.

### Document

* Added install documents for Debian.

### milter-manager

#### Improvements

* Supported OpenDKIM detection on Debian/Ubuntu/FreeBSD.

#### Bug fixes

* Fixed a bug that adding header statistics isn't logged    on evaluation mode.

## 1.3.1: 2009-09-16 {#release-1-3-1}

A development release. Evaluation mode was added.

### milter-manager

#### Improvements

* Added evaluation    mode    that ignores a result of child milter.
* Added configuration items:
  * max number of concurrent connections:      manager.max_connections
  * max number of file descriptors:      manager.max_file_descriptors
* Supported EPEL [Reported by Syunsuke Komma]
* Supported timeout configuration based on    milter-greylist's tarpit configuration.

### milter-toolkit

* Added more the Ruby bindings [Yuto Hayamizu]

### milter manager admin

* Supported Rails 2.3.4

### milter-test-client

* Added --syslog options that logs to syslog.

### milter-manager-log-analyzer

* Supported milter-greylist's SPF result.

### Thanks

* Yuto Hayamizu
* Syunsuke Komma

## 1.3.0: 2009-08-12 {#release-1-3-0}

A development release.

### milter-manager

#### Improvements

* Improved a process for multi messages in a SMTP session.

#### Bug fixes

* Fixed a bug that quarantine is ignored.    [Reported by Tsuchiya]
* Fixed a bug that discard is ignored.    [Reported by Tsuchiya]
* Fixed a bug that SEGV on non header mail.    [Reported by Павел Гришин]

### milter-test-server

* Suppressed needless abort.
* Changed to send 'continue' on 'quarantine'.

### milter-manager-log-analyzer

* Supported virus detection result of clamav-milter.

### Thanks

* Tsuchiya
* Павел Гришин

## 1.2.0: 2009-07-17 {#release-1-2-0}

A stable release.

### milter-manager

#### Improvements

* Supported DATA stopper independently of MTA's milter    protocol.

#### Bug fixes

* Fixed a timeout problem when all milters are stopped on    message processing. [Reported by sgyk]
* Fixed a problem that milter-manager doesn't work with    Postfix 2.3.3. [Reported by Fumihisa Tonaka]

### Thanks

* sgyk
* Fumihisa Tonaka

## 1.1.1: 2009-07-03 {#release-1-1-1}

A release to be the next stable release 1.2.0.

### milter-manager

#### Improvements

* Reduced needless abort calls.
* Reduced statistics logs.
* Supported multiple instances.
  * manager.custom_configuration_directory
* Added a configuration item that milter-manager waits how    many seconds when milter-manager can't accept    connections from MTA.
  * manager.suspend_time_on_unacceptable
* Supported Momonga Linux [Suggested by Fumihisa Tonaka]
* Supported absolute configuration file path.
* Changed milter stop behavior on RCPT TO. A milter    process for a stopped recipient is skipped. A milter    process for other recipients are not effected.
* Supported stopper callback on all events even if an    event is ignored by milter. (events marked as SMFIP_NO*)
* Supported multi mail transactions [Reported by sgyk]
* Supported local configuration file    "milter-manager.local.conf" that is loaded automatically    if it exists.
* [experimental] Added a sample to only apply a milter to    restricted users.

#### Bug fixes

* Fixed a race condition on multiple milters running.
* Fixed a problem that error status isn't replied to MTA.    [Reported by Fumihisa Tonaka]
* Fixed a problem that a milter application stopped    effects other milter application stopped.    [Reported by sgyk]

### milter-test-server

* Changed to report a message is rejected or temporary    failed if all recipients are rejected or temporary failed.

### milter-manager-log-analyzer

* Supported application result graphs for each milter.
* Supported statistics graphs for each method.

### Thanks

* Fumihisa Tonaka
* sgyk

## 1.1.0: 2009-06-02

A development release leading up to the next stable release 1.2.0.

### milter-manager

* Reduced needless logs.
* Supported ENMA auto detection on FreeBSD.
* Supported ClamAV 0.95 auto detection.
* Fixed dkim-filter's skip action is ignored for a mail    over 65535 bytes.
* Supported unknown address family on connect.
* Supported fallback status for each child milter.    (milter.fallback_status)
* Added milter ID to debug log.
* Fixed memory leaks.
* Supported periodical maintenance process.    (manager.maintenance_interval)
* Added workaround for Ruby/GLib 0.17.0.
* Supported backtrace log on crash.
* Added callback events to stop milter application:
  * condition.define_helo_stopper
  * condition.define_data_stopper
  * condition.define_end_of_header_stopper
  * condition.define_body_stopper
  * condition.define_end_of_message_stopper
* Fixed a milter-manager related process isn't terminated    on kill.
* Stopped accepting new connection on too many file    descriptors opened.

### milter manager admin

* Supported Ruby on Rails 2.3.2.

### milter-test-server

* Supported reply-code.
* Added options for authentication related macros:
  * --authenticated-name=NAME
  * --authenticated-type=TYPE
  * --authenticated-author=AUTHOR

### milter-manager-log-analyzer

* Reduced memory usage.

### Documentation

* Fixed a link: [Павел Гришин]

## 1.0.1: 2009-05-14

A bug fix release of 1.0.0.

### milter-manager

* Fixed a bug that milter-manager isn't restarted on    updating RPM package.

### milter manager admin

* Specified used gem version    [Reported by nhisa]

## 1.0.0: 2009-04-16

The first stable release.

### Documentation

* Added man pages for commands.
* Added --external option to clamav-milter's configuration.
* Changed install documents for Ubuntu and CentOS to    package based installation.

### milter-manager

* Added ENMA detection on CentOS.

### milter-performance-check

* Worked --n-mails option with --period/--interval option.

## 0.9.0: 2009-03-10

Speed and stability are improved.

### milter-manager

* Added a feature to change group of UNIX domain socket.
* Speed up:
  * Changed to send milter commands in a packet.
  * Changed to process mail body on memory as far as possible.
* configure:
  * --with-rcddir: Add a option to specify pkgsrc's rc.d directory.
* Bug fixes:
  * Fixed a bug that a file descriptor is too closed.
  * Fixed a bug that 'temporary failure' is reported as      'reject' in log.

### New applicable conditions

* sendmail-compatible:    It's a feature to avoid macro related incompatibility    between Sendmail's milter implementation and Postfix's    milter implementation.    (ref. [Postfix before-queue Milter support -    Workarounds](http://www.postfix.org/MILTER_README.html#workarounds))
  It's not an applicable condition but it uses applicablecondition framework to convert macros passed to a milterby MTA. dnsbl-milter can be worked with Postfix withouta patch(*) by the feature.
  (*) [[2594714] Postfix support](http://sourceforge.net/tracker/?func=detail&atid=1015126&aid=2594714&group_id=210782)
* authentication: It's an applicable condition to apply a    milter only when a connection is authenticated or    unauthenticated.

### milter-performance-check

* Added a feature to send a file as a mail.
* Added a feature to send each file under specified    directories as a mail.
* --from, --recipient, --force-from, --force-recipient:    Added features to override from address and/or recipient    address.
* --interval: Added a feature to send a mail at intervals.
* --period: Added a feature to send mails at the same    interval in period.
* --shuffle: Added a feature to send mails in random order.

### milter-manager-log-analyzer

* [incompatible]: Added an item "abort" to processed mail graph.

## 0.8.0: 2009-02-06

* New features
  * New tools:
    * milter-manager-log-analyzer:        It visualizes milter-manager's log.
    * milter manager admin:        Web interface for administrating milter-manager.
    * Screenshots of the above two tools:        The bottom of Install page.
  * Add milter detection method for pkgsrc.
  * Support CentOS.
  * Applicable condition
    * Support getting status of other milter.
    * Support getting/setting macros of milter.
* Update S25R (2009/02/01 version)
* Bug fixes
  * [#2518782] typo in configure: [OBATA Akio]

## 0.7.0: 2009-01-16

* Initial release on SF.net.

