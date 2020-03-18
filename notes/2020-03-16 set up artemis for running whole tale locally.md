## 2020-03-16 Set up artemis for running Whole Tale locally

### Background

- Need to run Whole Tale locally to evaluation options for further extension.
- Instructions and scripts for deploying WT locally are in [whole-tale/deploy-dev](https://github.com/whole-tale/deploy-dev).
- Will deploy WT to artemis which is running the version of Ubuntu supported by WT.

### Backed up entire disk hosting Ubuntu environment
- Used Paragon Hard Disk Manager 16.5 Advanced on Apollo (Windows 10).
- Performed a full backup of artemis system disk as part of a new incremental backup sequence:![](https://lh3.googleusercontent.com/RPACnf8U3ywmLp9EORV87UzafqxP0Xh5qFl1T3yjR9nkvBxFykzGRDbz_znOuyFvy0v0TtlZ_JrX=s800)
	 ![](https://lh3.googleusercontent.com/hc6rowwjQdK-9rPSA6wntBarL3AbqIDkrPpsWt4E_R2lCBjiRV9HtvdXcteACKHz1dwxp8fVpDrm=s800)
![
](https://lh3.googleusercontent.com/zkm3r5rRJTClo806qheZnSJRmDtxU4iIVsG7J0Bil5iphZ1GfhubqkLa5rRUXmNcTMsMShLKLmQ9=s800)
### Confirm distribution and kernel version and that system is up to date 

- Confirmed that artemis is running **Ubuntu 18.04**:
	```
	tmcphill@artemis:~$ cat /etc/lsb-release
	DISTRIB_ID=Ubuntu
	DISTRIB_RELEASE=18.04
	DISTRIB_CODENAME=bionic
	DISTRIB_DESCRIPTION="Ubuntu 18.04.4 LTS"
	```
- Noted that kernel version is **`4.15.0-91-generic`**:
	```
	tmcphill@artemis:~$ uname -a
	Linux artemis 4.15.0-91-generic #92-Ubuntu SMP Fri Feb 28 11:09:48 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
	```
- Checked that all apt packages are up to date:
	```
	tmcphill@artemis:~$ sudo apt update
	[sudo] password for tmcphill: 
	Get:1 file:/var/cuda-repo-10-0-local-10.0.130-410.48  InRelease
	Ign:1 file:/var/cuda-repo-10-0-local-10.0.130-410.48  InRelease
	Get:2 file:/var/cuda-repo-10-0-local-10.0.130-410.48  Release [574 B]
	Get:2 file:/var/cuda-repo-10-0-local-10.0.130-410.48  Release [574 B]
	Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease
	Hit:4 http://packages.microsoft.com/repos/vscode stable InRelease                                                                                     
	Hit:6 https://download.docker.com/linux/ubuntu bionic InRelease                                                                                       
	Hit:7 http://us.archive.ubuntu.com/ubuntu bionic InRelease                                                                                            
	Hit:8 http://dl.google.com/linux/chrome/deb stable Release                                                                                            
	Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]                                              
	Get:10 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]                              
	Hit:11 http://ppa.launchpad.net/ubuntugis/ppa/ubuntu bionic InRelease                                                  
	Get:12 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]                                        
	Get:14 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [655 kB]           
	Get:15 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [38.5 kB]
	Get:16 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [883 kB]    
	Get:17 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [307 kB]        
	Get:18 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [73.8 kB]
	Get:19 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [140 kB]
	Get:20 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 128x128 Icons [348 kB]
	Get:21 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [1,010 kB]
	Get:22 http://security.ubuntu.com/ubuntu bionic-security/main DEP-11 48x48 Icons [17.6 kB]
	Get:23 http://security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64 Icons [41.5 kB]        
	Get:24 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1,057 kB]     
	Get:25 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [265 kB] 
	Get:26 http://security.ubuntu.com/ubuntu bionic-security/main DEP-11 128x128 Icons [97.7 kB]            
	Get:27 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [199 kB]            
	Get:28 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [458 kB]      
	Get:29 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 128x128 Icons [1,006 kB]  
	Get:30 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]             
	Get:31 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [7,984 B]                 
	Get:32 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [42.1 kB]                    
	Get:33 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [16.4 kB]
	Get:34 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [116 kB]
	Get:35 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 128x128 Icons [181 kB]
	Get:36 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]
	Fetched 7,218 kB in 2s (3,066 kB/s)              
	Reading package lists... Done
	Building dependency tree       
	Reading state information... Done
	All packages are up to date.

	tmcphill@artemis:~$ sudo apt upgrade
	Reading package lists... Done
	Building dependency tree       
	Reading state information... Done
	Calculating upgrade... Done
	0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
	```
### Installed required FUSE and WebDAV support
 
- Checked versions of `davfs2`, `fuse`, and `libfuse-dev` currently installed:
	```
	tmcphill@artemis:~$ sudo apt list davfs2 fuse libfuse-dev
	Listing... Done
	davfs2/bionic 1.5.4-2 amd64
	fuse/bionic,now 2.9.7-1ubuntu1 amd64 [installed]
	libfuse-dev/bionic 2.9.7-1ubuntu1 amd64
	```
- Installed the missing packages, enabling mounting of WebDAV volumes by unprivileged users when prompted:
	```
	tmcphill@artemis:~$ sudo apt install davfs2 fuse libfuse-dev
	Reading package lists... Done
	Building dependency tree       
	Reading state information... Done
	fuse is already the newest version (2.9.7-1ubuntu1).
	The following additional packages will be installed:
	  libneon27 libpcre16-3 libpcre3-dev libpcre32-3 libpcrecpp0v5 libselinux1-dev libsepol1-dev
	The following NEW packages will be installed:
	  davfs2 libfuse-dev libneon27 libpcre16-3 libpcre3-dev libpcre32-3 libpcrecpp0v5 libselinux1-dev libsepol1-dev
	0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
	Need to get 1,644 kB of archives.
	After this operation, 7,348 kB of additional disk space will be used.
	Do you want to continue? [Y/n] 
	Get:1 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libsepol1-dev amd64 2.7-1 [324 kB]
	Get:2 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpcre16-3 amd64 2:8.39-9 [147 kB]
	Get:3 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpcre32-3 amd64 2:8.39-9 [138 kB]
	Get:4 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpcrecpp0v5 amd64 2:8.39-9 [15.3 kB]
	Get:5 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpcre3-dev amd64 2:8.39-9 [537 kB]
	Get:6 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libselinux1-dev amd64 2.7-2build2 [149 kB]
	Get:7 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libfuse-dev amd64 2.9.7-1ubuntu1 [105 kB]
	Get:8 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libneon27 amd64 0.30.2-3~ubuntu18.04.1 [94.6 kB]
	Get:9 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 davfs2 amd64 1.5.4-2 [134 kB]
	Fetched 1,644 kB in 1s (1,782 kB/s)
	Preconfiguring packages ...
	Selecting previously unselected package libsepol1-dev:amd64.
	(Reading database ... 233604 files and directories currently installed.)
	Preparing to unpack .../0-libsepol1-dev_2.7-1_amd64.deb ...
	Unpacking libsepol1-dev:amd64 (2.7-1) ...
	Selecting previously unselected package libpcre16-3:amd64.
	Preparing to unpack .../1-libpcre16-3_2%3a8.39-9_amd64.deb ...
	Unpacking libpcre16-3:amd64 (2:8.39-9) ...
	Selecting previously unselected package libpcre32-3:amd64.
	Preparing to unpack .../2-libpcre32-3_2%3a8.39-9_amd64.deb ...
	Unpacking libpcre32-3:amd64 (2:8.39-9) ...
	Selecting previously unselected package libpcrecpp0v5:amd64.
	Preparing to unpack .../3-libpcrecpp0v5_2%3a8.39-9_amd64.deb ...
	Unpacking libpcrecpp0v5:amd64 (2:8.39-9) ...
	Selecting previously unselected package libpcre3-dev:amd64.
	Preparing to unpack .../4-libpcre3-dev_2%3a8.39-9_amd64.deb ...
	Unpacking libpcre3-dev:amd64 (2:8.39-9) ...
	Selecting previously unselected package libselinux1-dev:amd64.
	Preparing to unpack .../5-libselinux1-dev_2.7-2build2_amd64.deb ...
	Unpacking libselinux1-dev:amd64 (2.7-2build2) ...
	Selecting previously unselected package libfuse-dev.
	Preparing to unpack .../6-libfuse-dev_2.9.7-1ubuntu1_amd64.deb ...
	Unpacking libfuse-dev (2.9.7-1ubuntu1) ...
	Selecting previously unselected package libneon27:amd64.
	Preparing to unpack .../7-libneon27_0.30.2-3~ubuntu18.04.1_amd64.deb ...
	Unpacking libneon27:amd64 (0.30.2-3~ubuntu18.04.1) ...
	Selecting previously unselected package davfs2.
	Preparing to unpack .../8-davfs2_1.5.4-2_amd64.deb ...
	Unpacking davfs2 (1.5.4-2) ...
	Setting up libsepol1-dev:amd64 (2.7-1) ...
	Setting up libpcrecpp0v5:amd64 (2:8.39-9) ...
	Setting up libpcre32-3:amd64 (2:8.39-9) ...
	Setting up libpcre16-3:amd64 (2:8.39-9) ...
	Setting up libneon27:amd64 (0.30.2-3~ubuntu18.04.1) ...
	Setting up libpcre3-dev:amd64 (2:8.39-9) ...
	Setting up davfs2 (1.5.4-2) ...
	Setting up libselinux1-dev:amd64 (2.7-2build2) ...
	Setting up libfuse-dev (2.9.7-1ubuntu1) ...
	Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
	Processing triggers for libc-bin (2.27-3ubuntu1) ...
	```
- Confirmed the packages are now installed:
	```
	tmcphill@artemis:~$ sudo apt list davfs2 fuse libfuse-dev
	Listing... Done
	davfs2/bionic,now 1.5.4-2 amd64 [installed]
	fuse/bionic,now 2.9.7-1ubuntu1 amd64 [installed]
	libfuse-dev/bionic,now 2.9.7-1ubuntu1 amd64 [installed]
	```
### Configure user accounts
- WT requires a user with UID 1000 and GID 100.  Noted that my account has user UID 1000 but GID 1000:
	```
	tmcphill@artemis:~$ id
	uid=1000(tmcphill) gid=1000(tmcphill) groups=1000(tmcphill),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare),999(docker
	```
- The existing group `users` has `UID=100`, but `tmcphill` is not a member of the `users` group:
	```
	tmcphill@artemis:~$ grep users /etc/group
	users:x:100:

	tmcphill@artemis:~$ groups tmcphill
	tmcphill : tmcphill adm cdrom sudo dip plugdev lpadmin sambashare docker
	```

- Added `tmcphill` to the `users` group and made it the account's primary group:
	```
	tmcphill@artemis:~$ sudo usermod -g users tmcphill
	```

- Confirmed that entry in `/etc/passwd` has been updated to reflect new primary group:
	```
	tmcphill@artemis:~$ grep tmcphill /etc/passwd
	tmcphill:x:1000:100:Timothy McPhillips,,,:/home/tmcphill:/bin/bash
	```
- Added `tmcphill` group as a second group for the `tmcphill` account so current access to files is maintained, and confirmed that all other previous groups memberships are maintained (via the `-a` flag):
	```
	tmcphill@artemis:~$ sudo usermod -a -G tmcphill tmcphill
	
	tmcphill@artemis:~$ grep tmcphill /etc/group
	adm:x:4:syslog,tmcphill
	cdrom:x:24:tmcphill
	sudo:x:27:tmcphill
	dip:x:30:tmcphill
	plugdev:x:46:tmcphill
	lpadmin:x:116:tmcphill
	tmcphill:x:1000:tmcphill
	sambashare:x:126:tmcphill
	docker:x:999:tmcphill
	```
- Started new terminal and noted that UID, GID, and group memberships are as expected:
	```
	tmcphill@artemis:~$ id
	uid=1000(tmcphill) gid=100(users) groups=100(users),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare),999(docker),1000(tmcphill)
	```

### Checked Docker installation

- Determined that Docker version is `19.0.3.8`:
	```
	tmcphill@artemis:~$ apt list -a docker-ce
	Listing... Done
	docker-ce/bionic,now 5:19.03.8~3-0~ubuntu-bionic amd64 [installed]
	docker-ce/bionic 5:19.03.7~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:19.03.6~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:19.03.5~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:19.03.4~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:19.03.3~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:19.03.2~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:19.03.1~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:19.03.0~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:18.09.9~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:18.09.8~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:18.09.7~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:18.09.6~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:18.09.5~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:18.09.4~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:18.09.3~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:18.09.2~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:18.09.1~3-0~ubuntu-bionic amd64
	docker-ce/bionic 5:18.09.0~3-0~ubuntu-bionic amd64
	docker-ce/bionic 18.06.3~ce~3-0~ubuntu amd64
	docker-ce/bionic 18.06.2~ce~3-0~ubuntu amd64
	docker-ce/bionic 18.06.1~ce~3-0~ubuntu amd64
	docker-ce/bionic 18.06.0~ce~3-0~ubuntu amd64
	docker-ce/bionic 18.03.1~ce~3-0~ubuntu amd64
	```
- Confirmed that swarm mode currently is inactive:
	```
	tmcphill@artemis:~$ docker info
	Client:
	 Debug Mode: false

	Server:
	 Containers: 2
	  Running: 0
	  Paused: 0
	  Stopped: 2
	 Images: 45
	 Server Version: 19.03.8
	 Storage Driver: overlay2
	  Backing Filesystem: <unknown>
	  Supports d_type: true
	  Native Overlay Diff: true
	 Logging Driver: json-file
	 Cgroup Driver: cgroupfs
	 Plugins:
	  Volume: local
	  Network: bridge host ipvlan macvlan null overlay
	  Log: awslogs fluentd gcplogs gelf journald json-file local logentries splunk syslog
	 Swarm: inactive
	 Runtimes: runc
	 Default Runtime: runc
	 Init Binary: docker-init
	 containerd version: 7ad184331fa3e55e52b890ea95e65ba581ae3429
	 runc version: dc9208a3303feef5b3839f4323d9beb36df0a9dd
	 init version: fec3683
	 Security Options:
	  apparmor
	  seccomp
	   Profile: default
	 Kernel Version: 4.15.0-91-generic
	 Operating System: Ubuntu 18.04.4 LTS
	 OSType: linux
	 Architecture: x86_64
	 CPUs: 4
	 Total Memory: 30.37GiB
	 Name: artemis
	 ID: IBKI:D7NO:UGPQ:DV62:DCQF:KWYF:PAS5:QKCN:Y6EU:XJW6:BBE3:IDUZ
	 Docker Root Dir: /var/lib/docker
	 Debug Mode: false
	 Registry: https://index.docker.io/v1/
	 Labels:
	 Experimental: false
	 Insecure Registries:
	  127.0.0.0/8
	 Live Restore Enabled: false

	WARNING: No swap limit support
	```
- Performed increment 1 of the system backup before continuing:
![enter image description here](https://lh3.googleusercontent.com/xDHqBlzd_oq_FPi5TiZeCjKf940i8TX2rHJq2i4V5RBE18j8ONGN4QHQ1fhfzXmF2RdwRvbmnJDJ=s800)
	![enter image description here](https://lh3.googleusercontent.com/eN23U89c0Tiyne4bT9lcR0gS_jbvQGYHRWsYfdbB8Kc1MPRrhaf51xDiKdiZ4jbG3x2KpDNm9FFm=s800)

###	Configure Docker to run in single-node swarm mode

- Initialized artemis as a swarm manager using the loopback address as `advertise-addr` to limit cluster to this machine:
	```
	tmcphill@artemis:~$ docker swarm init --advertise-addr 127.0.0.1
	Swarm initialized: current node (sfhevmg8ld5vnjbu7ibhftt6z) is now a manager.

	To add a worker to this swarm, run the following command:

	    docker swarm join --token XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX 127.0.0.1:2377

	To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
	```
- Checked swarm status noting that there is one manager and one node:
	```
	tmcphill@artemis:~$ docker info
	. . .
	 Swarm: active
	  NodeID: sfhevmg8ld5vnjbu7ibhftt6z
	  Is Manager: true
	  ClusterID: tdg6675yq42qri4rdyay90oms
	  Managers: 1
	  Nodes: 1
	  Default Address Pool: 10.0.0.0/8  
	  SubnetSize: 24
	  Data Path Port: 4789
	  Orchestration:
	   Task History Retention Limit: 5
	  Raft:
	   Snapshot Interval: 10000
	   Number of Old Snapshots to Retain: 0
	   Heartbeat Tick: 1
	   Election Tick: 10
	  Dispatcher:
	   Heartbeat Period: 5 seconds
	  CA Configuration:
	   Expiry Duration: 3 months
	   Force Rotate: 0
	  Autolock Managers: false
	  Root Rotation In Progress: false
	  Node Address: 127.0.0.1
	  Manager Addresses:
	   127.0.0.1:2377
	. . .
	```
- Listed info about the single swarm node:
	```
	tmcphill@artemis:~$ docker node ls
	ID                            HOSTNAME            STATUS              AVAILABILITY        MANAGER STATUS      ENGINE VERSION
	sfhevmg8ld5vnjbu7ibhftt6z *   artemis             Ready               Active              Leader              19.03.8
	```
- Rebooted system and noted that system is still in swarm mode as above.

### Installed Globus Oauth ID and SSL certificates

- Added two lines to end of ~/.bashrc, copying values (redacted) from #core-dev Slack channel pinned items:
	```bash
	export GLOBUS_CLIENT_ID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
	export GLOBUS_CLIENT_SECRET=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
	```
- Downloaded acme.json certificate from #core-dev Slack channel and installed in `~/traefik/acme/` owned and readable only by root:
	```
	tmcphill@artemis:~$ mkdir -p traefik/acme
	tmcphill@artemis:~$ cp ~/Downloads/acme.json traefik/acme/acme.json
	tmcphill@artemis:~$ sudo chown root:root traefik/acme/acme.json
	tmcphill@artemis:~$ sudo chmod 0600 traefik/acme/acme.json
	tmcphill@artemis:~$ ls -alR traefik/acme/acme.json 
	-rw------- 1 root root 10686 Mar 16 23:58 traefik/acme/acme.json
	```
- Performed increment 2 of the system backup before starting Whole Tale for the first time:
![](https://lh3.googleusercontent.com/71ZRGWUcoQv7pUZx9w5Xa0xREeYP5sl3j3h4yRYn8wRBArp2Ss8CpxsPidK0Ilhz9Wr7T0iXCEvU=s800)

### Ensured python and pip versions are consistent

- Linked `/usr/bin/python` to `/usr/bin/python3.7`:
	``` 
	tmcphill@artemis:/usr/bin$ ls -al *python*
	-rwxr-xr-x 1 root root    1056 Apr 16  2018 dh_python2
	lrwxrwxrwx 1 root root       9 Mar 17 02:46 python -> python3.6
	lrwxrwxrwx 1 root root       9 Nov  7  2018 python2 -> python2.7
	-rwxr-xr-x 1 root root 3637096 Nov  7 02:07 python2.7
	lrwxrwxrwx 1 root root       9 Oct 25  2018 python3 -> python3.6
	-rwxr-xr-x 2 root root 4526456 Nov  7 02:44 python3.6
	-rwxr-xr-x 2 root root 4526456 Nov  7 02:44 python3.6m
	-rwxr-xr-x 2 root root 4873376 Nov  7 02:50 python3.7
	-rwxr-xr-x 2 root root 4873376 Nov  7 02:50 python3.7m
	lrwxrwxrwx 1 root root      10 Oct 25  2018 python3m -> python3.6m

	tmcphill@artemis:/usr/bin$ sudo rm python python3
	tmcphill@artemis:/usr/bin$ sudo ln -s python3.7 python
	tmcphill@artemis:/usr/bin$ sudo ln -s python3.7 python3

	tmcphill@artemis:/usr/bin$ ls -al *python*
	-rwxr-xr-x 1 root root    1056 Apr 16  2018 dh_python2
	lrwxrwxrwx 1 root root       9 Mar 17 02:49 python -> python3.7
	lrwxrwxrwx 1 root root       9 Nov  7  2018 python2 -> python2.7
	-rwxr-xr-x 1 root root 3637096 Nov  7 02:07 python2.7
	lrwxrwxrwx 1 root root       9 Mar 17 02:52 python3 -> python3.7
	-rwxr-xr-x 2 root root 4526456 Nov  7 02:44 python3.6
	-rwxr-xr-x 2 root root 4526456 Nov  7 02:44 python3.6m
	-rwxr-xr-x 2 root root 4873376 Nov  7 02:50 python3.7
	-rwxr-xr-x 2 root root 4873376 Nov  7 02:50 python3.7m
	lrwxrwxrwx 1 root root      10 Oct 25  2018 python3m -> python3.6m
	```
- Confirmed that `python` and `python3` both run `python3.7`: 
	```
	tmcphill@artemis:/usr/bin$ python --version
	Python 3.7.5
	
	tmcphill@artemis:/usr/bin$ python3 --version
	Python 3.7.5	
	```

- Confirmed that `pip` and `pip3` commands correspond to `python3.7` as well:
	```
	tmcphill@artemis:/usr/local/bin$ pip --version
	pip 19.3.1 from /usr/local/lib/python3.7/dist-packages/pip (python 3.7)
	
	tmcphill@artemis:/usr/local/bin$ pip3 --version
	pip 19.3.1 from /usr/local/lib/python3.7/dist-packages/pip (python 3.7)
	```

- Installed `requests` package version `2.23.0`:
	```
	tmcphill@artemis:/usr/local/bin$ sudo pip install --upgrade requests
	Collecting requests
	  Downloading https://files.pythonhosted.org/packages/1a/70/1935c770cb3be6e3a8b78ced23d7e0f3b187f5cbfab4749523ed65d7c9b1/requests-2.23.0-py2.py3-none-any.whl (58kB)
	     |████████████████████████████████| 61kB 2.4MB/s
	Requirement already satisfied, skipping upgrade: certifi>=2017.4.17 in /usr/lib/python3/dist-packages (from requests) (2018.1.18)
	Requirement already satisfied, skipping upgrade: urllib3!=1.25.0,!=1.25.1,<1.26,>=1.21.1 in /usr/lib/python3/dist-packages (from requests) (1.22)
	Requirement already satisfied, skipping upgrade: idna<3,>=2.5 in /usr/lib/python3/dist-packages (from requests) (2.6)
	Requirement already satisfied, skipping upgrade: chardet<4,>=3.0.2 in /usr/lib/python3/dist-packages (from requests) (3.0.4)
	Installing collected packages: requests
	Successfully installed requests-2.23.0
	```

- Listed Python packages installed system-wide:
	```
	tmcphill@artemis:/usr/local/bin$ pip list
	Package                 Version
	----------------------- -------------------
	apt-xapian-index        0.47
	asn1crypto              0.24.0
	certifi                 2018.1.18
	chardet                 3.0.4
	command-not-found       0.3
	cryptography            2.1.4
	cupshelpers             1.0
	distro-info             0.18ubuntu0.18.04.1
	GDAL                    2.4.2
	httplib2                0.9.2
	idna                    2.6
	language-selector       0.1
	netifaces               0.10.4
	numpy                   1.13.3
	olefile                 0.45.1
	pexpect                 4.2.1
	Pillow                  5.1.0
	pip                     19.3.1
	pycairo                 1.16.2
	pycups                  1.9.73
	pygobject               3.26.1
	python-apt              1.6.5+ubuntu0.2
	python-debian           0.1.32
	pyxdg                   0.25
	PyYAML                  3.12
	reportlab               3.4.0
	requests                2.23.0
	requests-unixsocket     0.1.5
	screen-resolution-extra 0.0.0
	setuptools              39.0.1
	six                     1.11.0
	ssh-import-id           5.7
	systemd-python          234
	ubuntu-drivers-common   0.0.0
	ufw                     0.36
	unattended-upgrades     0.1
	urllib3                 1.22
	wheel                   0.33.6
	xkit                    0.0.0
	```
- Backed up system again (increment 3):
![](https://lh3.googleusercontent.com/U76_H8nFVGY4l-aFXKssQUOCcLHoZMqD0RrY1EH2_IHow4L8yerhiQREk4hVgfr2s4nD7LhM_fXg=s800)
