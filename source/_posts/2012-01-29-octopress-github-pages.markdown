---
layout: post
title: "Github page + Octopress"
date: 2012-01-19 18:15
comments: true
categories: [Github, git, Octopress]
author: ChiaChia Lee
---


發現最近很多大大紛紛使用[Octopress]來建自己的部落格，我也來體驗一下吧。目標就是用Octopress建立自己的blog，host在Github page，網址是zerodie.github.com(host在github)。以下是本網站的生產過程：

<!--more -->

**Step1. 建立自己的[Github page]:**

首先來[這裡](https://github.com/repositories/new)new一個github repository，在project name的地方填入username.github.com，以我自己為例就是zerodie.github.com

接著按照他給你的setup步驟走完就是啦，不會太難。


**Step2. Setup Octopress**

參考：[Octopress Setup](http://octopress.org/docs/setup/)

除了git以外，你還要用[rvm]/[rbenv]安裝Ruby 1.9.2。所有設定步驟文件裡面寫得非常清楚：
```
$ rvm install 1.9.2 && rvm use 1.9.2
$ git clone git://github.com/imathis/octopress.git octopress
$ cd octopress    # If you use RVM, You'll be asked if you trust the .rvmrc file (say yes).
$ ruby --version  # Should report Ruby 1.9.2
$ gem install bundler
$ bundle install
$ rake install
```


**Step3. ：**

參考：[Deploying to Github Pages](http://octopress.org/docs/deploying/github/)

```
rake setup_github_pages
```
輸入自己的Github Pages repository url，像我的就是：git@github.com:zerodie/zerodie.github.com.git。按下enter後：


```
$ rake generate
$ rake deploy
```
開始產生blog，並複製產生的檔案到_deploy/底下，add&commit&push到master branch(現在應該是在source branch，先前的"rake setup_github_pages"指令所做的事情之一是將branch從master切換到source)。這個時候你會收到一封Github寄給你的信，標題是"[zerodie.github.com] Page build successful"，表示發佈成功。接著把修改的push回source：

```
$ git add .
$ git commit -m 'your message'
$ git push origin source
```

**Step4. 設定blog參數**

參考：[Configuring Octopress](http://octopress.org/docs/configuring/)
這裡我只改了標題、副標題、作者，3rd party我用了Google Plus、Twitter、Facebook，之後這些buttons會顯示在文章的底下。

```
title: 李嘉玲的技術筆記
subtitle: rails notes
author: ChiaChia Lee
...
twitter_user: zerodie
google_plus_one: true
facebook_like: true
```

**Step5. 開始寫文章啦**

參考：[blogging basic](http://octopress.org/docs/blogging/)文件：

```
$ rake 'new_post["title"]'
```
這裡值得注意的是，不知道為什麼，如果我按照文件範例下指令會有錯誤，"no matches found: new_post[title]"，所以要修正成rake 'new_post["title"]'，如果你知道原因的話歡迎留言給我。

Octopress的網頁內容是使用Markdown語法，如果你沒寫過Markdown，這裡有[Markdown語法的中文文件](http://markdown.tw/)，如果你的文章像本文一樣常用到code blocks，Octopress有[plugin](http://octopress.org/docs/plugins/codeblock/)絕不能錯過。噢，順便推薦一個免費的markdown editor for MAC：[Mou]。

寫好一篇之後執行：

```
rake generate   # Generates posts and pages into the public directory
rake watch      # Watches source/ and sass/ for changes and regenerates
rake preview    # Watches, and mounts a webserver at http://localhost:4000
```
開啓瀏覽器http://localhost:4000應當要看到你的blog。

最後別忘了push&deploy
```
$ git add .
$ git commit -m "article：Github page + Octopress"
$ git push
$ rake deploy
```

來到http://zerodie.github.com，也就是這裡，你所看到的樣子囉:)



[Github page]: http://pages.github.com/
[rvm]: http://beginrescueend.com/rvm/install/
[rbenv]: https://github.com/sstephenson/rbenv
[Octopress]: http://octopress.org/
[Mou]: http://mouapp.com/