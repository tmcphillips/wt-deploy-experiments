## 2020-03-17 Attempt to start WT services on artemis

### Deployed WT services to artemis
- Started from checkpoint following third increment to system backup on [2020-03-16](../2020-03-16%20set%20up%20artemis%20for%20running%20whole%20tale%20locally.md).

- Ran `services` Makefile target without obvious errors:
	```
	tmcphill@artemis:~/deploy-dev$ make services
	git clone https://github.com/whole-tale/gwvolman src/gwvolman
	Cloning into 'src/gwvolman'...
	remote: Enumerating objects: 98, done.
	remote: Counting objects: 100% (98/98), done.
	remote: Compressing objects: 100% (63/63), done.
	remote: Total 1459 (delta 59), reused 67 (delta 35), pack-reused 1361
	Receiving objects: 100% (1459/1459), 707.92 KiB | 5.71 MiB/s, done.
	Resolving deltas: 100% (931/931), done.
	git clone https://github.com/whole-tale/girder_wholetale src/wholetale
	Cloning into 'src/wholetale'...
	remote: Enumerating objects: 111, done.
	remote: Counting objects: 100% (111/111), done.
	remote: Compressing objects: 100% (81/81), done.
	remote: Total 6367 (delta 63), reused 57 (delta 30), pack-reused 6256
	Receiving objects: 100% (6367/6367), 5.84 MiB | 16.24 MiB/s, done.
	Resolving deltas: 100% (4565/4565), done.
	git clone https://github.com/whole-tale/girder_wt_data_manager src/wt_data_manager
	Cloning into 'src/wt_data_manager'...
	remote: Enumerating objects: 32, done.
	remote: Counting objects: 100% (32/32), done.
	remote: Compressing objects: 100% (26/26), done.
	remote: Total 1226 (delta 11), reused 23 (delta 6), pack-reused 1194
	Receiving objects: 100% (1226/1226), 262.09 KiB | 4.16 MiB/s, done.
	Resolving deltas: 100% (781/781), done.
	git clone https://github.com/whole-tale/wt_home_dirs src/wt_home_dir
	Cloning into 'src/wt_home_dir'...
	remote: Enumerating objects: 45, done.
	remote: Counting objects: 100% (45/45), done.
	remote: Compressing objects: 100% (40/40), done.
	remote: Total 611 (delta 16), reused 27 (delta 4), pack-reused 566
	Receiving objects: 100% (611/611), 148.01 KiB | 2.60 MiB/s, done.
	Resolving deltas: 100% (367/367), done.
	git clone https://github.com/whole-tale/dashboard src/dashboard
	Cloning into 'src/dashboard'...
	remote: Enumerating objects: 126, done.
	remote: Counting objects: 100% (126/126), done.
	remote: Compressing objects: 100% (93/93), done.
	remote: Total 11900 (delta 67), reused 65 (delta 33), pack-reused 11774
	Receiving objects: 100% (11900/11900), 13.16 MiB | 27.78 MiB/s, done.
	Resolving deltas: 100% (7925/7925), done.
	docker run --rm -ti -v ${PWD}/src/dashboard:/usr/src/node-app -w /usr/src/node-app node:carbon-slim sh -c "$(cat dashboard_local/initial_bui                                                                                                                                              ld.sh)"
	Unable to find image 'node:carbon-slim' locally
	carbon-slim: Pulling from library/node
	804555ee0376: Pull complete
	2706bdf80250: Pull complete
	3093207c38c0: Pull complete
	215a12a9bee2: Pull complete
	c93986df02bb: Pull complete
	Digest: sha256:6f47d69e8deac79b425d3f5d49ee0f804dbfb07bfc0f8ee8688c1bff0fb50448
	Status: Downloaded newer image for node:carbon-slim
	npm WARN deprecated bower@1.8.8: We don't recommend using Bower for new projects. Please consider Yarn and Webpack or Parcel. You can read h                                                                                                                                              ow to migrate legacy project here: https://bower.io/blog/2017/how-to-migrate-away-from-bower/
	/usr/local/bin/bower -> /usr/local/lib/node_modules/bower/bin/bower
	+ bower@1.8.8
	added 1 package from 1 contributor in 2.301s
	Downloading binary from https://github.com/sass/node-sass/releases/download/v4.9.1/linux-x64-57_binding.node
	Download complete..] - :
	Binary saved to /usr/src/node-app/node_modules/node-sass/vendor/linux-x64-57/binding.node
	Caching binary to /root/.npm/node-sass/4.9.1/linux-x64-57_binding.node
	Binary found at /usr/src/node-app/node_modules/node-sass/vendor/linux-x64-57/binding.node
	Testing binary
	Binary is fine
	added 1848 packages from 1348 contributors and audited 156602 packages in 46.38s
	found 17841 vulnerabilities (328 low, 1173 moderate, 16338 high, 2 critical)
	  run `npm audit fix` to fix them, or `npm audit` for details
	Reading package lists... Done
	Building dependency tree
	Reading state information... Done
	The following additional packages will be installed:
	  git-man less libbsd0 libcurl3-gnutls libedit2 liberror-perl libexpat1 libgdbm3 libgpm2 libncurses5 libperl5.24 libpopt0 libx11-6
	  libx11-data libxau6 libxcb1 libxdmcp6 libxext6 libxmuu1 netbase openssh-client patch perl perl-base perl-modules-5.24 rename rsync xauth
	Suggested packages:
	  gettext-base git-daemon-run | git-daemon-sysvinit git-doc git-el git-email git-gui gitk gitweb git-arch git-cvs git-mediawiki git-svn                                                                                                                                                     gpm keychain libpam-ssh monkeysphere ssh-askpass ed diffutils-doc perl-doc libterm-readline-gnu-perl | libterm-readline-perl-perl make                                                                                                                                                    openssh-server
	The following NEW packages will be installed:
	  git git-man less libbsd0 libcurl3-gnutls libedit2 liberror-perl libexpat1 libgdbm3 libgpm2 libncurses5 libperl5.24 libpopt0 libx11-6                                                                                                                                                      libx11-data libxau6 libxcb1 libxdmcp6 libxext6 libxmuu1 netbase openssh-client patch perl perl-modules-5.24 rename rsync xauth
	The following packages will be upgraded:
	  perl-base
	1 upgraded, 28 newly installed, 0 to remove and 4 not upgraded.
	Need to get 17.0 MB of archives.
	After this operation, 82.8 MB of additional disk space will be used.
	Get:1 http://deb.debian.org/debian stretch/main amd64 perl-base amd64 5.24.1-3+deb9u6 [1345 kB]
	Get:3 http://deb.debian.org/debian stretch/main amd64 perl-modules-5.24 all 5.24.1-3+deb9u6 [2725 kB]
	Get:4 http://deb.debian.org/debian stretch/main amd64 libgdbm3 amd64 1.8.3-14 [30.0 kB]
	Get:5 http://deb.debian.org/debian stretch/main amd64 libperl5.24 amd64 5.24.1-3+deb9u6 [3525 kB]
	Get:2 http://security-cdn.debian.org/debian-security stretch/updates/main amd64 libcurl3-gnutls amd64 7.52.1-5+deb9u10 [290 kB]
	Get:6 http://deb.debian.org/debian stretch/main amd64 perl amd64 5.24.1-3+deb9u6 [218 kB]
	Get:7 http://deb.debian.org/debian stretch/main amd64 libexpat1 amd64 2.2.0-2+deb9u3 [83.7 kB]
	Get:8 http://deb.debian.org/debian stretch/main amd64 liberror-perl all 0.17024-1 [26.9 kB]
	Get:9 http://deb.debian.org/debian stretch/main amd64 git-man all 1:2.11.0-3+deb9u5 [1433 kB]
	Get:10 http://deb.debian.org/debian stretch/main amd64 git amd64 1:2.11.0-3+deb9u5 [4161 kB]
	Get:11 http://deb.debian.org/debian stretch/main amd64 libxau6 amd64 1:1.0.8-1 [20.7 kB]
	Get:12 http://deb.debian.org/debian stretch/main amd64 libpopt0 amd64 1.16-10+b2 [49.4 kB]
	Get:13 http://deb.debian.org/debian stretch/main amd64 netbase all 5.4 [19.1 kB]
	Get:14 http://deb.debian.org/debian stretch/main amd64 less amd64 481-2.1 [126 kB]
	Get:15 http://deb.debian.org/debian stretch/main amd64 libbsd0 amd64 0.8.3-1 [83.0 kB]
	Get:16 http://deb.debian.org/debian stretch/main amd64 libncurses5 amd64 6.0+20161126-1+deb9u2 [93.4 kB]
	Get:17 http://deb.debian.org/debian stretch/main amd64 libedit2 amd64 3.1-20160903-3 [84.8 kB]
	Get:18 http://deb.debian.org/debian stretch/main amd64 libgpm2 amd64 1.20.4-6.2+b1 [34.2 kB]
	Get:19 http://deb.debian.org/debian stretch/main amd64 openssh-client amd64 1:7.4p1-10+deb9u7 [780 kB]
	Get:20 http://deb.debian.org/debian stretch/main amd64 libxdmcp6 amd64 1:1.1.2-3 [26.3 kB]
	Get:21 http://deb.debian.org/debian stretch/main amd64 libxcb1 amd64 1.12-1 [133 kB]
	Get:22 http://deb.debian.org/debian stretch/main amd64 libx11-data all 2:1.6.4-3+deb9u1 [287 kB]
	Get:23 http://deb.debian.org/debian stretch/main amd64 libx11-6 amd64 2:1.6.4-3+deb9u1 [748 kB]
	Get:24 http://deb.debian.org/debian stretch/main amd64 libxext6 amd64 2:1.3.3-1+b2 [52.5 kB]
	Get:25 http://deb.debian.org/debian stretch/main amd64 libxmuu1 amd64 2:1.1.2-2 [23.5 kB]
	Get:26 http://deb.debian.org/debian stretch/main amd64 patch amd64 2.7.5-1+deb9u2 [112 kB]
	Get:27 http://deb.debian.org/debian stretch/main amd64 rename all 0.20-4 [12.5 kB]
	Get:28 http://deb.debian.org/debian stretch/main amd64 rsync amd64 3.1.2-1+deb9u2 [393 kB]
	Get:29 http://deb.debian.org/debian stretch/main amd64 xauth amd64 1:1.0.9-1+b2 [39.6 kB]
	Fetched 17.0 MB in 0s (28.8 MB/s)
	debconf: delaying package configuration, since apt-utils is not installed
	(Reading database ... 7102 files and directories currently installed.)
	Preparing to unpack .../perl-base_5.24.1-3+deb9u6_amd64.deb ...
	Unpacking perl-base (5.24.1-3+deb9u6) over (5.24.1-3+deb9u5) ...
	Setting up perl-base (5.24.1-3+deb9u6) ...
	Selecting previously unselected package perl-modules-5.24.
	(Reading database ... 7102 files and directories currently installed.)
	Preparing to unpack .../00-perl-modules-5.24_5.24.1-3+deb9u6_all.deb ...
	Unpacking perl-modules-5.24 (5.24.1-3+deb9u6) ...
	Selecting previously unselected package libgdbm3:amd64.
	Preparing to unpack .../01-libgdbm3_1.8.3-14_amd64.deb ...
	Unpacking libgdbm3:amd64 (1.8.3-14) ...
	Selecting previously unselected package libperl5.24:amd64.
	Preparing to unpack .../02-libperl5.24_5.24.1-3+deb9u6_amd64.deb ...
	Unpacking libperl5.24:amd64 (5.24.1-3+deb9u6) ...
	Selecting previously unselected package perl.
	Preparing to unpack .../03-perl_5.24.1-3+deb9u6_amd64.deb ...
	Unpacking perl (5.24.1-3+deb9u6) ...
	Selecting previously unselected package libcurl3-gnutls:amd64.
	Preparing to unpack .../04-libcurl3-gnutls_7.52.1-5+deb9u10_amd64.deb ...
	Unpacking libcurl3-gnutls:amd64 (7.52.1-5+deb9u10) ...
	Selecting previously unselected package libexpat1:amd64.
	Preparing to unpack .../05-libexpat1_2.2.0-2+deb9u3_amd64.deb ...
	Unpacking libexpat1:amd64 (2.2.0-2+deb9u3) ...
	Selecting previously unselected package liberror-perl.
	Preparing to unpack .../06-liberror-perl_0.17024-1_all.deb ...
	Unpacking liberror-perl (0.17024-1) ...
	Selecting previously unselected package git-man.
	Preparing to unpack .../07-git-man_1%3a2.11.0-3+deb9u5_all.deb ...
	Unpacking git-man (1:2.11.0-3+deb9u5) ...
	Selecting previously unselected package git.
	Preparing to unpack .../08-git_1%3a2.11.0-3+deb9u5_amd64.deb ...
	Unpacking git (1:2.11.0-3+deb9u5) ...
	Selecting previously unselected package libxau6:amd64.
	Preparing to unpack .../09-libxau6_1%3a1.0.8-1_amd64.deb ...
	Unpacking libxau6:amd64 (1:1.0.8-1) ...
	Selecting previously unselected package libpopt0:amd64.
	Preparing to unpack .../10-libpopt0_1.16-10+b2_amd64.deb ...
	Unpacking libpopt0:amd64 (1.16-10+b2) ...
	Selecting previously unselected package netbase.
	Preparing to unpack .../11-netbase_5.4_all.deb ...
	Unpacking netbase (5.4) ...
	Selecting previously unselected package less.
	Preparing to unpack .../12-less_481-2.1_amd64.deb ...
	Unpacking less (481-2.1) ...
	Selecting previously unselected package libbsd0:amd64.
	Preparing to unpack .../13-libbsd0_0.8.3-1_amd64.deb ...
	Unpacking libbsd0:amd64 (0.8.3-1) ...
	Selecting previously unselected package libncurses5:amd64.
	Preparing to unpack .../14-libncurses5_6.0+20161126-1+deb9u2_amd64.deb ...
	Unpacking libncurses5:amd64 (6.0+20161126-1+deb9u2) ...
	Selecting previously unselected package libedit2:amd64.
	Preparing to unpack .../15-libedit2_3.1-20160903-3_amd64.deb ...
	Unpacking libedit2:amd64 (3.1-20160903-3) ...
	Selecting previously unselected package libgpm2:amd64.
	Preparing to unpack .../16-libgpm2_1.20.4-6.2+b1_amd64.deb ...
	Unpacking libgpm2:amd64 (1.20.4-6.2+b1) ...
	Selecting previously unselected package openssh-client.
	Preparing to unpack .../17-openssh-client_1%3a7.4p1-10+deb9u7_amd64.deb ...
	Unpacking openssh-client (1:7.4p1-10+deb9u7) ...
	Selecting previously unselected package libxdmcp6:amd64.
	Preparing to unpack .../18-libxdmcp6_1%3a1.1.2-3_amd64.deb ...
	Unpacking libxdmcp6:amd64 (1:1.1.2-3) ...
	Selecting previously unselected package libxcb1:amd64.
	Preparing to unpack .../19-libxcb1_1.12-1_amd64.deb ...
	Unpacking libxcb1:amd64 (1.12-1) ...
	Selecting previously unselected package libx11-data.
	Preparing to unpack .../20-libx11-data_2%3a1.6.4-3+deb9u1_all.deb ...
	Unpacking libx11-data (2:1.6.4-3+deb9u1) ...
	Selecting previously unselected package libx11-6:amd64.
	Preparing to unpack .../21-libx11-6_2%3a1.6.4-3+deb9u1_amd64.deb ...
	Unpacking libx11-6:amd64 (2:1.6.4-3+deb9u1) ...
	Selecting previously unselected package libxext6:amd64.
	Preparing to unpack .../22-libxext6_2%3a1.3.3-1+b2_amd64.deb ...
	Unpacking libxext6:amd64 (2:1.3.3-1+b2) ...
	Selecting previously unselected package libxmuu1:amd64.
	Preparing to unpack .../23-libxmuu1_2%3a1.1.2-2_amd64.deb ...
	Unpacking libxmuu1:amd64 (2:1.1.2-2) ...
	Selecting previously unselected package patch.
	Preparing to unpack .../24-patch_2.7.5-1+deb9u2_amd64.deb ...
	Unpacking patch (2.7.5-1+deb9u2) ...
	Selecting previously unselected package rename.
	Preparing to unpack .../25-rename_0.20-4_all.deb ...
	Unpacking rename (0.20-4) ...
	Selecting previously unselected package rsync.
	Preparing to unpack .../26-rsync_3.1.2-1+deb9u2_amd64.deb ...
	Unpacking rsync (3.1.2-1+deb9u2) ...
	Selecting previously unselected package xauth.
	Preparing to unpack .../27-xauth_1%3a1.0.9-1+b2_amd64.deb ...
	Unpacking xauth (1:1.0.9-1+b2) ...
	Setting up libncurses5:amd64 (6.0+20161126-1+deb9u2) ...
	Setting up perl-modules-5.24 (5.24.1-3+deb9u6) ...
	Setting up libgdbm3:amd64 (1.8.3-14) ...
	Setting up libperl5.24:amd64 (5.24.1-3+deb9u6) ...
	Setting up git-man (1:2.11.0-3+deb9u5) ...
	Setting up libpopt0:amd64 (1.16-10+b2) ...
	Setting up libexpat1:amd64 (2.2.0-2+deb9u3) ...
	Setting up less (481-2.1) ...
	debconf: unable to initialize frontend: Dialog
	debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dial                                                                                                                                              og.pm line 76.)
	debconf: falling back to frontend: Readline
	Setting up libgpm2:amd64 (1.20.4-6.2+b1) ...
	Setting up libcurl3-gnutls:amd64 (7.52.1-5+deb9u10) ...
	Setting up libbsd0:amd64 (0.8.3-1) ...
	Setting up rsync (3.1.2-1+deb9u2) ...
	invoke-rc.d: could not determine current runlevel
	invoke-rc.d: policy-rc.d denied execution of restart.
	Setting up perl (5.24.1-3+deb9u6) ...
	update-alternatives: using /usr/bin/prename to provide /usr/bin/rename (rename) in auto mode
	update-alternatives: warning: skip creation of /usr/share/man/man1/rename.1.gz because associated file /usr/share/man/man1/prename.1.gz (of                                                                                                                                               link group rename) doesn't exist
	Setting up patch (2.7.5-1+deb9u2) ...
	Processing triggers for libc-bin (2.24-11+deb9u4) ...
	Setting up libxdmcp6:amd64 (1:1.1.2-3) ...
	Setting up libx11-data (2:1.6.4-3+deb9u1) ...
	Setting up libxau6:amd64 (1:1.0.8-1) ...
	Setting up netbase (5.4) ...
	Setting up libedit2:amd64 (3.1-20160903-3) ...
	Setting up liberror-perl (0.17024-1) ...
	Setting up rename (0.20-4) ...
	update-alternatives: using /usr/bin/file-rename to provide /usr/bin/rename (rename) in auto mode
	update-alternatives: warning: skip creation of /usr/share/man/man1/rename.1.gz because associated file /usr/share/man/man1/file-rename.1p.gz                                                                                                                                               (of link group rename) doesn't exist
	Setting up openssh-client (1:7.4p1-10+deb9u7) ...
	Setting up libxcb1:amd64 (1.12-1) ...
	Setting up git (1:2.11.0-3+deb9u5) ...
	Setting up libx11-6:amd64 (2:1.6.4-3+deb9u1) ...
	Setting up libxmuu1:amd64 (2:1.1.2-2) ...
	Setting up libxext6:amd64 (2:1.3.3-1+b2) ...
	Setting up xauth (1:1.0.9-1+b2) ...
	Processing triggers for libc-bin (2.24-11+deb9u4) ...
	bower es5-shim#^4.5.8       not-cached https://github.com/es-shims/es5-shim.git#^4.5.8
	bower es5-shim#^4.5.8          resolve https://github.com/es-shims/es5-shim.git#^4.5.8
	bower dropzone#^4.3.0       not-cached https://github.com/enyo/dropzone.git#^4.3.0
	bower dropzone#^4.3.0          resolve https://github.com/enyo/dropzone.git#^4.3.0
	bower medium-editor#5.14.4  not-cached https://github.com/daviferreira/medium-editor.git#5.14.4
	bower medium-editor#5.14.4     resolve https://github.com/daviferreira/medium-editor.git#5.14.4
	bower es5-shim#^4.5.8         download https://github.com/es-shims/es5-shim/archive/v4.5.13.tar.gz
	bower dropzone#^4.3.0         download https://github.com/enyo/dropzone/archive/v4.3.0.tar.gz
	bower medium-editor#5.14.4    download https://github.com/daviferreira/medium-editor/archive/5.14.4.tar.gz
	bower dropzone#^4.3.0          extract archive.tar.gz
	bower es5-shim#^4.5.8          extract archive.tar.gz
	bower dropzone#^4.3.0     invalid-meta for:/tmp/4294c729aafcbb5414e29bc0f50bf05c/bower/b168f285c84360eaba85a5928c3588b4-633-MCY5Pw/bower.jso                                                                                                                                              n
	bower dropzone#^4.3.0     invalid-meta The "main" field cannot contain minified files
	bower dropzone#^4.3.0     invalid-meta The "main" field cannot contain minified files
	bower dropzone#^4.3.0         resolved https://github.com/enyo/dropzone.git#4.3.0
	bower es5-shim#^4.5.8         resolved https://github.com/es-shims/es5-shim.git#4.5.13
	bower medium-editor#5.14.4     extract archive.tar.gz
	bower medium-editor#5.14.4     invalid-meta for:/tmp/4294c729aafcbb5414e29bc0f50bf05c/bower/8a7827481638ee3fcab28129d94ebc37-633-YFJLCm/bowe                                                                                                                                              r.json
	bower medium-editor#5.14.4     invalid-meta The "main" field has to contain only 1 file per filetype; found multiple .css files: ["dist/css/                                                                                                                                              medium-editor.css","dist/css/themes/default.css"]
	bower medium-editor#5.14.4         resolved https://github.com/daviferreira/medium-editor.git#5.14.4
	bower dropzone#^4.3.0               install dropzone#4.3.0
	bower es5-shim#^4.5.8               install es5-shim#4.5.13
	bower medium-editor#5.14.4          install medium-editor#5.14.4

	dropzone#4.3.0 bower_components/dropzone

	es5-shim#4.5.13 bower_components/es5-shim

	medium-editor#5.14.4 bower_components/medium-editor
	DEPRECATION: ember-cli-babel 5.x has been deprecated. Please upgrade to at least ember-cli-babel 6.6. Version 5.2.8 located: wholetale -> em                                                                                                                                              ber-cli-component-pod -> ember-cli-babel
	DEPRECATION: ember-cli-babel 5.x has been deprecated. Please upgrade to at least ember-cli-babel 6.6. Version 5.2.8 located: wholetale -> em                                                                                                                                              ber-cli-full-screen -> ember-cli-babel
	DEPRECATION: ember-cli-babel 5.x has been deprecated. Please upgrade to at least ember-cli-babel 6.6. Version 5.2.8 located: wholetale -> em                                                                                                                                              ber-cli-medium-editor -> ember-cli-babel
	DEPRECATION: ember-cli-babel 5.x has been deprecated. Please upgrade to at least ember-cli-babel 6.6. Version 5.2.8 located: wholetale -> em                                                                                                                                              ber-cli-sass-pods -> ember-cli-babel
	DEPRECATION: ember-cli-babel 5.x has been deprecated. Please upgrade to at least ember-cli-babel 6.6. Version 5.2.8 located: wholetale -> em                                                                                                                                              ber-oauth2 -> ember-cli-babel
	DEPRECATION: ember-cli-babel 5.x has been deprecated. Please upgrade to at least ember-cli-babel 6.6. Version 5.2.8 located: wholetale -> em                                                                                                                                              ber-token-auth -> ember-cli-babel
	Could not start watchman
	Visit https://ember-cli.com/user-guide/#watchman for more info.
	⠸ Building[WARN] (broccoli-uglify-sourcemap) Minifying: `assets/vendor.js` took: 28747ms (more than 20,000ms)
	cleaning up...
	Built project successfully. Stored in "dist/".
	File sizes:
	 - dist/assets/vendor-468b71615cf72303033dfaa7aa6e61b3.js: 2.03 MB (513.51 KB gzipped)
	 - dist/assets/vendor-c88e42650449232705375b854b2f2380.css: 598.57 KB (100.79 KB gzipped)
	 - dist/assets/wholetale-0feb901363914b2464d24592033487e4.js: 682.98 KB (108.94 KB gzipped)
	 - dist/assets/wholetale-5bd8ac00fdde70953d662a12d7ea4978.css: 109.51 KB (20.63 KB gzipped)
	 - dist/ember-fetch/fastboot-fetch-805e176077930c98aec5834ae48bd0f2.js: 283 B (199 B gzipped)
	git clone https://github.com/whole-tale/globus_handler src/globus_handler
	Cloning into 'src/globus_handler'...
	remote: Enumerating objects: 19, done.
	remote: Counting objects: 100% (19/19), done.
	remote: Compressing objects: 100% (15/15), done.
	remote: Total 1012 (delta 10), reused 13 (delta 4), pack-reused 993
	Receiving objects: 100% (1012/1012), 177.02 KiB | 3.28 MiB/s, done.
	Resolving deltas: 100% (656/656), done.
	git clone https://github.com/whole-tale/girderfs src/girderfs
	Cloning into 'src/girderfs'...
	remote: Enumerating objects: 75, done.
	remote: Counting objects: 100% (75/75), done.
	remote: Compressing objects: 100% (65/65), done.
	remote: Total 359 (delta 27), reused 55 (delta 10), pack-reused 284
	Receiving objects: 100% (359/359), 127.91 KiB | 2.46 MiB/s, done.
	Resolving deltas: 100% (179/179), done.
	```
