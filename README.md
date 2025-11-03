# OverTheWire: Bandit

Copyright © 2025 CopperKoi

> 鉴于题目下方给出了学习提示，本题解不解释命令的用法（才不是我懒！！！）.
> 
> 
> 本题解的大部分注释用以表示回显.
> 

> 标题 $i$ 表示 **Bandit Level $i$ → Level $i+1$ .**
> 
> 
> 利用 `ssh bandit{i}@bandit.labs.overthewire.org -p 2220` ssh.
> 

# -1

---

`bandit0`

# 0

---

```bash
cat readme
```


# 1

---

```bash
cat ./-
```


# 2

---

```bash
cat ./--spaces\ in\ this\ filename--
```


# 3

---

```bash
cd inhere
ls -la
cat ...Hiding-From-You
```


# 4

---

```bash
cd inhere
file ./*
cat ./-file07
```


# 5

---

```bash
cd inhere
find -size 1033c
cat maybehere07/.file2
```


# 6

---

```bash
cd /
find -user bandit7 -group bandit6 -size 33c
cat ./var/lib/dpkg/info/bandit7.password
```


# 7

---

```bash
grep millionth data.txt
```


# 8

---

```bash
sort data.txt | uniq -u
```


# 9

---

```bash
strings data.txt | grep "="
```


# 10

---

```bash
base64 -d data.txt
```


# 11

---

```bash
tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt
```


# 12

从这里开始上强度了.

---

```bash
mktemp -d
#/tmp/tmp.CtgVAsD26q
cp data.txt /tmp/tmp.CtgVAsD26q
xxd -r data.txt > data.bin
file data.bin
#data.bin: gzip compressed data, was "data2.bin", last modified: Tue Oct 14 09:26:06 2025, max compression, from Unix, original size modulo 2^32 564
gzip -d -c data.bin > data1
file data1
#data1: bzip2 compressed data, block size = 900k
bunzip2 -c data1 > data2
file data2
#data2: gzip compressed data, was "data4.bin", last modified: Tue Oct 14 09:26:06 2025, max compression, from Unix, original size modulo 2^32 20480
gzip -d -c data2 > data3
file data3
#data3: POSIX tar archive (GNU)
tar -xf data3
ls
#data1  data2  data3  data5.bin  data.bin  data.txt
file data5.bin
#data5.bin: POSIX tar archive (GNU)
tar -xf data5.bin
ls
#data1  data2  data3  data5.bin  data6.bin  data.bin  data.txt
file data6.bin
#data6.bin: bzip2 compressed data, block size = 900k
bunzip2 -c data6.bin > data7
file data7
#data7: POSIX tar archive (GNU)
tar -xf data7
ls
#data1  data2  data3  data5.bin  data6.bin  data7  data8.bin  data.bin  data.txt
file data8.bin
#data8.bin: gzip compressed data, was "data9.bin", last modified: Tue Oct 14 09:26:06 2025, max compression, from Unix, original size modulo 2^32 49
gzip -d -c data8.bin > data9
file data9
#data9: ASCII text
cat data9
```


# 13

---

```bash
ls
#sshkey.private
exit
	#这里有个小问题，从bandit13连接bandit14会被阻止. 之后的题目也要注意避免这个问题!

scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private ./
chmod 600 ./sshkey.private
	#注意权限问题，之后遇到不再赘述.
	#UGO r+w+x
ssh -i ./sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
#ssh -o StrictHostKeyChecking=no -i ./sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
	#这一条使用 -o 自动接受密钥.

bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
```


# 14

---

```bash
nc localhost 30000
{PwdOf14}
```


# 15

---

```bash
openssl s_client localhost:30001
{PwdOf15}
```


# 16

---

```bash
nmap -sCV localhost -p 31000-32000
```

