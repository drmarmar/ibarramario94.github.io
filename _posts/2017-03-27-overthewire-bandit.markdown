---
title: "Overthewire Bandit Writeup"
layout: post
date: 2017-03-27 20:30
image: /assets/images/markdown.jpg
headerImage: false
tag:
- writeup
- wargame
star: true
category: blog
author: marioibarra
description: Overthewire Bandit Lvls 1-23
---

## Intro
Bandit is a wargame that is often the starting point for beginners. It gives you a chance to learn the basics of getting around a linux OS
### Lvl 0-1
In the very first level you simply use the _ls_ command to view files in the specified directory. You also use the _cat_ command to read files.


<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit0@melissa:~$ </span>ls
readme
<span style="color:red">bandit0@melissa:~$ </span>cat readme</code></pre></figure>


### Lvl 1-2
<p>The password is stored in a file called <b>-</b> so we must locate it and read it. Since its a special character, we must use cat with the directory indicator.</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit1@melissa:~$ </span>ls
-
<span style="color:red">bandit1@melissa:~$ </span>cat ~/-</code></pre></figure>

### Lvl 2-3
<p>The password is located in a file called <b>spaces in this filename</b> so we located it with <i>ls</i> and because there are spaces in the file name we must read it as such: <i>cat spaces\ in\ this\ filename</i></p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit2@melissa:~$ </span>ls
spaces in this filename
<span style="color:red">bandit2@melissa:~$ </span>cat spaces\ in\ this\ filename</code></pre></figure>

### Lvl 3-4
<p>The password file was in a hidden directory so we had to use <i>ls -al</i> to list all files in the directory.</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit3@melissa:~$ </span>ls -al
drwxr-xr-x 3 root root 4096 Nov 14 2014 .
drwxr-xr-x 172 root root 4096 Jul 10 2016 ..
-rw-r--r-- 1 root root 220 Apr 9 2014 .bash_logout
-rw-r--r-- 1 root root 3637 Apr 9 2014 .bashrc
-rw-r--r-- 1 root root 675 Apr 9 2014 .profile
drwxr-xr-x 2 root root 4096 Nov 14 2014 inhere
<span style="color:red">bandit3@melissa:~$ </span>cd inhere
<span style="color:red">bandit3@melissa:~/inhere$ </span>ls -al
drwxr-xr-x 2 root root 4096 Nov 14 2014 .
drwxr-xr-x 3 root root 4096 Nov 14 2014 ..
-rw-r----- 1 bandit4 bandit3 33 Nov 14 2014 .hidden
<span style="color:red">bandit3@melissa:~/inhere$ </span>cat .hidden</code></pre></figure>