### Encountered errors starting WT services

- Ran Makefile `dev` target and saw no obvious errors up to just before invocation of `setup_girder.py` :
	```
	tmcphill@artemis:~/deploy-dev$ make dev
	docker stack deploy --compose-file=docker-stack.yml wt
	Creating network wt_traefik-net
	Creating network wt_celery
	Creating network wt_mongo
	Creating service wt_dashboard_next
	Creating service wt_registry
	Creating service wt_traefik
	Creating service wt_mongo
	Creating service wt_girder
	Creating service wt_redis
	Creating service wt_dashboard
	./run_worker.sh
	[sudo] password for tmcphill:
	Unable to find image 'wholetale/gwvolman:latest' locally
	latest: Pulling from wholetale/gwvolman
	fe703b657a32: Pull complete
	f9df1fafd224: Pull complete
	a645a4b887f9: Pull complete
	57db7fe0b522: Pull complete
	b46231dadc97: Pull complete
	7c11bc1f9ac7: Pull complete
	329613389b64: Pull complete
	de9deda589ad: Pull complete
	f2a86a4bab80: Pull complete
	567ca08cb0c3: Pull complete
	4a81b296947b: Pull complete
	456b68e111cd: Pull complete
	6161c5f0fb6a: Pull complete
	8378ba8904e6: Pull complete
	a65b47bd2167: Pull complete
	72435c8f701a: Pull complete
	4031685f3e65: Pull complete
	576be7878ae5: Pull complete
	125da2dbfecc: Pull complete
	Digest: sha256:1af273ce39daa534812b3cebb9015faed0f7aa7dae9f6e886332663c94ec4869
	Status: Downloaded newer image for wholetale/gwvolman:latest
	646040bee4b8bb9fd91b0d2e6bdc768031a86ab5690e7c282acccfc5b7921ff0
	cid=$(docker ps --filter=name=wt_girder -q);
	while [ -z ${cid} ] ; do \
	          echo ${cid} ; \
	          sleep 1 ; \
	    cid=$(docker ps --filter=name=wt_girder -q) ; \
	done; \
	true

	docker exec --user=root -ti $(docker ps --filter=name=wt_girder -q) pip install -r /gwvolman/requirements.txt -e /gwvolman
	Obtaining file:///gwvolman
	Requirement already satisfied: celery==4.2.1 in /usr/local/lib/python3.5/dist-packages (from -r /gwvolman/requirements.txt (line 1)) (4.2.1)                                                                                                                                              Requirement already satisfied: kombu==4.2.2post1 in /usr/local/lib/python3.5/dist-packages (from -r /gwvolman/requirements.txt (line 2)) (4.                                                                                                                                              2.2.post1)
	Requirement already satisfied: fusepy==3.0.1 in /usr/local/lib/python3.5/dist-packages (from -r /gwvolman/requirements.txt (line 3)) (3.0.1)                                                                                                                                              Collecting girder-client==2.4.0
	  Downloading girder-client-2.4.0.tar.gz (21 kB)
	Collecting girder-worker==0.5.0
	  Downloading girder-worker-0.5.0.tar.gz (938 kB)
	     |████████████████████████████████| 938 kB 3.6 MB/s
	Requirement already satisfied: redis==2.10.6 in /usr/local/lib/python3.5/dist-packages (from -r /gwvolman/requirements.txt (line 6)) (2.10.6                                                                                                                                              )
	Collecting pyOpenSSL==18.0.0
	  Downloading pyOpenSSL-18.0.0-py2.py3-none-any.whl (53 kB)
	     |████████████████████████████████| 53 kB 905 kB/s
	Requirement already satisfied: pycurl in /usr/lib/python3/dist-packages (from -r /gwvolman/requirements.txt (line 8)) (7.43.0)
	Requirement already satisfied: requests in /usr/local/lib/python3.5/dist-packages (from -r /gwvolman/requirements.txt (line 9)) (2.20.1)
	Requirement already satisfied: pyyaml in /usr/local/lib/python3.5/dist-packages (from -r /gwvolman/requirements.txt (line 10)) (5.3)
	Requirement already satisfied: lxml in /usr/local/lib/python3.5/dist-packages (from -r /gwvolman/requirements.txt (line 11)) (4.4.2)                                                                                                                                                      Collecting markdown
	  Downloading Markdown-3.2.1-py2.py3-none-any.whl (88 kB)
	     |████████████████████████████████| 88 kB 4.7 MB/s
	Collecting jwt==0.5.4
	  Downloading jwt-0.5.4-py35-none-any.whl (12 kB)
	Requirement already satisfied: dataone.common==3.2.0 in /usr/local/lib/python3.5/dist-packages (from -r /gwvolman/requirements.txt (line 14)                                                                                                                                              ) (3.2.0)
	Requirement already satisfied: dataone.libclient==3.2.0 in /usr/local/lib/python3.5/dist-packages (from -r /gwvolman/requirements.txt (line                                                                                                                                               15)) (3.2.0)
	Requirement already satisfied: dataone.cli==3.2.0 in /usr/local/lib/python3.5/dist-packages (from -r /gwvolman/requirements.txt (line 16)) (                                                                                                                                              3.2.0)
	Requirement already satisfied: girderfs from git+https://github.com/whole-tale/girderfs@v0.9rc3#egg=girderfs in /usr/local/lib/python3.5/dis                                                                                                                                              t-packages (from -r /gwvolman/requirements.txt (line 17)) (0.8.0)
	Requirement already satisfied: docker>=2.3.0 in /usr/local/lib/python3.5/dist-packages (from gwvolman==0.9.0rc3) (4.1.0)
	Requirement already satisfied: pytz>dev in /usr/local/lib/python3.5/dist-packages (from celery==4.2.1->-r /gwvolman/requirements.txt (line 1                                                                                                                                              )) (2019.3)
	Requirement already satisfied: billiard<3.6.0,>=3.5.0.2 in /usr/local/lib/python3.5/dist-packages (from celery==4.2.1->-r /gwvolman/requirem                                                                                                                                              ents.txt (line 1)) (3.5.0.5)
	Requirement already satisfied: amqp<3.0,>=2.1.4 in /usr/local/lib/python3.5/dist-packages (from kombu==4.2.2post1->-r /gwvolman/requirements                                                                                                                                              .txt (line 2)) (2.5.2)
	Requirement already satisfied: click>=6.7 in /usr/local/lib/python3.5/dist-packages (from girder-client==2.4.0->-r /gwvolman/requirements.tx                                                                                                                                              t (line 4)) (7.0)
	Requirement already satisfied: diskcache in /usr/local/lib/python3.5/dist-packages (from girder-client==2.4.0->-r /gwvolman/requirements.txt                                                                                                                                               (line 4)) (4.1.0)
	Requirement already satisfied: requests_toolbelt in /usr/local/lib/python3.5/dist-packages (from girder-client==2.4.0->-r /gwvolman/requirem                                                                                                                                              ents.txt (line 4)) (0.9.1)
	Requirement already satisfied: six in /usr/local/lib/python3.5/dist-packages (from girder-client==2.4.0->-r /gwvolman/requirements.txt (line                                                                                                                                               4)) (1.14.0)
	Collecting networkx<2
	  Downloading networkx-1.11-py2.py3-none-any.whl (1.3 MB)
	     |████████████████████████████████| 1.3 MB 17.7 MB/s
	Requirement already satisfied: pymongo>=3 in /usr/local/lib/python3.5/dist-packages (from girder-worker==0.5.0->-r /gwvolman/requirements.tx                                                                                                                                              t (line 5)) (3.10.1)
	Requirement already satisfied: setuptools_scm in /usr/local/lib/python3.5/dist-packages (from girder-worker==0.5.0->-r /gwvolman/requirement                                                                                                                                              s.txt (line 5)) (3.4.3)
	Requirement already satisfied: stevedore in /usr/local/lib/python3.5/dist-packages (from girder-worker==0.5.0->-r /gwvolman/requirements.txt                                                                                                                                               (line 5)) (1.31.0)
	Requirement already satisfied: jsonpickle in /usr/local/lib/python3.5/dist-packages (from girder-worker==0.5.0->-r /gwvolman/requirements.tx                                                                                                                                              t (line 5)) (1.2)
	Requirement already satisfied: girder_worker_utils>=0.8.0 in /usr/local/lib/python3.5/dist-packages (from girder-worker==0.5.0->-r /gwvolman                                                                                                                                              /requirements.txt (line 5)) (0.8.5)
	Requirement already satisfied: cryptography>=2.2.1 in /usr/local/lib/python3.5/dist-packages (from pyOpenSSL==18.0.0->-r /gwvolman/requireme                                                                                                                                              nts.txt (line 7)) (2.8)
	Requirement already satisfied: urllib3<1.25,>=1.21.1 in /usr/local/lib/python3.5/dist-packages (from requests->-r /gwvolman/requirements.txt                                                                                                                                               (line 9)) (1.24.3)
	Requirement already satisfied: chardet<3.1.0,>=3.0.2 in /usr/local/lib/python3.5/dist-packages (from requests->-r /gwvolman/requirements.txt                                                                                                                                               (line 9)) (3.0.4)
	Requirement already satisfied: certifi>=2017.4.17 in /usr/local/lib/python3.5/dist-packages (from requests->-r /gwvolman/requirements.txt (l                                                                                                                                              ine 9)) (2019.11.28)
	Requirement already satisfied: idna<2.8,>=2.5 in /usr/local/lib/python3.5/dist-packages (from requests->-r /gwvolman/requirements.txt (line                                                                                                                                               9)) (2.7)
	Requirement already satisfied: setuptools>=36 in /usr/local/lib/python3.5/dist-packages (from markdown->-r /gwvolman/requirements.txt (line                                                                                                                                               12)) (45.1.0)
	Requirement already satisfied: zipstream>=1.1.4 in /usr/local/lib/python3.5/dist-packages (from dataone.common==3.2.0->-r /gwvolman/requirem                                                                                                                                              ents.txt (line 14)) (1.1.4)
	Requirement already satisfied: PyJWT>=1.6.4 in /usr/local/lib/python3.5/dist-packages (from dataone.common==3.2.0->-r /gwvolman/requirements                                                                                                                                              .txt (line 14)) (1.7.1)
	Requirement already satisfied: pyxb>=1.2.6 in /usr/local/lib/python3.5/dist-packages (from dataone.common==3.2.0->-r /gwvolman/requirements.                                                                                                                                              txt (line 14)) (1.2.6)
	Requirement already satisfied: contextlib2>=0.5.5 in /usr/local/lib/python3.5/dist-packages (from dataone.common==3.2.0->-r /gwvolman/requir                                                                                                                                              ements.txt (line 14)) (0.6.0.post1)
	Requirement already satisfied: pyasn1>=0.4.4 in /usr/local/lib/python3.5/dist-packages (from dataone.common==3.2.0->-r /gwvolman/requirement                                                                                                                                              s.txt (line 14)) (0.4.8)
	Requirement already satisfied: rdflib>=4.2.2 in /usr/local/lib/python3.5/dist-packages (from dataone.common==3.2.0->-r /gwvolman/requirement                                                                                                                                              s.txt (line 14)) (4.2.2)
	Requirement already satisfied: iso8601>=0.1.12 in /usr/local/lib/python3.5/dist-packages (from dataone.common==3.2.0->-r /gwvolman/requireme                                                                                                                                              nts.txt (line 14)) (0.1.12)
	Requirement already satisfied: python-dateutil in /usr/local/lib/python3.5/dist-packages (from girderfs->-r /gwvolman/requirements.txt (line                                                                                                                                               17)) (2.6.1)
	Requirement already satisfied: websocket-client>=0.32.0 in /usr/local/lib/python3.5/dist-packages (from docker>=2.3.0->gwvolman==0.9.0rc3) (                                                                                                                                              0.57.0)
	Requirement already satisfied: vine<5.0.0a1,>=1.1.3 in /usr/local/lib/python3.5/dist-packages (from amqp<3.0,>=2.1.4->kombu==4.2.2post1->-r                                                                                                                                               /gwvolman/requirements.txt (line 2)) (1.3.0)
	Requirement already satisfied: decorator>=3.4.0 in /usr/local/lib/python3.5/dist-packages (from networkx<2->girder-worker==0.5.0->-r /gwvolm                                                                                                                                              an/requirements.txt (line 5)) (4.4.1)
	Requirement already satisfied: pbr!=2.1.0,>=2.0.0 in /usr/local/lib/python3.5/dist-packages (from stevedore->girder-worker==0.5.0->-r /gwvol                                                                                                                                              man/requirements.txt (line 5)) (5.4.4)
	Requirement already satisfied: cffi!=1.11.3,>=1.8 in /usr/local/lib/python3.5/dist-packages (from cryptography>=2.2.1->pyOpenSSL==18.0.0->-r                                                                                                                                               /gwvolman/requirements.txt (line 7)) (1.13.2)
	Requirement already satisfied: isodate in /usr/local/lib/python3.5/dist-packages (from rdflib>=4.2.2->dataone.common==3.2.0->-r /gwvolman/re                                                                                                                                              quirements.txt (line 14)) (0.6.0)
	Requirement already satisfied: pyparsing in /usr/local/lib/python3.5/dist-packages (from rdflib>=4.2.2->dataone.common==3.2.0->-r /gwvolman/                                                                                                                                              requirements.txt (line 14)) (2.4.6)
	Requirement already satisfied: pycparser in /usr/local/lib/python3.5/dist-packages (from cffi!=1.11.3,>=1.8->cryptography>=2.2.1->pyOpenSSL=                                                                                                                                              =18.0.0->-r /gwvolman/requirements.txt (line 7)) (2.19)
	Building wheels for collected packages: girder-client, girder-worker
	  Building wheel for girder-client (setup.py) ... done
	  Created wheel for girder-client: filename=girder_client-2.4.0-py3-none-any.whl size=22770 sha256=829f8d4717ce420246ee76bd33ee7a5772f7c0934                                                                                                                                              c37dc996f676291abb62520
	  Stored in directory: /root/.cache/pip/wheels/15/7c/92/18ed3ed12e254474c367ad984b308812096b68a239faea5543
	  Building wheel for girder-worker (setup.py) ... done
	  Created wheel for girder-worker: filename=girder_worker-0.5.0-py3-none-any.whl size=190519 sha256=ca66f714fc0790afaefed03141367220f36c0a5d                                                                                                                                              83d51262387d00da53c466cf
	  Stored in directory: /root/.cache/pip/wheels/ea/44/b6/45aa1c0d58eccf8937178fa12d507d3eaa1637af6ac19e3d74
	Successfully built girder-client girder-worker
	Installing collected packages: girder-client, networkx, girder-worker, pyOpenSSL, markdown, jwt, gwvolman
	  Attempting uninstall: girder-client
	    Found existing installation: girder-client 3.0.6
	    Uninstalling girder-client-3.0.6:
	      Successfully uninstalled girder-client-3.0.6
	  Attempting uninstall: girder-worker
	    Found existing installation: girder-worker 0.6.0
	    Uninstalling girder-worker-0.6.0:
	      Successfully uninstalled girder-worker-0.6.0
	  Attempting uninstall: pyOpenSSL
	    Found existing installation: pyOpenSSL 19.1.0
	    Uninstalling pyOpenSSL-19.1.0:
	      Successfully uninstalled pyOpenSSL-19.1.0
	  Attempting uninstall: gwvolman
	    Found existing installation: gwvolman 0.8.0
	    Uninstalling gwvolman-0.8.0:
	      Successfully uninstalled gwvolman-0.8.0
	  Running setup.py develop for gwvolman
	Successfully installed girder-client-2.4.0 girder-worker-0.5.0 gwvolman jwt-0.5.4 markdown-3.2.1 networkx-1.11 pyOpenSSL-18.0.0
	docker exec -ti $(docker ps --filter=name=wt_girder -q) girder-install plugin plugins/wt_data_manager plugins/wholetale plugins/wt_home_dir                                                                                                                                               plugins/globus_handler
	Installing wt_data_manager...
	Installing requirements.txt for wt_data_manager.
	Requirement already satisfied: globus-sdk in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/wt_data_manager/requirements.tx                                                                                                                                              t (line 1)) (1.8.0)
	Requirement already satisfied: requests<3.0.0,>=2.9.2 in /usr/local/lib/python3.5/dist-packages (from globus-sdk->-r /girder/plugins/wt_data                                                                                                                                              _manager/requirements.txt (line 1)) (2.20.1)
	Requirement already satisfied: six<2.0.0,>=1.10.0 in /usr/local/lib/python3.5/dist-packages (from globus-sdk->-r /girder/plugins/wt_data_man                                                                                                                                              ager/requirements.txt (line 1)) (1.14.0)
	Requirement already satisfied: pyjwt[crypto]<2.0.0,>=1.5.3 in /usr/local/lib/python3.5/dist-packages (from globus-sdk->-r /girder/plugins/wt                                                                                                                                              _data_manager/requirements.txt (line 1)) (1.7.1)
	Requirement already satisfied: idna<2.8,>=2.5 in /usr/local/lib/python3.5/dist-packages (from requests<3.0.0,>=2.9.2->globus-sdk->-r /girder                                                                                                                                              /plugins/wt_data_manager/requirements.txt (line 1)) (2.7)
	Requirement already satisfied: certifi>=2017.4.17 in /usr/local/lib/python3.5/dist-packages (from requests<3.0.0,>=2.9.2->globus-sdk->-r /gi                                                                                                                                              rder/plugins/wt_data_manager/requirements.txt (line 1)) (2019.11.28)
	Requirement already satisfied: urllib3<1.25,>=1.21.1 in /usr/local/lib/python3.5/dist-packages (from requests<3.0.0,>=2.9.2->globus-sdk->-r                                                                                                                                               /girder/plugins/wt_data_manager/requirements.txt (line 1)) (1.24.3)
	Requirement already satisfied: chardet<3.1.0,>=3.0.2 in /usr/local/lib/python3.5/dist-packages (from requests<3.0.0,>=2.9.2->globus-sdk->-r                                                                                                                                               /girder/plugins/wt_data_manager/requirements.txt (line 1)) (3.0.4)
	Requirement already satisfied: cryptography>=1.4; extra == "crypto" in /usr/local/lib/python3.5/dist-packages (from pyjwt[crypto]<2.0.0,>=1.                                                                                                                                              5.3->globus-sdk->-r /girder/plugins/wt_data_manager/requirements.txt (line 1)) (2.8)
	Requirement already satisfied: cffi!=1.11.3,>=1.8 in /usr/local/lib/python3.5/dist-packages (from cryptography>=1.4; extra == "crypto"->pyjw                                                                                                                                              t[crypto]<2.0.0,>=1.5.3->globus-sdk->-r /girder/plugins/wt_data_manager/requirements.txt (line 1)) (1.13.2)
	Requirement already satisfied: pycparser in /usr/local/lib/python3.5/dist-packages (from cffi!=1.11.3,>=1.8->cryptography>=1.4; extra == "cr                                                                                                                                              ypto"->pyjwt[crypto]<2.0.0,>=1.5.3->globus-sdk->-r /girder/plugins/wt_data_manager/requirements.txt (line 1)) (2.19)
	Installing wholetale...
	Installing requirements.txt for wholetale.
	Requirement already satisfied: rdflib in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/wholetale/requirements.txt (line 1)                                                                                                                                              ) (4.2.2)
	Requirement already satisfied: celery[redis]==4.2.1 in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/wholetale/requirement                                                                                                                                              s.txt (line 2)) (4.2.1)
	Requirement already satisfied: kombu==4.2.2post1 in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/wholetale/requirements.t                                                                                                                                              xt (line 3)) (4.2.2.post1)
	Requirement already satisfied: idna==2.7 in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/wholetale/requirements.txt (line                                                                                                                                               4)) (2.7)
	Requirement already satisfied: requests==2.20.1 in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/wholetale/requirements.tx                                                                                                                                              t (line 5)) (2.20.1)
	Requirement already satisfied: redis==2.10.6 in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/wholetale/requirements.txt (                                                                                                                                              line 6)) (2.10.6)
	Requirement already satisfied: girderfs from git+https://github.com/whole-tale/girderfs@v0.9rc3#egg=girderfs in /usr/local/lib/python3.5/dis                                                                                                                                              t-packages (from -r /girder/plugins/wholetale/requirements.txt (line 7)) (0.8.0)
	Requirement already satisfied: gwvolman from git+https://github.com/whole-tale/gwvolman@v0.9rc3#egg=gwvolman in /gwvolman (from -r /girder/p                                                                                                                                              lugins/wholetale/requirements.txt (line 8)) (0.9.0rc3)
	Requirement already satisfied: dataone.common==3.2.0 in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/wholetale/requiremen                                                                                                                                              ts.txt (line 9)) (3.2.0)
	Requirement already satisfied: dataone.libclient==3.2.0 in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/wholetale/require                                                                                                                                              ments.txt (line 10)) (3.2.0)
	Requirement already satisfied: dataone.cli==3.2.0 in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/wholetale/requirements.                                                                                                                                              txt (line 11)) (3.2.0)
	Requirement already satisfied: validators in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/wholetale/requirements.txt (lin                                                                                                                                              e 12)) (0.14.2)
	Requirement already satisfied: html2markdown in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/wholetale/requirements.txt (                                                                                                                                              line 13)) (0.1.7)
	Requirement already satisfied: fs.webdavfs in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/wholetale/requirements.txt (li                                                                                                                                              ne 14)) (0.3.7)
	Requirement already satisfied: isodate in /usr/local/lib/python3.5/dist-packages (from rdflib->-r /girder/plugins/wholetale/requirements.txt                                                                                                                                               (line 1)) (0.6.0)
	Requirement already satisfied: pyparsing in /usr/local/lib/python3.5/dist-packages (from rdflib->-r /girder/plugins/wholetale/requirements.t                                                                                                                                              xt (line 1)) (2.4.6)
	Requirement already satisfied: pytz>dev in /usr/local/lib/python3.5/dist-packages (from celery[redis]==4.2.1->-r /girder/plugins/wholetale/r                                                                                                                                              equirements.txt (line 2)) (2019.3)
	Requirement already satisfied: billiard<3.6.0,>=3.5.0.2 in /usr/local/lib/python3.5/dist-packages (from celery[redis]==4.2.1->-r /girder/plu                                                                                                                                              gins/wholetale/requirements.txt (line 2)) (3.5.0.5)
	Requirement already satisfied: amqp<3.0,>=2.1.4 in /usr/local/lib/python3.5/dist-packages (from kombu==4.2.2post1->-r /girder/plugins/wholet                                                                                                                                              ale/requirements.txt (line 3)) (2.5.2)
	Requirement already satisfied: certifi>=2017.4.17 in /usr/local/lib/python3.5/dist-packages (from requests==2.20.1->-r /girder/plugins/whole                                                                                                                                              tale/requirements.txt (line 5)) (2019.11.28)
	Requirement already satisfied: chardet<3.1.0,>=3.0.2 in /usr/local/lib/python3.5/dist-packages (from requests==2.20.1->-r /girder/plugins/wh                                                                                                                                              oletale/requirements.txt (line 5)) (3.0.4)
	Requirement already satisfied: urllib3<1.25,>=1.21.1 in /usr/local/lib/python3.5/dist-packages (from requests==2.20.1->-r /girder/plugins/wh                                                                                                                                              oletale/requirements.txt (line 5)) (1.24.3)
	Requirement already satisfied: fusepy in /usr/local/lib/python3.5/dist-packages (from girderfs->-r /girder/plugins/wholetale/requirements.tx                                                                                                                                              t (line 7)) (3.0.1)
	Requirement already satisfied: six in /usr/local/lib/python3.5/dist-packages (from girderfs->-r /girder/plugins/wholetale/requirements.txt (                                                                                                                                              line 7)) (1.14.0)
	Requirement already satisfied: python-dateutil in /usr/local/lib/python3.5/dist-packages (from girderfs->-r /girder/plugins/wholetale/requir                                                                                                                                              ements.txt (line 7)) (2.6.1)
	Requirement already satisfied: girder-client in /usr/local/lib/python3.5/dist-packages (from girderfs->-r /girder/plugins/wholetale/requirem                                                                                                                                              ents.txt (line 7)) (2.4.0)
	Requirement already satisfied: girder-worker in /usr/local/lib/python3.5/dist-packages (from gwvolman->-r /girder/plugins/wholetale/requirem                                                                                                                                              ents.txt (line 8)) (0.5.0)
	Requirement already satisfied: docker>=2.3.0 in /usr/local/lib/python3.5/dist-packages (from gwvolman->-r /girder/plugins/wholetale/requirem                                                                                                                                              ents.txt (line 8)) (4.1.0)
	Requirement already satisfied: markdown in /usr/local/lib/python3.5/dist-packages (from gwvolman->-r /girder/plugins/wholetale/requirements.                                                                                                                                              txt (line 8)) (3.2.1)
	Requirement already satisfied: pyxb>=1.2.6 in /usr/local/lib/python3.5/dist-packages (from dataone.common==3.2.0->-r /girder/plugins/wholeta                                                                                                                                              le/requirements.txt (line 9)) (1.2.6)
	Requirement already satisfied: pyasn1>=0.4.4 in /usr/local/lib/python3.5/dist-packages (from dataone.common==3.2.0->-r /girder/plugins/whole                                                                                                                                              tale/requirements.txt (line 9)) (0.4.8)
	Requirement already satisfied: iso8601>=0.1.12 in /usr/local/lib/python3.5/dist-packages (from dataone.common==3.2.0->-r /girder/plugins/who                                                                                                                                              letale/requirements.txt (line 9)) (0.1.12)
	Requirement already satisfied: PyJWT>=1.6.4 in /usr/local/lib/python3.5/dist-packages (from dataone.common==3.2.0->-r /girder/plugins/wholet                                                                                                                                              ale/requirements.txt (line 9)) (1.7.1)
	Requirement already satisfied: zipstream>=1.1.4 in /usr/local/lib/python3.5/dist-packages (from dataone.common==3.2.0->-r /girder/plugins/wh                                                                                                                                              oletale/requirements.txt (line 9)) (1.1.4)
	Requirement already satisfied: contextlib2>=0.5.5 in /usr/local/lib/python3.5/dist-packages (from dataone.common==3.2.0->-r /girder/plugins/                                                                                                                                              wholetale/requirements.txt (line 9)) (0.6.0.post1)
	Requirement already satisfied: cryptography>=2.3.1 in /usr/local/lib/python3.5/dist-packages (from dataone.common==3.2.0->-r /girder/plugins                                                                                                                                              /wholetale/requirements.txt (line 9)) (2.8)
	Requirement already satisfied: requests-toolbelt>=0.8.0 in /usr/local/lib/python3.5/dist-packages (from dataone.libclient==3.2.0->-r /girder                                                                                                                                              /plugins/wholetale/requirements.txt (line 10)) (0.9.1)
	Requirement already satisfied: decorator>=3.4.0 in /usr/local/lib/python3.5/dist-packages (from validators->-r /girder/plugins/wholetale/req                                                                                                                                              uirements.txt (line 12)) (4.4.1)
	Requirement already satisfied: beautifulsoup4 in /usr/local/lib/python3.5/dist-packages (from html2markdown->-r /girder/plugins/wholetale/re                                                                                                                                              quirements.txt (line 13)) (4.8.2)
	Requirement already satisfied: fs>2.0 in /usr/local/lib/python3.5/dist-packages (from fs.webdavfs->-r /girder/plugins/wholetale/requirements                                                                                                                                              .txt (line 14)) (2.4.11)
	Requirement already satisfied: webdavclient2 in /usr/local/lib/python3.5/dist-packages (from fs.webdavfs->-r /girder/plugins/wholetale/requi                                                                                                                                              rements.txt (line 14)) (0.1.1)
	Requirement already satisfied: vine<5.0.0a1,>=1.1.3 in /usr/local/lib/python3.5/dist-packages (from amqp<3.0,>=2.1.4->kombu==4.2.2post1->-r                                                                                                                                               /girder/plugins/wholetale/requirements.txt (line 3)) (1.3.0)
	Requirement already satisfied: diskcache in /usr/local/lib/python3.5/dist-packages (from girder-client->girderfs->-r /girder/plugins/wholeta                                                                                                                                              le/requirements.txt (line 7)) (4.1.0)
	Requirement already satisfied: click>=6.7 in /usr/local/lib/python3.5/dist-packages (from girder-client->girderfs->-r /girder/plugins/wholet                                                                                                                                              ale/requirements.txt (line 7)) (7.0)
	Requirement already satisfied: girder-worker-utils>=0.8.0 in /usr/local/lib/python3.5/dist-packages (from girder-worker->gwvolman->-r /girde                                                                                                                                              r/plugins/wholetale/requirements.txt (line 8)) (0.8.5)
	Requirement already satisfied: networkx<2 in /usr/local/lib/python3.5/dist-packages (from girder-worker->gwvolman->-r /girder/plugins/wholet                                                                                                                                              ale/requirements.txt (line 8)) (1.11)
	Requirement already satisfied: jsonpickle in /usr/local/lib/python3.5/dist-packages (from girder-worker->gwvolman->-r /girder/plugins/wholet                                                                                                                                              ale/requirements.txt (line 8)) (1.2)
	Requirement already satisfied: stevedore in /usr/local/lib/python3.5/dist-packages (from girder-worker->gwvolman->-r /girder/plugins/wholeta                                                                                                                                              le/requirements.txt (line 8)) (1.31.0)
	Requirement already satisfied: setuptools-scm in /usr/local/lib/python3.5/dist-packages (from girder-worker->gwvolman->-r /girder/plugins/wh                                                                                                                                              oletale/requirements.txt (line 8)) (3.4.3)
	Requirement already satisfied: pymongo>=3 in /usr/local/lib/python3.5/dist-packages (from girder-worker->gwvolman->-r /girder/plugins/wholet                                                                                                                                              ale/requirements.txt (line 8)) (3.10.1)
	Requirement already satisfied: websocket-client>=0.32.0 in /usr/local/lib/python3.5/dist-packages (from docker>=2.3.0->gwvolman->-r /girder/                                                                                                                                              plugins/wholetale/requirements.txt (line 8)) (0.57.0)
	Requirement already satisfied: setuptools>=36 in /usr/local/lib/python3.5/dist-packages (from markdown->gwvolman->-r /girder/plugins/wholeta                                                                                                                                              le/requirements.txt (line 8)) (45.1.0)
	Requirement already satisfied: cffi!=1.11.3,>=1.8 in /usr/local/lib/python3.5/dist-packages (from cryptography>=2.3.1->dataone.common==3.2.0                                                                                                                                              ->-r /girder/plugins/wholetale/requirements.txt (line 9)) (1.13.2)
	Requirement already satisfied: soupsieve>=1.2 in /usr/local/lib/python3.5/dist-packages (from beautifulsoup4->html2markdown->-r /girder/plug                                                                                                                                              ins/wholetale/requirements.txt (line 13)) (1.9.5)
	Requirement already satisfied: appdirs~=1.4.3 in /usr/local/lib/python3.5/dist-packages (from fs>2.0->fs.webdavfs->-r /girder/plugins/wholet                                                                                                                                              ale/requirements.txt (line 14)) (1.4.3)
	Requirement already satisfied: typing~=3.6; python_version < "3.6" in /usr/local/lib/python3.5/dist-packages (from fs>2.0->fs.webdavfs->-r /                                                                                                                                              girder/plugins/wholetale/requirements.txt (line 14)) (3.7.4.1)
	Requirement already satisfied: lxml in /usr/local/lib/python3.5/dist-packages (from webdavclient2->fs.webdavfs->-r /girder/plugins/wholetale                                                                                                                                              /requirements.txt (line 14)) (4.4.2)
	Requirement already satisfied: pbr!=2.1.0,>=2.0.0 in /usr/local/lib/python3.5/dist-packages (from stevedore->girder-worker->gwvolman->-r /gi                                                                                                                                              rder/plugins/wholetale/requirements.txt (line 8)) (5.4.4)
	Requirement already satisfied: pycparser in /usr/local/lib/python3.5/dist-packages (from cffi!=1.11.3,>=1.8->cryptography>=2.3.1->dataone.co                                                                                                                                              mmon==3.2.0->-r /girder/plugins/wholetale/requirements.txt (line 9)) (2.19)
	Installing wt_home_dir...
	Installing requirements.txt for wt_home_dir.
	Requirement already satisfied: WsgiDAV<3.0.0 in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/wt_home_dir/requirements.txt                                                                                                                                               (line 1)) (2.4.1)
	Requirement already satisfied: passlib>=1.7.1 in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/wt_home_dir/requirements.tx                                                                                                                                              t (line 2)) (1.7.2)
	Requirement already satisfied: defusedxml in /usr/local/lib/python3.5/dist-packages (from WsgiDAV<3.0.0->-r /girder/plugins/wt_home_dir/requ                                                                                                                                              irements.txt (line 1)) (0.6.0)
	Requirement already satisfied: PyYAML in /usr/local/lib/python3.5/dist-packages (from WsgiDAV<3.0.0->-r /girder/plugins/wt_home_dir/requirem                                                                                                                                              ents.txt (line 1)) (5.3)
	Requirement already satisfied: jsmin in /usr/local/lib/python3.5/dist-packages (from WsgiDAV<3.0.0->-r /girder/plugins/wt_home_dir/requireme                                                                                                                                              nts.txt (line 1)) (2.2.2)
	Installing globus_handler...
	Installing requirements.txt for globus_handler.
	Requirement already satisfied: globus-sdk in /usr/local/lib/python3.5/dist-packages (from -r /girder/plugins/globus_handler/requirements.txt                                                                                                                                               (line 1)) (1.8.0)
	Requirement already satisfied: requests<3.0.0,>=2.9.2 in /usr/local/lib/python3.5/dist-packages (from globus-sdk->-r /girder/plugins/globus_                                                                                                                                              handler/requirements.txt (line 1)) (2.20.1)
	Requirement already satisfied: six<2.0.0,>=1.10.0 in /usr/local/lib/python3.5/dist-packages (from globus-sdk->-r /girder/plugins/globus_hand                                                                                                                                              ler/requirements.txt (line 1)) (1.14.0)
	Requirement already satisfied: pyjwt[crypto]<2.0.0,>=1.5.3 in /usr/local/lib/python3.5/dist-packages (from globus-sdk->-r /girder/plugins/gl                                                                                                                                              obus_handler/requirements.txt (line 1)) (1.7.1)
	Requirement already satisfied: certifi>=2017.4.17 in /usr/local/lib/python3.5/dist-packages (from requests<3.0.0,>=2.9.2->globus-sdk->-r /gi                                                                                                                                              rder/plugins/globus_handler/requirements.txt (line 1)) (2019.11.28)
	Requirement already satisfied: idna<2.8,>=2.5 in /usr/local/lib/python3.5/dist-packages (from requests<3.0.0,>=2.9.2->globus-sdk->-r /girder                                                                                                                                              /plugins/globus_handler/requirements.txt (line 1)) (2.7)
	Requirement already satisfied: chardet<3.1.0,>=3.0.2 in /usr/local/lib/python3.5/dist-packages (from requests<3.0.0,>=2.9.2->globus-sdk->-r                                                                                                                                               /girder/plugins/globus_handler/requirements.txt (line 1)) (3.0.4)
	Requirement already satisfied: urllib3<1.25,>=1.21.1 in /usr/local/lib/python3.5/dist-packages (from requests<3.0.0,>=2.9.2->globus-sdk->-r                                                                                                                                               /girder/plugins/globus_handler/requirements.txt (line 1)) (1.24.3)
	Requirement already satisfied: cryptography>=1.4; extra == "crypto" in /usr/local/lib/python3.5/dist-packages (from pyjwt[crypto]<2.0.0,>=1.                                                                                                                                              5.3->globus-sdk->-r /girder/plugins/globus_handler/requirements.txt (line 1)) (2.8)
	Requirement already satisfied: cffi!=1.11.3,>=1.8 in /usr/local/lib/python3.5/dist-packages (from cryptography>=1.4; extra == "crypto"->pyjw                                                                                                                                              t[crypto]<2.0.0,>=1.5.3->globus-sdk->-r /girder/plugins/globus_handler/requirements.txt (line 1)) (1.13.2)
	Requirement already satisfied: pycparser in /usr/local/lib/python3.5/dist-packages (from cffi!=1.11.3,>=1.8->cryptography>=1.4; extra == "cr                                                                                                                                              ypto"->pyjwt[crypto]<2.0.0,>=1.5.3->globus-sdk->-r /girder/plugins/globus_handler/requirements.txt (line 1)) (2.19)
	docker exec -ti $(docker ps --filter=name=wt_girder -q) girder-install web --dev --plugins=oauth,gravatar,jobs,worker,wt_data_manager,wholet                                                                                                                                              ale,wt_home_dir,globus_handler
	npm WARN deprecated core-js@2.6.11: core-js@<3 is no longer maintained and not recommended for usage due to the number of issues. Please, up                                                                                                                                              grade your dependencies to the actual version of core-js@3.
	npm WARN deprecated eslint-config-girder@4.0.1: This package has been moved. It now lives at @girder/eslint-config.
	npm WARN deprecated phantomjs-prebuilt@2.1.16: this package is now deprecated
	npm WARN deprecated extract-text-webpack-plugin@2.1.2: Deprecated. Please use https://github.com/webpack-contrib/mini-css-extract-plugin
	npm WARN deprecated swagger-ui@2.2.10: No longer maintained, please upgrade to swagger-ui@3.
	npm WARN deprecated mkdirp@0.5.3: Legacy versions of mkdirp are no longer supported. Please update to mkdirp 1.x. (Note that the API surface                                                                                                                                               has changed to use Promises in 1.x.)
	npm WARN deprecated request@2.88.2: request has been deprecated, see https://github.com/request/request/issues/3142
	npm WARN deprecated mkdirp@0.5.1: Legacy versions of mkdirp are no longer supported. Please update to mkdirp 1.x. (Note that the API surface                                                                                                                                               has changed to use Promises in 1.x.)
	npm WARN deprecated circular-json@0.3.3: CircularJSON is in maintenance only, flatted is its successor.
	npm WARN deprecated browserslist@1.7.7: Browserslist 2 could fail on reading Browserslist >3.0 config used in other tools.
	npm WARN deprecated gulp-header@1.8.12: Removed event-stream from gulp-header

	> phantomjs-prebuilt@2.1.16 install /girder/node_modules/phantomjs-prebuilt
	> node install.js

	PhantomJS not found on PATH
	Downloading https://github.com/Medium/phantomjs/releases/download/v2.1.1/phantomjs-2.1.1-linux-x86_64.tar.bz2
	Saving to /tmp/phantomjs/phantomjs-2.1.1-linux-x86_64.tar.bz2
	Receiving...
	  [============================------------] 71%
	Received 22866K total.
	Extracting tar contents (via spawned process)
	Removing /girder/node_modules/phantomjs-prebuilt/lib/phantom
	Copying extracted folder /tmp/phantomjs/phantomjs-2.1.1-linux-x86_64.tar.bz2-extract-1584493906774/phantomjs-2.1.1-linux-x86_64 -> /girder/n                                                                                                                                              ode_modules/phantomjs-prebuilt/lib/phantom
	Writing location.js file
	Done. Phantomjs binary available at /girder/node_modules/phantomjs-prebuilt/lib/phantom/bin/phantomjs

	> core-js@2.6.11 postinstall /girder/node_modules/core-js
	> node -e "try{require('./postinstall')}catch(e){}"

	npm WARN notsup Unsupported engine for mkdirp@1.0.3: wanted: {"node":">=10"} (current: {"node":"8.17.0","npm":"6.13.4"})
	npm WARN notsup Not compatible with your version of node/npm: mkdirp@1.0.3
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@^1.2.7 (node_modules/chokidar/node_modules/fsevents):
	npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.11: wanted {"os":"darwin","arch":"any"} (current: {"os":                                                                                                                                              "linux","arch":"x64"})
	npm WARN ajv-keywords@3.4.1 requires a peer of ajv@^6.9.1 but none is installed. You must install peer dependencies yourself.
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: abbrev@1.1.1 (node_modules/fsevents/node_modules/abbrev):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/abbrev'                                                                                                                                               -> '/girder/node_modules/fsevents/node_modules/.abbrev.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: ansi-regex@2.1.1 (node_modules/fsevents/node_modules/ansi-regex):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/ansi-reg                                                                                                                                              ex' -> '/girder/node_modules/fsevents/node_modules/.ansi-regex.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: aproba@1.2.0 (node_modules/fsevents/node_modules/aproba):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/aproba'                                                                                                                                               -> '/girder/node_modules/fsevents/node_modules/.aproba.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: balanced-match@1.0.0 (node_modules/fsevents/node_modules/balanced-match):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/balanced                                                                                                                                              -match' -> '/girder/node_modules/fsevents/node_modules/.balanced-match.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: chownr@1.1.3 (node_modules/fsevents/node_modules/chownr):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/chownr'                                                                                                                                               -> '/girder/node_modules/fsevents/node_modules/.chownr.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: code-point-at@1.1.0 (node_modules/fsevents/node_modules/code-point-at):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/code-poi                                                                                                                                              nt-at' -> '/girder/node_modules/fsevents/node_modules/.code-point-at.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: concat-map@0.0.1 (node_modules/fsevents/node_modules/concat-map):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/concat-m                                                                                                                                              ap' -> '/girder/node_modules/fsevents/node_modules/.concat-map.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: console-control-strings@1.1.0 (node_modules/fsevents/node_modules/console-control-strings):                                                                                                                                               npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/console-                                                                                                                                              control-strings' -> '/girder/node_modules/fsevents/node_modules/.console-control-strings.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: core-util-is@1.0.2 (node_modules/fsevents/node_modules/core-util-is):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/core-uti                                                                                                                                              l-is' -> '/girder/node_modules/fsevents/node_modules/.core-util-is.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: deep-extend@0.6.0 (node_modules/fsevents/node_modules/deep-extend):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/deep-ext                                                                                                                                              end' -> '/girder/node_modules/fsevents/node_modules/.deep-extend.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: delegates@1.0.0 (node_modules/fsevents/node_modules/delegates):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/delegate                                                                                                                                              s' -> '/girder/node_modules/fsevents/node_modules/.delegates.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: detect-libc@1.0.3 (node_modules/fsevents/node_modules/detect-libc):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/detect-l                                                                                                                                              ibc' -> '/girder/node_modules/fsevents/node_modules/.detect-libc.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fs.realpath@1.0.0 (node_modules/fsevents/node_modules/fs.realpath):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/fs.realp                                                                                                                                              ath' -> '/girder/node_modules/fsevents/node_modules/.fs.realpath.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: has-unicode@2.0.1 (node_modules/fsevents/node_modules/has-unicode):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/has-unic                                                                                                                                              ode' -> '/girder/node_modules/fsevents/node_modules/.has-unicode.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: inherits@2.0.4 (node_modules/fsevents/node_modules/inherits):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/inherits                                                                                                                                              ' -> '/girder/node_modules/fsevents/node_modules/.inherits.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: ini@1.3.5 (node_modules/fsevents/node_modules/ini):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/ini' ->                                                                                                                                               '/girder/node_modules/fsevents/node_modules/.ini.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: isarray@1.0.0 (node_modules/fsevents/node_modules/isarray):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/isarray'                                                                                                                                               -> '/girder/node_modules/fsevents/node_modules/.isarray.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: minimist@0.0.8 (node_modules/fsevents/node_modules/minimist):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/minimist                                                                                                                                              ' -> '/girder/node_modules/fsevents/node_modules/.minimist.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: ms@2.1.2 (node_modules/fsevents/node_modules/ms):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/ms' -> '                                                                                                                                              /girder/node_modules/fsevents/node_modules/.ms.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: npm-normalize-package-bin@1.0.1 (node_modules/fsevents/node_modules/npm-normalize-package-bi                                                                                                                                              n):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/npm-norm                                                                                                                                              alize-package-bin' -> '/girder/node_modules/fsevents/node_modules/.npm-normalize-package-bin.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: number-is-nan@1.0.1 (node_modules/fsevents/node_modules/number-is-nan):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/number-i                                                                                                                                              s-nan' -> '/girder/node_modules/fsevents/node_modules/.number-is-nan.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: object-assign@4.1.1 (node_modules/fsevents/node_modules/object-assign):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/object-a                                                                                                                                              ssign' -> '/girder/node_modules/fsevents/node_modules/.object-assign.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: os-homedir@1.0.2 (node_modules/fsevents/node_modules/os-homedir):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/os-homed                                                                                                                                              ir' -> '/girder/node_modules/fsevents/node_modules/.os-homedir.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: os-tmpdir@1.0.2 (node_modules/fsevents/node_modules/os-tmpdir):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/os-tmpdi                                                                                                                                              r' -> '/girder/node_modules/fsevents/node_modules/.os-tmpdir.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: path-is-absolute@1.0.1 (node_modules/fsevents/node_modules/path-is-absolute):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/path-is-                                                                                                                                              absolute' -> '/girder/node_modules/fsevents/node_modules/.path-is-absolute.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: process-nextick-args@2.0.1 (node_modules/fsevents/node_modules/process-nextick-args):                                                                                                                                                     npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/process-                                                                                                                                              nextick-args' -> '/girder/node_modules/fsevents/node_modules/.process-nextick-args.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: minimist@1.2.0 (node_modules/fsevents/node_modules/rc/node_modules/minimist):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/rc/node_                                                                                                                                              modules/minimist' -> '/girder/node_modules/fsevents/node_modules/rc/node_modules/.minimist.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: safe-buffer@5.1.2 (node_modules/fsevents/node_modules/safe-buffer):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/safe-buf                                                                                                                                              fer' -> '/girder/node_modules/fsevents/node_modules/.safe-buffer.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: safer-buffer@2.1.2 (node_modules/fsevents/node_modules/safer-buffer):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/safer-bu                                                                                                                                              ffer' -> '/girder/node_modules/fsevents/node_modules/.safer-buffer.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: sax@1.2.4 (node_modules/fsevents/node_modules/sax):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/sax' ->                                                                                                                                               '/girder/node_modules/fsevents/node_modules/.sax.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: semver@5.7.1 (node_modules/fsevents/node_modules/semver):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/semver'                                                                                                                                               -> '/girder/node_modules/fsevents/node_modules/.semver.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: set-blocking@2.0.0 (node_modules/fsevents/node_modules/set-blocking):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/set-bloc                                                                                                                                              king' -> '/girder/node_modules/fsevents/node_modules/.set-blocking.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: signal-exit@3.0.2 (node_modules/fsevents/node_modules/signal-exit):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/signal-e                                                                                                                                              xit' -> '/girder/node_modules/fsevents/node_modules/.signal-exit.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: strip-json-comments@2.0.1 (node_modules/fsevents/node_modules/strip-json-comments):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/strip-js                                                                                                                                              on-comments' -> '/girder/node_modules/fsevents/node_modules/.strip-json-comments.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: util-deprecate@1.0.2 (node_modules/fsevents/node_modules/util-deprecate):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/util-dep                                                                                                                                              recate' -> '/girder/node_modules/fsevents/node_modules/.util-deprecate.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: wrappy@1.0.2 (node_modules/fsevents/node_modules/wrappy):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/wrappy'                                                                                                                                               -> '/girder/node_modules/fsevents/node_modules/.wrappy.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: yallist@3.1.1 (node_modules/fsevents/node_modules/yallist):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/fsevents/node_modules/yallist'                                                                                                                                               -> '/girder/node_modules/fsevents/node_modules/.yallist.DELETE'

	added 1528 packages from 837 contributors and audited 12502 packages in 47s

	18 packages are looking for funding
	  run `npm fund` for details

	found 192 vulnerabilities (104 low, 30 moderate, 57 high, 1 critical)
	  run `npm audit fix` to fix them, or `npm audit` for details

	> @girder/app@2.5.0 build /girder
	> NODE_PATH=$PWD/node_modules grunt "--no-progress=false" "--env=dev" "--plugins=gravatar,jobs,oauth,globus_handler,worker,wholetale,wt_data                                                                                                                                              _manager,wt_home_dir" "--configure-plugins="

	Configuring plugin gravatar (plugin.yml, build=ON)
	Configuring plugin jobs (plugin.yml, build=ON)
	Configuring plugin oauth (plugin.json, build=ON)
	Configuring plugin globus_handler (plugin.yml, build=ON)
	Configuring plugin worker (plugin.json, build=ON)
	Configuring plugin wholetale (plugin.yml, build=ON)
	Configuring plugin wt_data_manager (plugin.yml, build=ON)
	Configuring plugin wt_home_dir (plugin.yml, build=ON)

	Running "npm-install-plugins" task
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@^1.2.7 (node_modules/chokidar/node_modules/fsevents):
	npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.11: wanted {"os":"darwin","arch":"any"} (current: {"os":                                                                                                                                              "linux","arch":"x64"})
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@^1.0.0 (node_modules/stylint/node_modules/chokidar/node_modules/fsevents):
	npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.11: wanted {"os":"darwin","arch":"any"} (current: {"os":                                                                                                                                              "linux","arch":"x64"})
	npm WARN ajv-keywords@3.4.1 requires a peer of ajv@^6.9.1 but none is installed. You must install peer dependencies yourself.
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: abbrev@1.1.1 (node_modules/chokidar/node_modules/fsevents/node_modules/abbrev):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/abbrev' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.abbrev.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: ansi-regex@2.1.1 (node_modules/chokidar/node_modules/fsevents/node_modules/ansi-regex):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/ansi-regex' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.ansi-regex.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: aproba@1.2.0 (node_modules/chokidar/node_modules/fsevents/node_modules/aproba):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/aproba' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.aproba.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: balanced-match@1.0.0 (node_modules/chokidar/node_modules/fsevents/node_modules/balanced-matc                                                                                                                                              h):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/balanced-match' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.balanced-match.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: chownr@1.1.3 (node_modules/chokidar/node_modules/fsevents/node_modules/chownr):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/chownr' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.chownr.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: code-point-at@1.1.0 (node_modules/chokidar/node_modules/fsevents/node_modules/code-point-at)                                                                                                                                              :
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/code-point-at' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.code-point-at.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: concat-map@0.0.1 (node_modules/chokidar/node_modules/fsevents/node_modules/concat-map):                                                                                                                                                   npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/concat-map' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.concat-map.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: console-control-strings@1.1.0 (node_modules/chokidar/node_modules/fsevents/node_modules/cons                                                                                                                                              ole-control-strings):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/console-control-strings' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.console-control-strings.DELETE'                                                                                                                                              npm WARN optional SKIPPING OPTIONAL DEPENDENCY: core-util-is@1.0.2 (node_modules/chokidar/node_modules/fsevents/node_modules/core-util-is):                                                                                                                                               npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/core-util-is' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.core-util-is.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: deep-extend@0.6.0 (node_modules/chokidar/node_modules/fsevents/node_modules/deep-extend):                                                                                                                                                 npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/deep-extend' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.deep-extend.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: delegates@1.0.0 (node_modules/chokidar/node_modules/fsevents/node_modules/delegates):                                                                                                                                                     npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/delegates' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.delegates.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: detect-libc@1.0.3 (node_modules/chokidar/node_modules/fsevents/node_modules/detect-libc):                                                                                                                                                 npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/detect-libc' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.detect-libc.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fs.realpath@1.0.0 (node_modules/chokidar/node_modules/fsevents/node_modules/fs.realpath):                                                                                                                                                 npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/fs.realpath' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.fs.realpath.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: has-unicode@2.0.1 (node_modules/chokidar/node_modules/fsevents/node_modules/has-unicode):                                                                                                                                                 npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/has-unicode' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.has-unicode.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: inherits@2.0.4 (node_modules/chokidar/node_modules/fsevents/node_modules/inherits):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/inherits' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.inherits.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: ini@1.3.5 (node_modules/chokidar/node_modules/fsevents/node_modules/ini):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/ini' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.ini.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: isarray@1.0.0 (node_modules/chokidar/node_modules/fsevents/node_modules/isarray):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/isarray' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.isarray.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: minimist@0.0.8 (node_modules/chokidar/node_modules/fsevents/node_modules/minimist):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/minimist' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.minimist.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: ms@2.1.2 (node_modules/chokidar/node_modules/fsevents/node_modules/ms):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/ms' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.ms.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: npm-normalize-package-bin@1.0.1 (node_modules/chokidar/node_modules/fsevents/node_modules/np                                                                                                                                              m-normalize-package-bin):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/npm-normalize-package-bin' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.npm-normalize-package-bin.DEL                                                                                                                                              ETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: number-is-nan@1.0.1 (node_modules/chokidar/node_modules/fsevents/node_modules/number-is-nan)                                                                                                                                              :
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/number-is-nan' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.number-is-nan.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: object-assign@4.1.1 (node_modules/chokidar/node_modules/fsevents/node_modules/object-assign)                                                                                                                                              :
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/object-assign' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.object-assign.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: os-homedir@1.0.2 (node_modules/chokidar/node_modules/fsevents/node_modules/os-homedir):                                                                                                                                                   npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/os-homedir' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.os-homedir.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: os-tmpdir@1.0.2 (node_modules/chokidar/node_modules/fsevents/node_modules/os-tmpdir):                                                                                                                                                     npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/os-tmpdir' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.os-tmpdir.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: path-is-absolute@1.0.1 (node_modules/chokidar/node_modules/fsevents/node_modules/path-is-abs                                                                                                                                              olute):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/path-is-absolute' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.path-is-absolute.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: process-nextick-args@2.0.1 (node_modules/chokidar/node_modules/fsevents/node_modules/process                                                                                                                                              -nextick-args):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/process-nextick-args' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.process-nextick-args.DELETE'                                                                                                                                                    npm WARN optional SKIPPING OPTIONAL DEPENDENCY: minimist@1.2.0 (node_modules/chokidar/node_modules/fsevents/node_modules/rc/node_modules/min                                                                                                                                              imist):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/rc/node_modules/minimist' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/rc/node_modules/.minimist.DELET                                                                                                                                              E'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: safe-buffer@5.1.2 (node_modules/chokidar/node_modules/fsevents/node_modules/safe-buffer):                                                                                                                                                 npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/safe-buffer' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.safe-buffer.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: safer-buffer@2.1.2 (node_modules/chokidar/node_modules/fsevents/node_modules/safer-buffer):                                                                                                                                               npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/safer-buffer' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.safer-buffer.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: sax@1.2.4 (node_modules/chokidar/node_modules/fsevents/node_modules/sax):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/sax' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.sax.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: semver@5.7.1 (node_modules/chokidar/node_modules/fsevents/node_modules/semver):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/semver' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.semver.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: set-blocking@2.0.0 (node_modules/chokidar/node_modules/fsevents/node_modules/set-blocking):                                                                                                                                               npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/set-blocking' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.set-blocking.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: signal-exit@3.0.2 (node_modules/chokidar/node_modules/fsevents/node_modules/signal-exit):                                                                                                                                                 npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/signal-exit' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.signal-exit.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: strip-json-comments@2.0.1 (node_modules/chokidar/node_modules/fsevents/node_modules/strip-js                                                                                                                                              on-comments):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/strip-json-comments' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.strip-json-comments.DELETE'                                                                                                                                                      npm WARN optional SKIPPING OPTIONAL DEPENDENCY: util-deprecate@1.0.2 (node_modules/chokidar/node_modules/fsevents/node_modules/util-deprecat                                                                                                                                              e):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/util-deprecate' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.util-deprecate.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: wrappy@1.0.2 (node_modules/chokidar/node_modules/fsevents/node_modules/wrappy):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/wrappy' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.wrappy.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: yallist@3.1.1 (node_modules/chokidar/node_modules/fsevents/node_modules/yallist):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/chokidar/node_modules/fsevents                                                                                                                                              /node_modules/yallist' -> '/girder/node_modules/chokidar/node_modules/fsevents/node_modules/.yallist.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: abbrev@1.1.1 (node_modules/stylint/node_modules/fsevents/node_modules/abbrev):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/abbrev' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.abbrev.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: ansi-regex@2.1.1 (node_modules/stylint/node_modules/fsevents/node_modules/ansi-regex):                                                                                                                                                    npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/ansi-regex' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.ansi-regex.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: aproba@1.2.0 (node_modules/stylint/node_modules/fsevents/node_modules/aproba):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/aproba' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.aproba.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: balanced-match@1.0.0 (node_modules/stylint/node_modules/fsevents/node_modules/balanced-match                                                                                                                                              ):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/balanced-match' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.balanced-match.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: chownr@1.1.3 (node_modules/stylint/node_modules/fsevents/node_modules/chownr):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/chownr' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.chownr.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: code-point-at@1.1.0 (node_modules/stylint/node_modules/fsevents/node_modules/code-point-at):                                                                                                                                              npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/code-point-at' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.code-point-at.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: concat-map@0.0.1 (node_modules/stylint/node_modules/fsevents/node_modules/concat-map):                                                                                                                                                    npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/concat-map' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.concat-map.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: console-control-strings@1.1.0 (node_modules/stylint/node_modules/fsevents/node_modules/conso                                                                                                                                              le-control-strings):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/console-control-strings' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.console-control-strings.DELETE'                                                                                                                                                npm WARN optional SKIPPING OPTIONAL DEPENDENCY: core-util-is@1.0.2 (node_modules/stylint/node_modules/fsevents/node_modules/core-util-is):                                                                                                                                                npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/core-util-is' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.core-util-is.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: deep-extend@0.6.0 (node_modules/stylint/node_modules/fsevents/node_modules/deep-extend):                                                                                                                                                  npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/deep-extend' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.deep-extend.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: delegates@1.0.0 (node_modules/stylint/node_modules/fsevents/node_modules/delegates):                                                                                                                                                      npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/delegates' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.delegates.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: detect-libc@1.0.3 (node_modules/stylint/node_modules/fsevents/node_modules/detect-libc):                                                                                                                                                  npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/detect-libc' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.detect-libc.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fs.realpath@1.0.0 (node_modules/stylint/node_modules/fsevents/node_modules/fs.realpath):                                                                                                                                                  npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/fs.realpath' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.fs.realpath.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: has-unicode@2.0.1 (node_modules/stylint/node_modules/fsevents/node_modules/has-unicode):                                                                                                                                                  npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/has-unicode' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.has-unicode.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: inherits@2.0.4 (node_modules/stylint/node_modules/fsevents/node_modules/inherits):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/inherits' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.inherits.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: ini@1.3.5 (node_modules/stylint/node_modules/fsevents/node_modules/ini):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/ini' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.ini.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: isarray@1.0.0 (node_modules/stylint/node_modules/fsevents/node_modules/isarray):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/isarray' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.isarray.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: minimist@0.0.8 (node_modules/stylint/node_modules/fsevents/node_modules/minimist):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/minimist' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.minimist.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: ms@2.1.2 (node_modules/stylint/node_modules/fsevents/node_modules/ms):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/ms' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.ms.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: npm-normalize-package-bin@1.0.1 (node_modules/stylint/node_modules/fsevents/node_modules/npm                                                                                                                                              -normalize-package-bin):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/npm-normalize-package-bin' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.npm-normalize-package-bin.DELET                                                                                                                                              E'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: number-is-nan@1.0.1 (node_modules/stylint/node_modules/fsevents/node_modules/number-is-nan):                                                                                                                                              npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/number-is-nan' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.number-is-nan.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: object-assign@4.1.1 (node_modules/stylint/node_modules/fsevents/node_modules/object-assign):                                                                                                                                              npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/object-assign' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.object-assign.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: os-homedir@1.0.2 (node_modules/stylint/node_modules/fsevents/node_modules/os-homedir):                                                                                                                                                    npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/os-homedir' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.os-homedir.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: os-tmpdir@1.0.2 (node_modules/stylint/node_modules/fsevents/node_modules/os-tmpdir):                                                                                                                                                      npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/os-tmpdir' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.os-tmpdir.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: path-is-absolute@1.0.1 (node_modules/stylint/node_modules/fsevents/node_modules/path-is-abso                                                                                                                                              lute):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/path-is-absolute' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.path-is-absolute.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: process-nextick-args@2.0.1 (node_modules/stylint/node_modules/fsevents/node_modules/process-                                                                                                                                              nextick-args):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/process-nextick-args' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.process-nextick-args.DELETE'                                                                                                                                                      npm WARN optional SKIPPING OPTIONAL DEPENDENCY: minimist@1.2.0 (node_modules/stylint/node_modules/fsevents/node_modules/rc/node_modules/mini                                                                                                                                              mist):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/rc/node_modules/minimist' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/rc/node_modules/.minimist.DELETE'                                                                                                                                              npm WARN optional SKIPPING OPTIONAL DEPENDENCY: safe-buffer@5.1.2 (node_modules/stylint/node_modules/fsevents/node_modules/safe-buffer):                                                                                                                                                  npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/safe-buffer' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.safe-buffer.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: safer-buffer@2.1.2 (node_modules/stylint/node_modules/fsevents/node_modules/safer-buffer):                                                                                                                                                npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/safer-buffer' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.safer-buffer.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: sax@1.2.4 (node_modules/stylint/node_modules/fsevents/node_modules/sax):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/sax' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.sax.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: semver@5.7.1 (node_modules/stylint/node_modules/fsevents/node_modules/semver):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/semver' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.semver.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: set-blocking@2.0.0 (node_modules/stylint/node_modules/fsevents/node_modules/set-blocking):                                                                                                                                                npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/set-blocking' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.set-blocking.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: signal-exit@3.0.2 (node_modules/stylint/node_modules/fsevents/node_modules/signal-exit):                                                                                                                                                  npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/signal-exit' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.signal-exit.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: strip-json-comments@2.0.1 (node_modules/stylint/node_modules/fsevents/node_modules/strip-jso                                                                                                                                              n-comments):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/strip-json-comments' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.strip-json-comments.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: util-deprecate@1.0.2 (node_modules/stylint/node_modules/fsevents/node_modules/util-deprecate                                                                                                                                              ):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/util-deprecate' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.util-deprecate.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: wrappy@1.0.2 (node_modules/stylint/node_modules/fsevents/node_modules/wrappy):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/wrappy' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.wrappy.DELETE'
	npm WARN optional SKIPPING OPTIONAL DEPENDENCY: yallist@3.1.1 (node_modules/stylint/node_modules/fsevents/node_modules/yallist):
	npm WARN enoent SKIPPING OPTIONAL DEPENDENCY: ENOENT: no such file or directory, rename '/girder/node_modules/stylint/node_modules/fsevents/                                                                                                                                              node_modules/yallist' -> '/girder/node_modules/stylint/node_modules/fsevents/node_modules/.yallist.DELETE'

	+ vega-lib@3.3.1
	added 51 packages from 12 contributors, removed 2 packages and audited 12502 packages in 12.888s

	18 packages are looking for funding
	  run `npm fund` for details

	found 192 vulnerabilities (104 low, 30 moderate, 57 high, 1 critical)
	  run `npm audit fix` to fix them, or `npm audit` for details

	Running "shell:fontello" (shell) task
	  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
	                                 Dload  Upload   Total   Spent    Left  Speed
	100  540k  100  540k    0     0   404k      0  0:00:01  0:00:01 --:--:--  404k

	Running "unzip:fontello" (unzip) task
	Created "clients/web/static/built/fontello/" directory

	Running "local-config" task

	Running "plugin:gravatar" (plugin) task

	Running "copy:plugin-gravatar" (copy) task


	Running "plugin:jobs" (plugin) task

	Running "copy:plugin-jobs" (copy) task


	Running "plugin:oauth" (plugin) task

	Running "copy:plugin-oauth" (copy) task


	Running "plugin:globus_handler" (plugin) task

	Running "copy:plugin-globus_handler" (copy) task


	Running "plugin:worker" (plugin) task

	Running "copy:plugin-worker" (copy) task


	Running "plugin:wholetale" (plugin) task

	Running "copy:plugin-wholetale" (copy) task
	Created 2 directories, copied 10 files

	Running "plugin:wt_data_manager" (plugin) task

	Running "copy:plugin-wt_data_manager" (copy) task


	Running "plugin:wt_home_dir" (plugin) task

	Running "copy:plugin-wt_home_dir" (copy) task


	Running "plugin:gravatar" (plugin) task

	Running "copy:plugin-gravatar" (copy) task


	Running "npm-install:gravatar" (npm-install) task

	Running "plugin:jobs" (plugin) task

	Running "copy:plugin-jobs" (copy) task


	Running "npm-install:jobs" (npm-install) task

	Running "plugin:oauth" (plugin) task

	Running "copy:plugin-oauth" (copy) task


	Running "npm-install:oauth" (npm-install) task

	Running "plugin:globus_handler" (plugin) task

	Running "copy:plugin-globus_handler" (copy) task


	Running "npm-install:globus_handler" (npm-install) task

	Running "plugin:worker" (plugin) task

	Running "copy:plugin-worker" (copy) task


	Running "npm-install:worker" (npm-install) task

	Running "plugin:wholetale" (plugin) task

	Running "copy:plugin-wholetale" (copy) task
	Created 2 directories, copied 10 files

	Running "npm-install:wholetale" (npm-install) task

	Running "plugin:wt_data_manager" (plugin) task

	Running "copy:plugin-wt_data_manager" (copy) task


	Running "npm-install:wt_data_manager" (npm-install) task

	Running "plugin:wt_home_dir" (plugin) task

	Running "copy:plugin-wt_home_dir" (copy) task


	Running "npm-install:wt_home_dir" (npm-install) task

	Running "copy:swagger" (copy) task
	Created 3 directories, copied 32 files

	Running "stylus:swagger" (stylus) task
	>> 1 file created.

	Running "uglify:test" (uglify) task
	>> 1 file created 387.46 kB → 152.48 kB

	Running "copy:test" (copy) task
	Copied 1 file

	Running "pug:test" (pug) task
	>> 1 file created.

	Running "gitinfo" task

	Running "file-creator:python-version" (file-creator) task
	Writing file [girder/girder-version.json]
	>> 1 file(s) written.

	Running "file-creator:javascript-version" (file-creator) task
	Writing file [clients/web/src/version.js]
	>> 1 file(s) written.

	Running "webpack:core_lib" (webpack) task
	Version: webpack 2.7.0
	                                             Asset      Size  Chunks                    Chunk Names
	                            font/OpenSans-Bold.eot     16 kB          [emitted]         fonts
	              assets/jsoneditor-icons-8e7baace.svg     36 kB          [emitted]
	 assets/glyphicons-halflings-regular-fa277232.woff   23.4 kB          [emitted]
	assets/glyphicons-halflings-regular-448c34a5.woff2     18 kB          [emitted]
	  assets/glyphicons-halflings-regular-e18bbf61.ttf   45.4 kB          [emitted]
	  assets/glyphicons-halflings-regular-89889688.svg    109 kB          [emitted]
	                                   googlefonts.css      2 kB          [emitted]         fonts
	                          font/OpenSans-Italic.eot   14.8 kB          [emitted]         fonts
	                         font/OpenSans-Italic.woff   17.4 kB          [emitted]         fonts
	                        font/OpenSans-Italic.woff2   13.8 kB          [emitted]         fonts
	                         font/OpenSans-Regular.eot   15.4 kB          [emitted]         fonts
	                          font/OpenSans-Italic.ttf   25.7 kB          [emitted]         fonts
	                       font/OpenSans-Regular.woff2   14.4 kB          [emitted]         fonts
	                        font/OpenSans-Regular.woff   18.1 kB          [emitted]         fonts
	                         font/OpenSans-Regular.ttf   27.1 kB          [emitted]         fonts
	                         font/OpenSans-Regular.svg   56.3 kB          [emitted]         fonts
	  assets/glyphicons-halflings-regular-f4769f9b.eot   20.1 kB          [emitted]
	                           font/OpenSans-Bold.woff   18.9 kB          [emitted]         fonts
	                          font/OpenSans-Bold.woff2   15.1 kB          [emitted]         fonts
	                            font/OpenSans-Bold.ttf   28.8 kB          [emitted]         fonts
	                          font/OpenSans-Italic.svg   59.4 kB          [emitted]         fonts
	                      font/OpenSans-BoldItalic.eot   14.8 kB          [emitted]         fonts
	                     font/OpenSans-BoldItalic.woff   17.5 kB          [emitted]         fonts
	                    font/OpenSans-BoldItalic.woff2   13.9 kB          [emitted]         fonts
	                      font/OpenSans-BoldItalic.ttf   25.9 kB          [emitted]         fonts
	                            font/OpenSans-Bold.svg   55.7 kB          [emitted]         fonts
	                      font/OpenSans-BoldItalic.svg   58.5 kB          [emitted]         fonts
	                   assets/Girder_Mark-6719b633.png   7.59 kB          [emitted]
	                                 girder_lib.min.js   7.58 MB       0  [emitted]  [big]  girder_lib
	                                girder_lib.min.css    246 kB       0  [emitted]         girder_lib
	                             girder_lib.min.js.map   6.26 MB       0  [emitted]         girder_lib
	                            girder_lib.min.css.map  95 bytes       0  [emitted]         girder_lib

	Running "webpack:core_app" (webpack) task
	Version: webpack 2.7.0
	                Asset     Size  Chunks             Chunk Names
	    girder_app.min.js  8.53 kB       0  [emitted]  girder_app
	girder_app.min.js.map  5.59 kB       0  [emitted]  girder_app

	Running "webpack:plugin_gravatar" (webpack) task
	Version: webpack 2.7.0
	            Asset     Size  Chunks             Chunk Names
	    plugin.min.js  30.9 kB       0  [emitted]  plugins/gravatar/plugin
	plugin.min.js.map  17.9 kB       0  [emitted]  plugins/gravatar/plugin

	Running "webpack:plugin_jobs" (webpack) task
	Version: webpack 2.7.0
	             Asset      Size  Chunks                    Chunk Names
	     plugin.min.js   2.65 MB       0  [emitted]  [big]  plugins/jobs/plugin
	    plugin.min.css   2.34 kB       0  [emitted]         plugins/jobs/plugin
	 plugin.min.js.map   2.19 MB       0  [emitted]         plugins/jobs/plugin
	plugin.min.css.map  91 bytes       0  [emitted]         plugins/jobs/plugin

	WARNING in ./~/vega-statistics/src/quantiles.js
	11:20-34 "export 'quantileSorted' was not found in 'd3-array'
	  at HarmonyImportSpecifierDependency._getErrors (/girder/node_modules/webpack/lib/dependencies/HarmonyImportSpecifierDependency.js:61:15)                                                                                                                                                  at HarmonyImportSpecifierDependency.getWarnings (/girder/node_modules/webpack/lib/dependencies/HarmonyImportSpecifierDependency.js:35:15)                                                                                                                                                 at Compilation.reportDependencyErrorsAndWarnings (/girder/node_modules/webpack/lib/Compilation.js:672:24)
	  at Compilation.finish (/girder/node_modules/webpack/lib/Compilation.js:535:9)
	  at /girder/node_modules/webpack/lib/Compiler.js:491:16
	  at /girder/node_modules/tapable/lib/Tapable.js:289:11
	  at _addModuleChain (/girder/node_modules/webpack/lib/Compilation.js:481:11)
	  at processModuleDependencies.err (/girder/node_modules/webpack/lib/Compilation.js:452:13)
	  at _combinedTickCallback (internal/process/next_tick.js:132:7)
	  at process._tickCallback (internal/process/next_tick.js:181:9)


	Running "webpack:plugin_oauth" (webpack) task
	Version: webpack 2.7.0
	             Asset      Size  Chunks             Chunk Names
	     plugin.min.js   99.3 kB       0  [emitted]  plugins/oauth/plugin
	    plugin.min.css    3.5 kB       0  [emitted]  plugins/oauth/plugin
	 plugin.min.js.map   79.8 kB       0  [emitted]  plugins/oauth/plugin
	plugin.min.css.map  91 bytes       0  [emitted]  plugins/oauth/plugin

	Running "webpack:plugin_globus_handler" (webpack) task
	Version: webpack 2.7.0
	             Asset      Size  Chunks             Chunk Names
	     plugin.min.js   35.2 kB       0  [emitted]  plugins/globus_handler/plugin
	    plugin.min.css  42 bytes       0  [emitted]  plugins/globus_handler/plugin
	 plugin.min.js.map   21.8 kB       0  [emitted]  plugins/globus_handler/plugin
	plugin.min.css.map  91 bytes       0  [emitted]  plugins/globus_handler/plugin

	Running "webpack:plugin_worker" (webpack) task
	Version: webpack 2.7.0
	             Asset      Size  Chunks             Chunk Names
	     plugin.min.js    112 kB       0  [emitted]  plugins/worker/plugin
	    plugin.min.css   3.56 kB       0  [emitted]  plugins/worker/plugin
	 plugin.min.js.map    101 kB       0  [emitted]  plugins/worker/plugin
	plugin.min.css.map  91 bytes       0  [emitted]  plugins/worker/plugin

	Running "webpack:plugin_wholetale" (webpack) task
	Version: webpack 2.7.0
	             Asset      Size  Chunks                    Chunk Names
	     plugin.min.js    312 kB       0  [emitted]  [big]  plugins/wholetale/plugin
	    plugin.min.css   3.81 kB       0  [emitted]         plugins/wholetale/plugin
	 plugin.min.js.map    213 kB       0  [emitted]         plugins/wholetale/plugin
	plugin.min.css.map  91 bytes       0  [emitted]         plugins/wholetale/plugin

	Running "webpack:plugin_wt_data_manager" (webpack) task
	Version: webpack 2.7.0
	             Asset      Size  Chunks             Chunk Names
	     plugin.min.js   38.8 kB       0  [emitted]  plugins/wt_data_manager/plugin
	    plugin.min.css  42 bytes       0  [emitted]  plugins/wt_data_manager/plugin
	 plugin.min.js.map   27.1 kB       0  [emitted]  plugins/wt_data_manager/plugin
	plugin.min.css.map  91 bytes       0  [emitted]  plugins/wt_data_manager/plugin

	Running "webpack:plugin_wt_home_dir" (webpack) task
	Version: webpack 2.7.0
	             Asset      Size  Chunks             Chunk Names
	     plugin.min.js   57.4 kB       0  [emitted]  plugins/wt_home_dir/plugin
	    plugin.min.css  42 bytes       0  [emitted]  plugins/wt_home_dir/plugin
	 plugin.min.js.map   38.8 kB       0  [emitted]  plugins/wt_home_dir/plugin
	plugin.min.css.map  91 bytes       0  [emitted]  plugins/wt_home_dir/plugin

	Done.


	   ╭────────────────────────────────────────────────────────────────╮
	   │                                                                │
	   │      New minor version of npm available! 6.13.4 → 6.14.2       │
	   │   Changelog: https://github.com/npm/cli/releases/tag/v6.14.2   │
	   │                  Run npm i -g npm to update!                   │
	   │                                                                │
	   ╰────────────────────────────────────────────────────────────────╯
	
	<<< OUTPUT CONTINUED BELOW... >>>
	```