```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-11-02 13:59 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00011s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT      STATE SERVICE     VERSION
31046/tcp open  echo
31518/tcp open  ssl/echo
|_ssl-date: TLS randomness does not represent time
| ssl-cert: Subject: commonName=SnakeOil
| Not valid before: 2024-06-10T03:59:50
|_Not valid after:  2034-06-08T03:59:50
31691/tcp open  echo
31790/tcp open  ssl/unknown
|_ssl-date: TLS randomness does not represent time
| ssl-cert: Subject: commonName=SnakeOil
| Not valid before: 2024-06-10T03:59:50
|_Not valid after:  2034-06-08T03:59:50
| fingerprint-strings: 
|   FourOhFourRequest, GenericLines, GetRequest, HTTPOptions, Help, LPDString, RTSPRequest, SIPOptions: 
|_    Wrong! Please enter the correct current password.
31960/tcp open  echo
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port31790-TCP:V=7.94SVN%T=SSL%I=7%D=11/2%Time=690763C7%P=x86_64-pc-linu
SF:x-gnu%r(GenericLines,32,"Wrong!\x20Please\x20enter\x20the\x20correct\x2
SF:0current\x20password\.\n")%r(GetRequest,32,"Wrong!\x20Please\x20enter\x
SF:20the\x20correct\x20current\x20password\.\n")%r(HTTPOptions,32,"Wrong!\
SF:x20Please\x20enter\x20the\x20correct\x20current\x20password\.\n")%r(RTS
SF:PRequest,32,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x20
SF:password\.\n")%r(Help,32,"Wrong!\x20Please\x20enter\x20the\x20correct\x
SF:20current\x20password\.\n")%r(FourOhFourRequest,32,"Wrong!\x20Please\x2
SF:0enter\x20the\x20correct\x20current\x20password\.\n")%r(LPDString,32,"W
SF:rong!\x20Please\x20enter\x20the\x20correct\x20current\x20password\.\n")
SF:%r(SIPOptions,32,"Wrong!\x20Please\x20enter\x20the\x20correct\x20curren
SF:t\x20password\.\n");

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 144.55 seconds

```

```bash
openssl s_client -connect localhost:31790 -ign_eof
	#不使用 -ign_eof 会导致 s_client 从标准输入读到 EOF 后就关闭 TLS，因此收不到响应.
```

```
-----BEGIN RSA PRIVATE KEY-----
***
-----END RSA PRIVATE KEY-----
```

```bash
vim pwd
#把 RSA 密钥写进去.
ssh -i ./pwd bandit17@bandit.labs.overthewire.org -p 2220

bandit17@bandit:~$ cat /etc/bandit_pass/bandit17
```


# 17

---

```bash
diff passwords.new passwords.old
```


# 18

---

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"
{PwdOf18}
```


# 19

---

```bash
ls -la
```

```
total 36
drwxr-xr-x   2 root     root      4096 Oct 14 09:26 .
drwxr-xr-x 150 root     root      4096 Oct 14 09:29 ..
-rwsr-x---   1 bandit20 bandit19 14884 Oct 14 09:26 bandit20-do
-rw-r--r--   1 root     root       220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root     root      3851 Oct 14 09:19 .bashrc
-rw-r--r--   1 root     root       807 Mar 31  2024 .profile
```

```bash
./bandit20-do
#Run a command as another user.
#  Example: ./bandit20-do whoami
./bandit20-do cat /etc/bandit_pass/bandit20
```


# 20

---

```bash
ls -la
```

```
total 36
drwxr-xr-x   2 root     root      4096 Oct 14 09:26 .
drwxr-xr-x 150 root     root      4096 Oct 14 09:29 ..
-rw-r--r--   1 root     root       220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root     root      3851 Oct 14 09:19 .bashrc
-rw-r--r--   1 root     root       807 Mar 31  2024 .profile
-rwsr-x---   1 bandit21 bandit20 15608 Oct 14 09:26 suconnect
```

```bash
./suconnect
#Usage: ./suconnect <portnumber>
#This program will connect to the given port on localhost using TCP. If it receives the correct password from the other side, the next password is transmitted back.

#再弹一个 shell.
nc -lvp 4444

#回到原先的 shell.
./suconnect 4444

#这时候新的 shell 监听到了.
#Connection received on localhost 43602
{PwdOf20}
```


# 21

---

```bash
ls -la /etc/cron.d
```

```
total 60
drwxr-xr-x   2 root root  4096 Oct 14 09:29 .
drwxr-xr-x 128 root root 12288 Oct 20 16:35 ..
-r--r-----   1 root root    47 Oct 14 09:26 behemoth4_cleanup
-rw-r--r--   1 root root   123 Oct 14 09:19 clean_tmp
-rw-r--r--   1 root root   120 Oct 14 09:26 cronjob_bandit22
-rw-r--r--   1 root root   122 Oct 14 09:26 cronjob_bandit23
-rw-r--r--   1 root root   120 Oct 14 09:26 cronjob_bandit24
-rw-r--r--   1 root root   201 Apr  8  2024 e2scrub_all
-r--r-----   1 root root    48 Oct 14 09:27 leviathan5_cleanup
-rw-------   1 root root   138 Oct 14 09:28 manpage3_resetpw_job
-rwx------   1 root root    52 Oct 14 09:29 otw-tmp-dir
-rw-r--r--   1 root root   102 Mar 31  2024 .placeholder
-rw-r--r--   1 root root   396 Jan  9  2024 sysstat
```

```bash
cat /etc/cron.d/cronjob_bandit22
#@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
#* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
cat /usr/bin/cronjob_bandit22.sh
```

```bash
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

