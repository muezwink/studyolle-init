
$ docker run -d -p 5432:5432 --name spring-jpa-postgres --rm -v pgdata:/var/lib/postgresql/data postgres
828b1cbb71d649f7762cbca85950f6aae2eacc59260344ee9e4f09d43e3adda2

mraz@DESKTOP-2G6QFBR MINGW64 /e/project-learn/inflearn/studyolle-init (master)
$ docker ps -a
CONTAINER ID        IMAGE                                            COMMAND                  CREATED             STATUS                     PORTS                              NAMES
828b1cbb71d6        postgres                                         "docker-entrypoint.s…"   4 seconds ago       Up 3 seconds               0.0.0.0:5432->5432/tcp             spring-jpa-postgres
638b9ee1b256        mariadb                                          "docker-entrypoint.s…"   2 weeks ago         Exited (255) 2 weeks ago   0.0.0.0:3306->3306/tcp             spring-mariadb
1ca9f725943f        store/oracle/database-enterprise:12.2.0.1        "/bin/sh -c '/bin/ba…"   4 weeks ago         Exited (255) 2 weeks ago   0.0.0.0:1521->1521/tcp, 5500/tcp   oracle12c
37c1c5af535a        store/oracle/database-enterprise:12.2.0.1-slim   "/bin/sh -c '/bin/ba…"   4 weeks ago         Exited (137) 2 weeks ago                                      oracle12s
9a2a72081c69        jaspeen/oracle-xe-11g                            "/entrypoint.sh "        4 weeks ago         Exited (137) 2 weeks ago                                      oracle11g

$ docker exec -it spring-jpa-postgres bash
root@828b1cbb71d6:/# apt-get update
Get:1 http://security.debian.org/debian-security buster/updates InRelease [65.4 kB]
Get:2 http://deb.debian.org/debian buster InRelease [121 kB]
Get:3 http://deb.debian.org/debian buster-updates InRelease [51.9 kB]
Get:4 http://security.debian.org/debian-security buster/updates/main amd64 Packages [203 kB]
Get:5 http://deb.debian.org/debian buster/main amd64 Packages [7,905 kB]
Get:6 http://apt.postgresql.org/pub/repos/apt buster-pgdg InRelease [84.6 kB]
Get:7 http://apt.postgresql.org/pub/repos/apt buster-pgdg/12 amd64 Packages [861 B]
Get:8 http://apt.postgresql.org/pub/repos/apt buster-pgdg/main amd64 Packages [177 kB]
Get:9 http://deb.debian.org/debian buster-updates/main amd64 Packages [7,868 B]
Fetched 8,617 kB in 5s (1,877 kB/s)
Reading package lists... Done

root@828b1cbb71d6:/# apt-get install net-tools
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  net-tools
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 248 kB of archives.
After this operation, 1,002 kB of additional disk space will be used.
Get:1 http://deb.debian.org/debian buster/main amd64 net-tools amd64 1.60+git20180626.aebd88e-1 [248 kB]
Fetched 248 kB in 1s (331 kB/s)
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously unselected package net-tools.
(Reading database ... 11764 files and directories currently installed.)
Preparing to unpack .../net-tools_1.60+git20180626.aebd88e-1_amd64.deb ...
Unpacking net-tools (1.60+git20180626.aebd88e-1) ...
Setting up net-tools (1.60+git20180626.aebd88e-1) ...
root@828b1cbb71d6:/# netstat -ntl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:5432            0.0.0.0:*               LISTEN
tcp6       0      0 :::5432                 :::*                    LISTEN

root@828b1cbb71d6:/# apt-get install vim
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  libgpm2 vim-common vim-runtime xxd
Suggested packages:
  gpm ctags vim-doc vim-scripts
The following NEW packages will be installed:
  libgpm2 vim vim-common vim-runtime xxd