- Saw error messages during invocation of `setup_girder.py` by `dev` target:
	```
	<<< ...OUTPUT CONTINUED FROM ABOVE >>>
	
	./setup_girder.py
	Waiting for Girder to start
	Traceback (most recent call last):
	  File "/usr/lib/python3/dist-packages/urllib3/connection.py", line 141, in _new_conn
	    (self.host, self.port), self.timeout, **extra_kw)
	  File "/usr/lib/python3/dist-packages/urllib3/util/connection.py", line 83, in create_connection
	    raise err
	  File "/usr/lib/python3/dist-packages/urllib3/util/connection.py", line 73, in create_connection
	    sock.connect(sa)
	ConnectionRefusedError: [Errno 111] Connection refused

	During handling of the above exception, another exception occurred:

	Traceback (most recent call last):
	  File "/usr/lib/python3/dist-packages/urllib3/connectionpool.py", line 601, in urlopen
	    chunked=chunked)
	  File "/usr/lib/python3/dist-packages/urllib3/connectionpool.py", line 346, in _make_request
	    self._validate_conn(conn)
	  File "/usr/lib/python3/dist-packages/urllib3/connectionpool.py", line 852, in _validate_conn
	    conn.connect()
	  File "/usr/lib/python3/dist-packages/urllib3/connection.py", line 284, in connect
	    conn = self._new_conn()
	  File "/usr/lib/python3/dist-packages/urllib3/connection.py", line 150, in _new_conn
	    self, "Failed to establish a new connection: %s" % e)
	urllib3.exceptions.NewConnectionError: <urllib3.connection.VerifiedHTTPSConnection object at 0x7fd54273b6d0>: Failed to establish a new conn                                                                                                                                              ection: [Errno 111] Connection refused

	During handling of the above exception, another exception occurred:

	Traceback (most recent call last):
	  File "/usr/local/lib/python3.7/dist-packages/requests/adapters.py", line 449, in send
	    timeout=timeout
	  File "/usr/lib/python3/dist-packages/urllib3/connectionpool.py", line 639, in urlopen
	    _stacktrace=sys.exc_info()[2])
	  File "/usr/lib/python3/dist-packages/urllib3/util/retry.py", line 398, in increment
	    raise MaxRetryError(_pool, url, error or ResponseError(cause))
	urllib3.exceptions.MaxRetryError: HTTPSConnectionPool(host='girder.local.wholetale.org', port=443): Max retries exceeded with url: /api/v1 (                                                                                                                                              Caused by NewConnectionError('<urllib3.connection.VerifiedHTTPSConnection object at 0x7fd54273b6d0>: Failed to establish a new connection: [                                                                                                                                              Errno 111] Connection refused'))

	During handling of the above exception, another exception occurred:

	Traceback (most recent call last):
	  File "./setup_girder.py", line 31, in <module>
	    r = requests.get(api_url)
	  File "/usr/local/lib/python3.7/dist-packages/requests/api.py", line 76, in get
	    return request('get', url, params=params, **kwargs)
	  File "/usr/local/lib/python3.7/dist-packages/requests/api.py", line 61, in request
	    return session.request(method=method, url=url, **kwargs)
	  File "/usr/local/lib/python3.7/dist-packages/requests/sessions.py", line 530, in request
	    resp = self.send(prep, **send_kwargs)
	  File "/usr/local/lib/python3.7/dist-packages/requests/sessions.py", line 643, in send
	    r = adapter.send(request, **kwargs)
	  File "/usr/local/lib/python3.7/dist-packages/requests/adapters.py", line 516, in send
	    raise ConnectionError(e, request=request)
	requests.exceptions.ConnectionError: HTTPSConnectionPool(host='girder.local.wholetale.org', port=443): Max retries exceeded with url: /api/v                                                                                                                                              1 (Caused by NewConnectionError('<urllib3.connection.VerifiedHTTPSConnection object at 0x7fd54273b6d0>: Failed to establish a new connection                                                                                                                                              : [Errno 111] Connection refused'))
	Error in sys.excepthook:
	Traceback (most recent call last):
	  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 63, in apport_excepthook
	    from apport.fileutils import likely_packaged, get_recent_crashes
	  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
	    from apport.report import Report
	  File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in <module>
	    import apport.fileutils
	  File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 23, in <module>
	    from apport.packaging_impl import impl as packaging
	  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 24, in <module>
	    import apt
	  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
	    import apt_pkg
	ModuleNotFoundError: No module named 'apt_pkg'

	Original exception was:
	Traceback (most recent call last):
	  File "/usr/lib/python3/dist-packages/urllib3/connection.py", line 141, in _new_conn
	    (self.host, self.port), self.timeout, **extra_kw)
	  File "/usr/lib/python3/dist-packages/urllib3/util/connection.py", line 83, in create_connection
	    raise err
	  File "/usr/lib/python3/dist-packages/urllib3/util/connection.py", line 73, in create_connection
	    sock.connect(sa)
	ConnectionRefusedError: [Errno 111] Connection refused

	During handling of the above exception, another exception occurred:

	Traceback (most recent call last):
	  File "/usr/lib/python3/dist-packages/urllib3/connectionpool.py", line 601, in urlopen
	    chunked=chunked)
	  File "/usr/lib/python3/dist-packages/urllib3/connectionpool.py", line 346, in _make_request
	    self._validate_conn(conn)
	  File "/usr/lib/python3/dist-packages/urllib3/connectionpool.py", line 852, in _validate_conn
	    conn.connect()
	  File "/usr/lib/python3/dist-packages/urllib3/connection.py", line 284, in connect
	    conn = self._new_conn()
	  File "/usr/lib/python3/dist-packages/urllib3/connection.py", line 150, in _new_conn
	    self, "Failed to establish a new connection: %s" % e)
	urllib3.exceptions.NewConnectionError: <urllib3.connection.VerifiedHTTPSConnection object at 0x7fd54273b6d0>: Failed to establish a new connection: [Errno 111] Connection refused

	During handling of the above exception, another exception occurred:

	Traceback (most recent call last):
	  File "/usr/local/lib/python3.7/dist-packages/requests/adapters.py", line 449, in send
	    timeout=timeout
	  File "/usr/lib/python3/dist-packages/urllib3/connectionpool.py", line 639, in urlopen
	    _stacktrace=sys.exc_info()[2])
	  File "/usr/lib/python3/dist-packages/urllib3/util/retry.py", line 398, in increment
	    raise MaxRetryError(_pool, url, error or ResponseError(cause))
	urllib3.exceptions.MaxRetryError: HTTPSConnectionPool(host='girder.local.wholetale.org', port=443): Max retries exceeded with url: /api/v1 (Caused by NewConnectionError('<urllib3.connection.VerifiedHTTPSConnection object at 0x7fd54273b6d0>: Failed to establish a new connection: [Errno 111] Connection refused'))

	During handling of the above exception, another exception occurred:

	Traceback (most recent call last):
	  File "./setup_girder.py", line 31, in <module>
	    r = requests.get(api_url)
	  File "/usr/local/lib/python3.7/dist-packages/requests/api.py", line 76, in get
	    return request('get', url, params=params, **kwargs)
	  File "/usr/local/lib/python3.7/dist-packages/requests/api.py", line 61, in request
	    return session.request(method=method, url=url, **kwargs)
	  File "/usr/local/lib/python3.7/dist-packages/requests/sessions.py", line 530, in request
	    resp = self.send(prep, **send_kwargs)
	  File "/usr/local/lib/python3.7/dist-packages/requests/sessions.py", line 643, in send
	    r = adapter.send(request, **kwargs)
	  File "/usr/local/lib/python3.7/dist-packages/requests/adapters.py", line 516, in send
	    raise ConnectionError(e, request=request)
	requests.exceptions.ConnectionError: HTTPSConnectionPool(host='girder.local.wholetale.org', port=443): Max retries exceeded with url: /api/v1 (Caused by NewConnectionError('<urllib3.connection.VerifiedHTTPSConnection object at 0x7fd54273b6d0>: Failed to establish a new connection: [Errno 111] Connection refused'))
	Makefile:49: recipe for target 'dev' failed
	make: *** [dev] Error 1

	```
