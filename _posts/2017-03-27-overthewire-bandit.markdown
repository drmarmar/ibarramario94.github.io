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
<p>Within the inhere directory the password is stored in the only human-readable file. I used the <i>file</i> command to display the file data types and locate the password.
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
bandit4@melinda:~$ cat inhere/-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
</code></pre></figure>

---

## Code

A HTML Example:

{% highlight html %}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <h1>Just a test</h1>
</body>
</html>
{% endhighlight %}