0 upgraded, 5 newly installed, 0 to remove and 1 not upgraded.
Need to get 7,425 kB of archives.
After this operation, 33.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://deb.debian.org/debian buster/main amd64 xxd amd64 2:8.1.0875-5 [140 kB]
Get:2 http://deb.debian.org/debian buster/main amd64 vim-common all 2:8.1.0875-5 [195 kB]
Get:3 http://deb.debian.org/debian buster/main amd64 libgpm2 amd64 1.20.7-5 [35.1 kB]
Get:4 http://deb.debian.org/debian buster/main amd64 vim-runtime all 2:8.1.0875-5 [5,775 kB]
Get:5 http://deb.debian.org/debian buster/main amd64 vim amd64 2:8.1.0875-5 [1,280 kB]
Fetched 7,425 kB in 3s (2,660 kB/s)
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously unselected package xxd.
(Reading database ... 11821 files and directories currently installed.)
Preparing to unpack .../xxd_2%3a8.1.0875-5_amd64.deb ...
Unpacking xxd (2:8.1.0875-5) ...
Selecting previously unselected package vim-common.
Preparing to unpack .../vim-common_2%3a8.1.0875-5_all.deb ...
Unpacking vim-common (2:8.1.0875-5) ...
Selecting previously unselected package libgpm2:amd64.
Preparing to unpack .../libgpm2_1.20.7-5_amd64.deb ...
Unpacking libgpm2:amd64 (1.20.7-5) ...
Selecting previously unselected package vim-runtime.
Preparing to unpack .../vim-runtime_2%3a8.1.0875-5_all.deb ...
Adding 'diversion of /usr/share/vim/vim81/doc/help.txt to /usr/share/vim/vim81/doc/help.txt.vim-tiny by vim-runtime'
Adding 'diversion of /usr/share/vim/vim81/doc/tags to /usr/share/vim/vim81/doc/tags.vim-tiny by vim-runtime'
Unpacking vim-runtime (2:8.1.0875-5) ...
Selecting previously unselected package vim.
Preparing to unpack .../vim_2%3a8.1.0875-5_amd64.deb ...
Unpacking vim (2:8.1.0875-5) ...
Setting up libgpm2:amd64 (1.20.7-5) ...
Setting up xxd (2:8.1.0875-5) ...
Setting up vim-common (2:8.1.0875-5) ...
Setting up vim-runtime (2:8.1.0875-5) ...
Setting up vim (2:8.1.0875-5) ...
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/vim (vim) in auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/vimdiff (vimdiff) in auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/rvim (rvim) in auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/rview (rview) in auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/vi (vi) in auto mode
update-alternatives: warning: skip creation of /usr/share/man/da/man1/vi.1.gz because associated file /usr/share/man/da/man1/vim.1.gz (of link group vi) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/de/man1/vi.1.gz because associated file /usr/share/man/de/man1/vim.1.gz (of link group vi) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/fr/man1/vi.1.gz because associated file /usr/share/man/fr/man1/vim.1.gz (of link group vi) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/it/man1/vi.1.gz because associated file /usr/share/man/it/man1/vim.1.gz (of link group vi) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/ja/man1/vi.1.gz because associated file /usr/share/man/ja/man1/vim.1.gz (of link group vi) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/pl/man1/vi.1.gz because associated file /usr/share/man/pl/man1/vim.1.gz (of link group vi) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/ru/man1/vi.1.gz because associated file /usr/share/man/ru/man1/vim.1.gz (of link group vi) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/man1/vi.1.gz because associated file /usr/share/man/man1/vim.1.gz (of link group vi) doesn't exist
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/view (view) in auto mode
update-alternatives: warning: skip creation of /usr/share/man/da/man1/view.1.gz because associated file /usr/share/man/da/man1/vim.1.gz (of link group view) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/de/man1/view.1.gz because associated file /usr/share/man/de/man1/vim.1.gz (of link group view) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/fr/man1/view.1.gz because associated file /usr/share/man/fr/man1/vim.1.gz (of link group view) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/it/man1/view.1.gz because associated file /usr/share/man/it/man1/vim.1.gz (of link group view) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/ja/man1/view.1.gz because associated file /usr/share/man/ja/man1/vim.1.gz (of link group view) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/pl/man1/view.1.gz because associated file /usr/share/man/pl/man1/vim.1.gz (of link group view) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/ru/man1/view.1.gz because associated file /usr/share/man/ru/man1/vim.1.gz (of link group view) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/man1/view.1.gz because associated file /usr/share/man/man1/vim.1.gz (of link group view) doesn't exist
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/ex (ex) in auto mode
update-alternatives: warning: skip creation of /usr/share/man/da/man1/ex.1.gz because associated file /usr/share/man/da/man1/vim.1.gz (of link group ex) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/de/man1/ex.1.gz because associated file /usr/share/man/de/man1/vim.1.gz (of link group ex) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/fr/man1/ex.1.gz because associated file /usr/share/man/fr/man1/vim.1.gz (of link group ex) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/it/man1/ex.1.gz because associated file /usr/share/man/it/man1/vim.1.gz (of link group ex) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/ja/man1/ex.1.gz because associated file /usr/share/man/ja/man1/vim.1.gz (of link group ex) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/pl/man1/ex.1.gz because associated file /usr/share/man/pl/man1/vim.1.gz (of link group ex) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/ru/man1/ex.1.gz because associated file /usr/share/man/ru/man1/vim.1.gz (of link group ex) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/man1/ex.1.gz because associated file /usr/share/man/man1/vim.1.gz (of link group ex) doesn't exist
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/editor (editor) in auto mode
update-alternatives: warning: skip creation of /usr/share/man/da/man1/editor.1.gz because associated file /usr/share/man/da/man1/vim.1.gz (of link group editor) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/de/man1/editor.1.gz because associated file /usr/share/man/de/man1/vim.1.gz (of link group editor) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/fr/man1/editor.1.gz because associated file /usr/share/man/fr/man1/vim.1.gz (of link group editor) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/it/man1/editor.1.gz because associated file /usr/share/man/it/man1/vim.1.gz (of link group editor) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/ja/man1/editor.1.gz because associated file /usr/share/man/ja/man1/vim.1.gz (of link group editor) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/pl/man1/editor.1.gz because associated file /usr/share/man/pl/man1/vim.1.gz (of link group editor) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/ru/man1/editor.1.gz because associated file /usr/share/man/ru/man1/vim.1.gz (of link group editor) doesn't exist
update-alternatives: warning: skip creation of /usr/share/man/man1/editor.1.gz because associated file /usr/share/man/man1/vim.1.gz (of link group editor) doesn't exist
Processing triggers for libc-bin (2.28-10) ...