- The first exception is a `ConnectionRefusedError` (copied from preceding output):
	```
	. . .
	./setup_girder.py
	Waiting for Girder to start
	Traceback (most recent call last):
	  File "/usr/lib/python3/dist-packages/urllib3/connection.py", line 141, in _new_conn
	    (self.host, self.port), self.timeout, **extra_kw)
	  File "/usr/lib/python3/dist-packages/urllib3/util/connection.py", line 83, in create_connection
	    raise err
	  File "/usr/lib/python3/dist-packages/urllib3/util/connection.py", line 73, in create_connection
	    sock.connect(sa)
	ConnectionRefusedError: [Errno 111] Connection refused
	. . .
	```
- During handling of the above exception, another exception occurred indicating that the failed connection is on port 443:
	```
	Traceback (most recent call last):
	  File "/usr/local/lib/python3.7/dist-packages/requests/adapters.py", line 449, in send
	    timeout=timeout
	  File "/usr/lib/python3/dist-packages/urllib3/connectionpool.py", line 639, in urlopen
	    _stacktrace=sys.exc_info()[2])
	  File "/usr/lib/python3/dist-packages/urllib3/util/retry.py", line 398, in increment
	    raise MaxRetryError(_pool, url, error or ResponseError(cause))
	urllib3.exceptions.MaxRetryError: 
		HTTPSConnectionPool(host='girder.local.wholetale.org', port=443): Max retries exceeded with url: /api/v1 (                                                                                                                                              
		Caused by NewConnectionError('<urllib3.connection.VerifiedHTTPSConnection object at 0x7fd54273b6d0>: Failed to establish a new connection: [                                                                                                                                              Errno 111] Connection refused'))
	```