### Lvl 4-5
<p>Within the inhere directory the password is stored in the only human-readable file. I used the <i>file</i> command to display the file data types and locate the password.</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit4@melissa:~$ </span>ls
inhere
<span style="color:red">bandit4@melissa:~$ </span>file inhere/*
inhere/-file00: data
inhere/-file01: data
inhere/-file02: data
inhere/-file03: data
inhere/-file04: data
inhere/-file05: data
inhere/-file06: data
inhere/-file07: ASCII text
inhere/-file08: data
inhere/-file09: data
<span style="color:red">bandit4@melinda:~$</span> cat inhere/-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
</code></pre></figure>


### Lvl 5-6
<p>Within the inhere directory the password is stored in the only human-readable file. I used the <i>file</i> command to display the file data types and locate the password.</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit5@melissa:~$ </span>ls
<span style="color:blue">inhere</span>
<span style="color:red">bandit5@melinda:~$</span> ls
inhere
<span style="color:red">bandit5@melinda:~$</span> cd inhere/
<span style="color:red">bandit5@melinda:~/inhere$</span> ls -al
total 88
drwxr-x--- 22 root bandit5 4096 Nov 14  2014 .
drwxr-xr-x  3 root root    4096 Nov 14  2014 ..
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere00</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere01</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere02</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere03</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere04</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere05</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere06</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere07</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere08</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere09</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere10</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere11</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere12</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere13</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere14</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere15</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere16</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere17</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere18</span>
drwxr-x---  2 root bandit5 4096 Nov 14  2014 <span style="color:blue">maybehere19</span>
<span style="color:red">bandit5@melinda:~/inhere$</span> find . -size 1033c -readable ! -executable
./maybehere07/.file2
<span style="color:red">bandit5@melinda:~/inhere$</span>
</code></pre></figure>

### Lvl 6-7
<p>The file is somewhere on the server so I used <i>find</i> and filtered the STDERR output by sending it to <i>/dev/null</i>. As a result, only the successful results are displayed.</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit6@melinda:~$</span> find / -size 33c -user bandit7 -group bandit6 2>/dev/null
/var/lib/dpkg/info/bandit7.password
<span style="color:red">bandit6@melinda:~$</span> cat /var/lib/dpkg/info/bandit7.password
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
</code></pre></figure>

### Lvl 7-8
<p>The password is stored next to the word 'millionth' in the data.txt file.</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit7@melinda:~$</span> cat data.txt | grep "millionth"
<span style="color:orange">millionth</span>       cvX2JJa4CFALtqS87jk27qwqGhBM9plV
<span style="color:red">bandit7@melinda:~$</span></code></pre></figure>

### Lvl 8-9
<p>The password is the only line of text that occurs once in data.txt. A simple <i>pipe</i> of <i>cat</i>, <i>sort</i>, and <i>uniq</i> will do the job.</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit8@melinda:~$</span> cat data.txt | sort | uniq -u
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
<span style="color:red">bandit8@melinda:~$ </span></code></pre></figure>

### Lvl 9-10
<p>"The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several ‘=’ characters"</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit9@melinda:~$</span> strings data.txt | grep "=="
I<span style="color:orange">==========</span> the6
<span style="color:orange">==========</span> password
<span style="color:orange">==========</span> ism
<span style="color:orange">==========</span> truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
<span style="color:red">bandit9@melinda:~$ </span></code></pre></figure>

### Lvl 10-11
<p>'The password for the next level is stored in the file data.txt, which contains base64 encoded data'</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit10@melinda:~$</span> base64 -d data.txt
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
</code></pre></figure>

### Lvl 11-12
<p>'The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions'</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit11@melinda:~$</span> tr a-zA-Z n-za-mN-ZA-M < data.txt
The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
</code></pre></figure>

### Lvl 12-13
<p>"The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv"</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit12@melinda:~$</span> mkdir /tmp/mario
<span style="color:red">bandit12@melinda:~$</span> cd /tmp/mario
<span style="color:red">bandit12@melinda:~$</span> cp /home/bandit12/data.txt ./
<span style="color:red">bandit12@melinda:~$</span> xxd -r data.txt > d1 | file d1
d1: gzip compressed data, was "data2.bin", from Unix, last modified: Fri Nov 14 10:32:20 2014, max compression
<span style="color:red">bandit12@melinda:/tmp/mario$</span> mv d1 d1.gz && gzip -d d1.gz
<span style="color:red">bandit12@melinda:~$</span> file d1
d1: bzip2 compressed data, block size = 900k
<span style="color:red">bandit12@melinda:~$</span> bzip2 -d d1
bzip2: Can't guess original name for d1 -- using d1.out
<span style="color:red">bandit12@melinda:/tmp/mario$</span> file d1.out
d1.out: gzip compressed data, was "data4.bin", from Unix, last modified: Fri Nov 14 10:32:20 2014, max compression
<span style="color:red">bandit12@melinda:/tmp/mario$</span> mv d1.out d1.gz && gzip -d d1.gz | file d1
d1: POSIX tar archive (GNU)
<span style="color:red">bandit12@melinda:/tmp/mario$</span> tar -xvf d1
data5.bin
<span style="color:red">bandit12@melinda:/tmp/mario$</span> file data5.bin
data5.bin: POSIX tar archive (GNU)
<span style="color:red">bandit12@melinda:/tmp/mario$</span> tar -xvf data5.bin
data6.bin
<span style="color:red">bandit12@melinda:/tmp/mario$</span> file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
<span style="color:red">bandit12@melinda:/tmp/mario$</span> bzip2 -d data6.bin
bzip2: Can't guess original name for data6.bin -- using data6.bin.out
<span style="color:red">bandit12@melinda:/tmp/mario$</span> file data6.bin.out
data6.bin.out: POSIX tar archive (GNU)
<span style="color:red">bandit12@melinda:/tmp/mario$</span> tar -xvf data6.bin.out
data8.bin
<span style="color:red">bandit12@melinda:/tmp/mario$</span> mv data8.bin data8.gz && gzip -d data8.gz
<span style="color:red">bandit12@melinda:/tmp/mario$</span> file data8
data8: ASCII text
<span style="color:red">bandit12@melinda:/tmp/mario$</span> cat data8
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
</code></pre></figure>

### Lvl 13-14
<p>'The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on'</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit13@melinda:~$</span> ls
sshkey.private
<span style="color:red">bandit13@melinda:~$</span> ssh -i sshkey.private bandit14@localhost
Could not create directory '/home/bandit13/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is 05:3a:1c:25:35:0a:ed:2f:cd:87:1c:f6:fe:69:e4:f6.
Are you sure you want to continue connecting (yes/no)? yes

<span style="color:red">bandit14@melinda:~$</span> cat /etc/bandit_pass/bandit14
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
</code></pre></figure>

### Lvl 14-15
<p>'The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.'</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit14@melinda:~$</span> echo '4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e' | nc localhost 30000Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr
</code></pre></figure>

### Lvl 15-16
<p>'The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.'</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit15@melinda:~$</span> openssl s_client -ign_eof -connect localhost:30001
CONNECTED(00000003)
depth=0 CN = li190-250.members.linode.com
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = li190-250.members.linode.com
verify return:1
---
Certificate chain
 0 s:/CN=li190-250.members.linode.com
   i:/CN=li190-250.members.linode.com
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIC3jCCAcagAwIBAgIJAI5QiWZw4YHbMA0GCSqGSIb3DQEBCwUAMCcxJTAjBgNV
BAMTHGxpMTkwLTI1MC5tZW1iZXJzLmxpbm9kZS5jb20wHhcNMTQxMTE0MTAyODA0
WhcNMjQxMTExMTAyODA0WjAnMSUwIwYDVQQDExxsaTE5MC0yNTAubWVtYmVycy5s
aW5vZGUuY29tMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAsKmy9o5z
WU+1EH7Z3bB5TGQA+16zXDcEJy6tZWZ8CDrRyQXiahendp45BWUc/ZuLDo0+B3Wt
ZXjofmLw/F4fmR+8X1s1fQZX2dFt920qEm7LxqzWd0c7FdHiBwwRrwhkk+3cQpOB
TTGdLWEgpdmwwNZDTUdsDLzjDczPnju6T6p6ArTECztPbmTjfY4QIRtC6capL1Z+
yPJSQVAuAMEX1wTDWTGdm0VV7oW4F5cGZutf6QAP51jdhSyZuGilIPHbnj0l6Qc7
a7+OtEsEGi31aJ8KpRf7LNZ7DXCuoB3Hf75Pd6VjDgoOIagcH0NYqa75gEjBkGzs
ktLWykT7ag7fKwIDAQABow0wCzAJBgNVHRMEAjAAMA0GCSqGSIb3DQEBCwUAA4IB
AQCaZdUNAj8WDEKWdoU3LNXUBJlTJwiWBrh550PbHSQORcCz2K0kiMei1A4ojK2N
dMHFGAqAeUEaxtz92p2BoFpZasAtdSa3u63tBckFhfUolIS1TC7Cj51y19ysTeep
fGPFpuPCVqVPsruei8Z/iqn3bFIhQQdmumeePZQdPMwZSWHNVYC5XODd7PvNDrDu
5MZJjkz4+6LbwwAvyew62meFN2QEsYbK2Brtbhze+IjE27FGWlSw4K3jlwa409MD
MTf4JU41ELaYY8G/LSNDJsBVhhkHzvXR9iCbXxNz3IL0dQDNj7h4LKhBy0q7hvqg
kDzwlmBO4WKSmCAuky44cXmd
-----END CERTIFICATE-----
subject=/CN=li190-250.members.linode.com
issuer=/CN=li190-250.members.linode.com
---
No client certificate CA names sent
---
SSL handshake has read 1714 bytes and written 637 bytes
---
New, TLSv1/SSLv3, Cipher is DHE-RSA-AES256-SHA
Server public key is 2048 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : SSLv3
    Cipher    : DHE-RSA-AES256-SHA
    Session-ID: 5FF52BC376690852AAB74A7AF1019C75CA4DC769EDEEEE901889EDFD8E4AB23E
    Session-ID-ctx:
    Master-Key: F9F0D2B2D75B33339DE861F178346C255780ADC3D921701421E13AE63E66BF55EEEB633BC53528FC124335BBF51E6304
    Key-Arg   : None
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    Start Time: 1493709386
    Timeout   : 300 (sec)
    Verify return code: 18 (self signed certificate)
---
BfMYroe26WYalil77FoDi9qh59eK5xNr
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd

read:errno=0
</code></pre></figure>
<p>We used -ign_eof to bypass "HEARTBEATING" and "read R BLOCK"</p>

### Lvl 16-17
<p>'The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.'</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit16@melinda:~$</span> nmap -sV -p 31000-32000 localhost

Starting Nmap 6.40 ( http://nmap.org ) at 2017-05-02 07:22 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00027s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE VERSION
31046/tcp open  echo
31518/tcp open  msdtc   Microsoft Distributed Transaction Coordinator (error)
31691/tcp open  echo
31790/tcp open  msdtc   Microsoft Distributed Transaction Coordinator (error)
31960/tcp open  echo
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 41.20 seconds

<span style="color:red">bandit16@melinda:~$</span> openssl s_client -connect localhost:31518
CONNECTED(00000003)
depth=0 CN = li190-250.members.linode.com
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = li190-250.members.linode.com
verify return:1
---
Certificate chain
 0 s:/CN=li190-250.members.linode.com
   i:/CN=li190-250.members.linode.com
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIC3jCCAcagAwIBAgIJAI5QiWZw4YHbMA0GCSqGSIb3DQEBCwUAMCcxJTAjBgNV
BAMTHGxpMTkwLTI1MC5tZW1iZXJzLmxpbm9kZS5jb20wHhcNMTQxMTE0MTAyODA0
WhcNMjQxMTExMTAyODA0WjAnMSUwIwYDVQQDExxsaTE5MC0yNTAubWVtYmVycy5s
aW5vZGUuY29tMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAsKmy9o5z
WU+1EH7Z3bB5TGQA+16zXDcEJy6tZWZ8CDrRyQXiahendp45BWUc/ZuLDo0+B3Wt
ZXjofmLw/F4fmR+8X1s1fQZX2dFt920qEm7LxqzWd0c7FdHiBwwRrwhkk+3cQpOB
TTGdLWEgpdmwwNZDTUdsDLzjDczPnju6T6p6ArTECztPbmTjfY4QIRtC6capL1Z+
yPJSQVAuAMEX1wTDWTGdm0VV7oW4F5cGZutf6QAP51jdhSyZuGilIPHbnj0l6Qc7
a7+OtEsEGi31aJ8KpRf7LNZ7DXCuoB3Hf75Pd6VjDgoOIagcH0NYqa75gEjBkGzs
ktLWykT7ag7fKwIDAQABow0wCzAJBgNVHRMEAjAAMA0GCSqGSIb3DQEBCwUAA4IB
AQCaZdUNAj8WDEKWdoU3LNXUBJlTJwiWBrh550PbHSQORcCz2K0kiMei1A4ojK2N
dMHFGAqAeUEaxtz92p2BoFpZasAtdSa3u63tBckFhfUolIS1TC7Cj51y19ysTeep
fGPFpuPCVqVPsruei8Z/iqn3bFIhQQdmumeePZQdPMwZSWHNVYC5XODd7PvNDrDu
5MZJjkz4+6LbwwAvyew62meFN2QEsYbK2Brtbhze+IjE27FGWlSw4K3jlwa409MD
MTf4JU41ELaYY8G/LSNDJsBVhhkHzvXR9iCbXxNz3IL0dQDNj7h4LKhBy0q7hvqg
kDzwlmBO4WKSmCAuky44cXmd
-----END CERTIFICATE-----
subject=/CN=li190-250.members.linode.com
issuer=/CN=li190-250.members.linode.com
---
No client certificate CA names sent
---
SSL handshake has read 1714 bytes and written 637 bytes
---
New, TLSv1/SSLv3, Cipher is DHE-RSA-AES256-SHA
Server public key is 2048 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : SSLv3
    Cipher    : DHE-RSA-AES256-SHA
    Session-ID: F95A1961737CC6B01F63693D62DF94467C65A217AD7D53906BCFC1EABA3F1C97
    Session-ID-ctx:
    Master-Key: C668277C716D1501AF29B517E4D1A28BCE7EDDF5C79B9C68A2D44CFE4796EB455AD9C4F444D24A7618A0D3E796D69E30
    Key-Arg   : None
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    Start Time: 1493710060
    Timeout   : 300 (sec)
    Verify return code: 18 (self signed certificate)
---
cluFn7wTiGryunymYOu4RcffSxQluehd
cluFn7wTiGryunymYOu4RcffSxQluehd

<span style="color:red">bandit16@melinda:~$</span> openssl s_client -connect localhost:31790
CONNECTED(00000003)
depth=0 CN = li190-250.members.linode.com
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = li190-250.members.linode.com
verify return:1
---
Certificate chain
 0 s:/CN=li190-250.members.linode.com
   i:/CN=li190-250.members.linode.com
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIC3jCCAcagAwIBAgIJAI5QiWZw4YHbMA0GCSqGSIb3DQEBCwUAMCcxJTAjBgNV
BAMTHGxpMTkwLTI1MC5tZW1iZXJzLmxpbm9kZS5jb20wHhcNMTQxMTE0MTAyODA0
WhcNMjQxMTExMTAyODA0WjAnMSUwIwYDVQQDExxsaTE5MC0yNTAubWVtYmVycy5s
aW5vZGUuY29tMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAsKmy9o5z
WU+1EH7Z3bB5TGQA+16zXDcEJy6tZWZ8CDrRyQXiahendp45BWUc/ZuLDo0+B3Wt
ZXjofmLw/F4fmR+8X1s1fQZX2dFt920qEm7LxqzWd0c7FdHiBwwRrwhkk+3cQpOB
TTGdLWEgpdmwwNZDTUdsDLzjDczPnju6T6p6ArTECztPbmTjfY4QIRtC6capL1Z+
yPJSQVAuAMEX1wTDWTGdm0VV7oW4F5cGZutf6QAP51jdhSyZuGilIPHbnj0l6Qc7
a7+OtEsEGi31aJ8KpRf7LNZ7DXCuoB3Hf75Pd6VjDgoOIagcH0NYqa75gEjBkGzs
ktLWykT7ag7fKwIDAQABow0wCzAJBgNVHRMEAjAAMA0GCSqGSIb3DQEBCwUAA4IB
AQCaZdUNAj8WDEKWdoU3LNXUBJlTJwiWBrh550PbHSQORcCz2K0kiMei1A4ojK2N
dMHFGAqAeUEaxtz92p2BoFpZasAtdSa3u63tBckFhfUolIS1TC7Cj51y19ysTeep
fGPFpuPCVqVPsruei8Z/iqn3bFIhQQdmumeePZQdPMwZSWHNVYC5XODd7PvNDrDu
5MZJjkz4+6LbwwAvyew62meFN2QEsYbK2Brtbhze+IjE27FGWlSw4K3jlwa409MD
MTf4JU41ELaYY8G/LSNDJsBVhhkHzvXR9iCbXxNz3IL0dQDNj7h4LKhBy0q7hvqg
kDzwlmBO4WKSmCAuky44cXmd
-----END CERTIFICATE-----
subject=/CN=li190-250.members.linode.com
issuer=/CN=li190-250.members.linode.com
---
No client certificate CA names sent
---
SSL handshake has read 1714 bytes and written 637 bytes
---
New, TLSv1/SSLv3, Cipher is DHE-RSA-AES256-SHA
Server public key is 2048 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : SSLv3
    Cipher    : DHE-RSA-AES256-SHA
    Session-ID: 08EDF6C0875162325755219F73225528C2550355101C7FF3333247A105BDD79F
    Session-ID-ctx:
    Master-Key: 2FD99FF8C31F14D1780A7D7136E42E253E6E15AD9975294F54B27BDF9E06CCEE04DC339E80B41D084E060A748A225223
    Key-Arg   : None
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    Start Time: 1493710105
    Timeout   : 300 (sec)
    Verify return code: 18 (self signed certificate)
---
cluFn7wTiGryunymYOu4RcffSxQluehd
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

read:errno=0
<span style="color:red">bandit16@melinda:~$</span> mkdir /tmp/key
mkdir: cannot create directory '/tmp/key': File exists
<span style="color:red">bandit16@melinda:~$</span> cd /tmp/key
<span style="color:red">bandit16@melinda:/tmp/key$</span> touch sshkey.private
<span style="color:red">bandit16@melinda:/tmp/key$</span> vim sshkey.private
<span style="color:red">bandit16@melinda:/tmp/key$</span> ssh -i sshkey.private bandit17@localhost
Could not create directory '/home/bandit16/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is 05:3a:1c:25:35:0a:ed:2f:cd:87:1c:f6:fe:69:e4:f6.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit16/.ssh/known_hosts).
</code></pre></figure>
<p>The echo ports aren't what we're looking for so we try to connect to port 31518 and 31790.</p>

### Lvl 17-18
<p>'There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new'</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit17@melinda:~$</span> diff passwords.new passwords.old
42c42
 kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
---
 BS8bqB1kqkinKJjuxL6k072Qq9NRwQpR
</code></pre></figure>
<p>We want the top password because that's the one from the passwords.new file.</p>

<h3>Lvl 18-19</h3>
<p>'The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.'</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash">
<span style="color:red"> $</span>ssh -t bandit18@bandit.labs.overthewire.org bash --norc

This is the OverTheWire game server. More information on http://www.overthewire.org/wargames

Please note that wargame usernames are no longer level<X>, but wargamename<X>
e.g. vortex4, semtex2, ...

Note: at this moment, blacksun is not available.

bandit18@bandit.labs.overthewire.org's password:
<span style="color:red">bash-4.3$</span> ls
readme
<span style="color:red">bash-4.3$</span> cat readme
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
</code></pre></figure>

### Lvl 19-20
<p>'To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.'</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit19@melinda:~$</span> ./bandit20-do cat /etc/bandit_pass/bandit20
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
</code></pre></figure>

<h3>Lvl 20-21</h3>
<p>'There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21)..'</p>

<p>We'll need to ssh to bandit20 on two shells. On the first shell, we must listen on a certain port and run suconnect on shell 2 using the same port. Send the current password of the level in the first shell to receive the password for level 21.</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit20@melinda:~$</span> ls
suconnect
<span style="color:red">bandit20@melinda:~$</span> ./suconnect
Usage: ./suconnect < portnumber >
This program will connect to the given port on localhost using TCP. If it receives the correct password from the other side, the next password is transmitted back.
</code></pre></figure>

<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit20@melinda:~$</span> nc -l 30050
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
</code></pre></figure>

<h3>Lvl 21-22</h3>
<p>'A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.'</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit21@melinda:~$</span> cd /etc/cron.d
<span style="color:red">bandit21@melinda:/etc/cron.d$</span> ls -al
total 104
drwxr-xr-x   2 root root 4096 Mar  5 12:43 .
drwxr-xr-x 108 root root 4096 May  4 00:39 ..
-rw-r--r--   1 root root  102 Feb  9  2013 .placeholder
-r--r-----   1 root root   46 Nov 14  2014 behemoth4_cleanup
-rw-r--r--   1 root root  355 May 25  2013 cron-apt
-rw-r--r--   1 root root   61 Nov 14  2014 cronjob_bandit22
-rw-r--r--   1 root root   62 Nov 14  2014 cronjob_bandit23
-rw-r--r--   1 root root   61 May  3  2015 cronjob_bandit24
-rw-r--r--   1 root root   62 May  3  2015 cronjob_bandit24_root
-r--r-----   1 root root   47 Nov 14  2014 leviathan5_cleanup
-rw-------   1 root root  233 Nov 14  2014 manpage3_resetpw_job
-rw-r--r--   1 root root   51 Nov 14  2014 melinda-stats
-rw-r--r--   1 root root   54 Jun 25  2016 natas-session-toucher
-rw-r--r--   1 root root   49 Jun 25  2016 natas-stats
-r--r-----   1 root root   44 Jun 25  2016 natas25_cleanup
-r--r-----   1 root root   47 Aug  3  2015 natas25_cleanup~
-r--r-----   1 root root   47 Jun 25  2016 natas26_cleanup
-r--r-----   1 root root   43 Jun 25  2016 natas27_cleanup
-rw-r--r--   1 root root  510 Oct 29  2014 php5
-rw-r--r--   1 root root   63 Jul  8  2015 semtex0-32
-rw-r--r--   1 root root   63 Jul  8  2015 semtex0-64
-rw-r--r--   1 root root   64 Jul  8  2015 semtex0-ppc
-rw-r--r--   1 root root   35 Nov 14  2014 semtex5
-rw-r--r--   1 root root  396 Nov 10  2013 sysstat
-rw-r--r--   1 root root   29 Nov 14  2014 vortex0
-rw-r--r--   1 root root   30 Nov 14  2014 vortex20
<span style="color:red">bandit21@melinda:/etc/cron.d$</span> cat cronjob_bandit22
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
<span style="color:red">bandit21@melinda:/etc/cron.d$</span> cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
<span style="color:red">bandit21@melinda:/etc/cron.d$</span> cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
</code></pre></figure>

### Lvl 22-23
<p>'A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.'</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit22@melinda:~$</span> cat /etc/cron.d/cronjob_bandit23
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
<span style="color:red">bandit22@melinda:~$</span> cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
<span style="color:red">bandit22@melinda:~$</span> echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
<span style="color:red">bandit22@melinda:~$</span> cat /tmp/8ca319486bfbbc3663ea0fbe81326349
jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n
</code></pre></figure>

### Lvl 23-24
<p>'A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.'</p>
<p>This one is a little tricky. The cronjob script runs and then deletes all scripts in /var/spool/bandit24. We know the password file is located in /etc/bandit_pass/ from previous levels, so we'll create a script to read that file.</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit23@melinda:~$</span> cat /etc/cron.d/cronjob_bandit24
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
<span style="color:red">bandit23@melinda:~$</span> cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname
echo "Executing and deleting all scripts in /var/spool/$myname:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        timeout -s 9 60 "./$i"
        rm -f "./$i"
    fi
done
<span style="color:red">bandit23@melinda:/etc/cron.d$</span> mkdir /tmp/mariotest
<span style="color:red">bandit23@melinda:/etc/cron.d$</span> cd /tmp/mariotest
<span style="color:red">bandit23@melinda:/tmp/mariotest$</span> vim test.sh
    #!/bin/bash
    cat /etc/bandit_pass/bandit24 > /tmp/mariotest/ps.txt
<span style="color:red">bandit23@melinda:/tmp/mariotest$</span> chmod 777 test.sh
<span style="color:red">bandit23@melinda:/tmp/mariotest$</span> cp test.sh /var/spool/bandit24
<span style="color:red">bandit23@melinda:/tmp/mariotest$</span> cat ps.txt
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ
</code></pre></figure>