root@828b1cbb71d6:/# su postgres
postgres@828b1cbb71d6:/$ ls -al
total 92
drwxr-xr-x   1 root root 4096 Jun 21 00:49 .
drwxr-xr-x   1 root root 4096 Jun 21 00:49 ..
drwxr-xr-x   1 root root 4096 Jun 21 00:50 bin
drwxr-xr-x   2 root root 4096 May  2 16:39 boot
drwxr-xr-x   5 root root  340 Jun 21 00:49 dev
drwxr-xr-x   2 root root 4096 May 16 02:41 docker-entrypoint-initdb.d
lrwxrwxrwx   1 root root   34 May 16 02:41 docker-entrypoint.sh -> usr/local/bin/docker-entrypoint.sh
-rwxr-xr-x   1 root root    0 Jun 21 00:49 .dockerenv
drwxr-xr-x   1 root root 4096 Jun 21 00:51 etc
drwxr-xr-x   2 root root 4096 May  2 16:39 home
drwxr-xr-x   1 root root 4096 May 16 02:40 lib
drwxr-xr-x   2 root root 4096 May 14 14:50 lib64
drwxr-xr-x   2 root root 4096 May 14 14:50 media
drwxr-xr-x   2 root root 4096 May 14 14:50 mnt
drwxr-xr-x   2 root root 4096 May 14 14:50 opt
dr-xr-xr-x 133 root root    0 Jun 21 00:49 proc
drwx------   1 root root 4096 May 16 02:40 root
drwxr-xr-x   1 root root 4096 May 16 02:41 run
drwxr-xr-x   1 root root 4096 Jun 21 00:50 sbin
drwxr-xr-x   2 root root 4096 May 14 14:50 srv
dr-xr-xr-x  12 root root    0 Jun 21 00:51 sys
drwxrwxrwt   1 root root 4096 Jun 21 00:51 tmp
drwxr-xr-x   1 root root 4096 May 14 14:50 usr
drwxr-xr-x   1 root root 4096 May 14 14:50 var
postgres@828b1cbb71d6:/$ psql
psql (12.3 (Debian 12.3-1.pgdg100+1))
Type "help" for help.

postgres=# create database testdb
postgres-# create user testuser;
postgres=# create database testdb;
postgres=# grant all privileges on database testdb to testuser;