```bash
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```


# 22

---

```bash
cat /usr/bin/cronjob_bandit23.sh
```

```bash
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```

```bash
echo I am user bandit23 | md5sum | cut -d ' ' -f 1
#-d ' '
	#设置分隔符为空格
#-f 1
	#只取第一个字段（即MD5哈希值本身）
#8ca319486bfbbc3663ea0fbe81326349
cat /tmp/8ca319486bfbbc3663ea0fbe81326349
```


# 23

---

## 非预期

我们用 22 的方法，可以通过 `cronjob_bandit23.sh` 得到 24 密码.


## 预期

```bash
cat /usr/bin/cronjob_bandit24.sh
```

```bash
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```

```bash
cd /tmp
#主目录没有权限
vim pwd.sh
```

```bash
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/pwd
```

```bash
chmod 777 pwd.sh
cp pwd.sh /var/spool/bandit24/foo
cat /tmp/pwd
```


# 24

---

```bash
for i in {0000..9999}; do echo "{PwdOf24} $i"; done | nc localhost 30002 | grep -v "^Wrong!" > /tmp/pwd
```

> 这个空格非常恶心！
> 

```bash
cat /tmp/pwd
```


# 25

---

```bash
ls
#bandit26.sshkey
scp -P 2220 bandit25@bandit.labs.overthewire.org:bandit26.sshkey ./
grep bandit26 /etc/passwd
#bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
cat /usr/bin/showtext
```

```bash
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
```

我们利用 `more` 的一个小 trick，只需要让 `text.txt` 显示不全就不会执行 `exit 0` .

把终端拉扁再 ssh.

```bash
ssh -i ./bandit26.sshkey bandit26@bandit.labs.overthewire.org -p 2220
```

按 `V` 进入 vim，可以

```bash
:set shell=/bin/bash
:shell
```

获得一个 shell 后执行 `cat /etc/bandit_pass/bandit26` .

当然，直接在 vim 读取也是可行的.

```bash
:ex! /etc/bandit_pass/bandit26
#or
:r /etc/bandit_pass/bandit26
```


# 26

---

通过 25 的手段获得一个 shell.

```bash
ls -la
```

```
total 44                                                                                                                                                                                                                                    
drwxr-xr-x   3 root     root      4096 Oct 14 09:26 .                                                                                                                                                                                       
drwxr-xr-x 150 root     root      4096 Oct 14 09:29 ..                                                                                                                                                                                      
-rwsr-x---   1 bandit27 bandit26 14884 Oct 14 09:26 bandit27-do                                                                                                                                                                             
-rw-r--r--   1 root     root       220 Mar 31  2024 .bash_logout                                                                                                                                                                            
-rw-r--r--   1 root     root      3851 Oct 14 09:19 .bashrc                                                                                                                                                                                 
-rw-r--r--   1 root     root       807 Mar 31  2024 .profile                                                                                                                                                                                
drwxr-xr-x   2 root     root      4096 Oct 14 09:26 .ssh                                                                                                                                                                                    
-rw-r-----   1 bandit26 bandit26   258 Oct 14 09:26 text.txt
```

```bash
./bandit27-do cat /etc/bandit_pass/bandit27
```


# 27

接下来考察 git.

---

和13相同的问题，我们不要 ssh，在本地做.

```bash
git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
cd repo
ls -la
```

```
total 16
drwxrwxr-x 3 kali kali 4096 11月 3日 18:47 .
drwxr-xr-x 3 kali kali 4096 11月 3日 18:46 ..
drwxrwxr-x 7 kali kali 4096 11月 3日 18:47 .git
-rw-rw-r-- 1 kali kali   68 11月 3日 18:47 README
```

```bash
cat README
```


# 28

---

```bash
git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo
cd repo
ls -la
```

```
total 16
drwxrwxr-x 3 kali kali 4096 11月 3日 18:55 .
drwxr-xr-x 3 kali kali 4096 11月 3日 18:55 ..
drwxrwxr-x 7 kali kali 4096 11月 3日 18:55 .git
-rw-rw-r-- 1 kali kali  111 11月 3日 18:55 README.md
```

```bash
cat README.md
```

```
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx
```

```bash
git log
```

```
commit b5ed4b5a3499533c2611217c8780e8ead48609f6 (**HEAD** -> **master**, **origin/master**, **origin/HEAD**)
Author: Morla Porla <morla@overthewire.org>
Date:   Tue Oct 14 09:26:24 2025 +0000

    fix info leak

commit 8b7c651b37ce7a94633b7b7b7c980ded19a16e4f
Author: Morla Porla <morla@overthewire.org>
Date:   Tue Oct 14 09:26:24 2025 +0000

    add missing data

commit 6d8e5e607602b597ade7504a550a29ba03f2cca0
Author: Ben Dover <noone@overthewire.org>
Date:   Tue Oct 14 09:26:24 2025 +0000

    initial commit of README.md
```