### Compared current status of system with expectations given in README

- Checked which services started successfully despite the errors above:
	```
	tmcphill@artemis:~/deploy-dev$ docker service ls
	ID                  NAME                MODE                REPLICAS            IMAGE                             PORTS
	afn4ovha6sns        wt_dashboard        replicated          1/1                 wholetale/dashboardproxy:latest
	gdnd47dt96cw        wt_dashboard_next   replicated          1/1                 bodom0015/ng-dashboard:wt
	mv93s5t5lgnd        wt_girder           replicated          1/1                 wholetale/girder:latest
	wagnda3ctnh1        wt_mongo            replicated          1/1                 mongo:3.2
	qtmughf9j9ng        wt_redis            replicated          1/1                 redis:4-stretch
	qkvzf99rxe78        wt_registry         replicated          1/1                 registry:2.6
	i3t35q0z1nkx        wt_traefik          replicated          0/1                 traefik:alpine                    *:80->80/tcp, *:443->443/tcp, *:8080->8080/tcp
	```
- And listed running containers:
	```
	tmcphill@artemis:~/deploy-dev$ docker ps
	CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS              PORTS               NAMES
	646040bee4b8        wholetale/gwvolman:latest         "/docker-entrypoint.…"   42 minutes ago      Up 42 minutes                           celery_worker
	763f6c34eb9b        wholetale/girder:latest           "/usr/local/bin/dock…"   42 minutes ago      Up 42 minutes       8080/tcp            wt_girder.1.q8jrb3en5z1amnxmbeo9wdq5e
	4da20c09f8b7        mongo:3.2                         "docker-entrypoint.s…"   43 minutes ago      Up 43 minutes       27017/tcp           wt_mongo.1.lecu4rxaejdqnkgdqxq4lq85q
	3caef98ca999        redis:4-stretch                   "docker-entrypoint.s…"   43 minutes ago      Up 43 minutes       6379/tcp            wt_redis.1.v5bz1j7vvffhdjj8198p745mi
	b70349dc2dc4        wholetale/dashboardproxy:latest   "nginx -g 'daemon of…"   43 minutes ago      Up 43 minutes       80/tcp              wt_dashboard.1.jpjlw05t0ff3bdu3x3nxbh6sn
	ddf55c72a418        registry:2.6                      "/entrypoint.sh /etc…"   43 minutes ago      Up 43 minutes       5000/tcp            wt_registry.1.qb3e32hrymjlf7nyi84cz7zt3
	b42560c493e1        bodom0015/ng-dashboard:wt         "nginx -g 'daemon of…"   43 minutes ago      Up 43 minutes       80/tcp              wt_dashboard_next.1.8gqvteqsuz99d7yra2mg38q90
	```

