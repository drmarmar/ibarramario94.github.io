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


<p><b>Lvl 1-2</b></p>
<p>The password is stored in a file called <b>-</b> so we must locate it and read it. Since its a special character, we must use cat with the directory indicator.</p>
<code><span style="color:red">bandit1@melissa:~$ </span>ls
-
<span style="color:red">bandit1@melissa:~$ </span>cat ~/-</code>


<p><b>Lvl 1-2</b></p>
<p>The password is stored in a file called <b>-</b> so we must locate it and read it. Since its a special character, we must use cat with the directory indicator.</p>
<figure class="highlight"><pre><code class="language-bash" data-lang="bash"><span style="color:red">bandit1@melissa:~$ </span>ls
-
<span style="color:red">bandit1@melissa:~$ </span>cat ~/-</code></pre></figure>

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