```bash
git show 8b7c651b37ce7a94633b7b7b7c980ded19a16e4f
```


# 29

---

```bash
git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
cd repo
ls -la
```

```
total 16
drwxrwxr-x 3 kali kali 4096 11月 3日 19:08 .
drwxr-xr-x 3 kali kali 4096 11月 3日 19:08 ..
drwxrwxr-x 7 kali kali 4096 11月 3日 19:08 .git
-rw-rw-r-- 1 kali kali  131 11月 3日 19:08 README.md
```

```bash
cat README.md
```

```
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>
```

```bash
git branch -a                                                                       
```

```
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
```

```bash
git checkout remotes/origin/dev
```

```
commit e50e6cc6be6bc718f834b1584971b1039e4e87db (**HEAD**, **origin/dev**, **dev**)
Author: Morla Porla <morla@overthewire.org>
Date:   Tue Oct 14 09:26:26 2025 +0000

    add data needed for development

commit a3b6378aa0d0088c60b8854d0d20f46aabd466bc
Author: Ben Dover <noone@overthewire.org>
Date:   Tue Oct 14 09:26:26 2025 +0000

    add gif2ascii

commit 8ff4dfab0a869265c3cd59719c5101098e2279ed (**origin/master**, **origin/HEAD**, **master**)
Author: Ben Dover <noone@overthewire.org>
Date:   Tue Oct 14 09:26:26 2025 +0000

    fix username

commit 09300a1ee84da9a017084bc0723c2e0de4a12584
Author: Ben Dover <noone@overthewire.org>
Date:   Tue Oct 14 09:26:26 2025 +0000

    initial commit of README.md
```

```bash
git show e50e6cc6be6bc718f834b1584971b1039e4e87db
```


# 30

---

```bash
git clone ssh://bandit30-git@bandit.labs.overthewire.org:2220/home/bandit30-git/repo
cd repo
ls -la
```

```
total 16
drwxrwxr-x 3 kali kali 4096 11月 3日 19:20 .
drwxr-xr-x 3 kali kali 4096 11月 3日 19:20 ..
drwxrwxr-x 7 kali kali 4096 11月 3日 19:20 .git
-rw-rw-r-- 1 kali kali   30 11月 3日 19:20 README.md
```

```bash
cat README.md
#just an epmty file... muahaha
git tag                                                                             
#secret                                                                                                                                                                                                                                                                                                   
git show secret                                  
```


# 31

---

```bash
#这题本地没有权限 git push，所以我们把仓库下载在本地再传上去.
mkdir /tmp/copperkoi
```

```bash
git clone ssh://bandit31-git@bandit.labs.overthewire.org:2220/home/bandit31-git/repo
scp -P 2220 -r repo/ bandit31@bandit.labs.overthewire.org:/tmp/copperkoi
```

```bash
cd /tmp/copperkoi/repo
ls -la
```

```
total 20
drwxrwxr-x 3 kali kali 4096 11月 3日 19:24 .
drwxr-xr-x 3 kali kali 4096 11月 3日 19:24 ..
drwxrwxr-x 7 kali kali 4096 11月 3日 19:24 .git
-rw-rw-r-- 1 kali kali    6 11月 3日 19:24 .gitignore
-rw-rw-r-- 1 kali kali  147 11月 3日 19:24 README.md
```

```bash
cat README.md
```

```
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
```

```bash
cat .gitignore
*.txt
rm .gitignore
echo 'May I come in?' >> key.txt
git config --global user.email "exp@exp.com"
git config --global user.name "copperkoi"
git commit -a
git push origin master
```


# 32

“After all this `git` stuff, it’s time for another escape.”

---

我们发现这个 `UPPERCASE SHELL` 几乎执行不了什么命令，因此我们 `$0` 创建一个正常的 shell.

```bash
cat /etc/bandit_pass/bandit33
```


# 33

---

> **At this moment, level 34 does not exist yet.**
> 

# 如何查看之前的密码？

```bash
ls /etc/bandit_pass
```

```
bandit0  bandit10  bandit12  bandit14  bandit16  bandit18  bandit2   bandit21  bandit23  bandit25  bandit27  bandit29  bandit30  bandit32  bandit4  bandit6  bandit8
bandit1  bandit11  bandit13  bandit15  bandit17  bandit19  bandit20  bandit22  bandit24  bandit26  bandit28  bandit3   bandit31  bandit33  bandit5  bandit7  bandit9
```

```bash
cat /etc/bandit_pass/banditi
#i < 当前用户.
```