- Listed `celery_worker` specifically:
	```
	tmcphill@artemis:~/deploy-dev$ docker ps | grep celery_worker
	646040bee4b8        wholetale/gwvolman:latest         "/docker-entrypoint.…"   45 minutes ago      Up 45 minutes                           celery_worker
	```
- All expected services appear to be running.

- However, there are differences between the output of `docker service ls` and the sample output in the README:

	- There is both a  `wt_dashboard` and a `wt_dashboard_next` service running on `artemis`.  The expected output in the README does not  includes  `wt_dashboard_next`.

	- The ports associated with `wt_traefik` include `443` (https) on `artemis`...
		```
		...   wt_traefik    ...   *:80->80/tcp, *:443->443/tcp, *:8080->8080/tcp
		```
		...but not in the expected output in the README:
		```
		...   wt_traefik    ...   *:80->80/tcp, *:8080->8080/tcp
		```
	- And while no ports are associated with the `wt_registry` service on `artemis`...
		```
		...   wt_registry   ...   
		```
		...port `443` is associated with this service in the README sample output:
		```
		...   wt_registry   ...   *:443->443/tcp
		```

- Noted last commit in local clone of  `whole-tale/deploy-dev`:
	```
	tmcphill@artemis:~/deploy-dev$ git log | head -9
	commit 20daa6d68334e43679b6b3b930b0db4d53600177
	Merge: fe29e85 9693f11
	Author: Kacper Kowalik <xarthisius.kk@gmail.com>
	Date:   Wed Jan 22 11:55:34 2020 -0600

	    Merge pull request #30 from whole-tale/rename-images

	    Rename images to match production
	 ```
