---
layout: post
title: "some useful ruby tips"
date: 2013-10-22 09:53
comments: true
categories: [Ruby, tips, useful]
author: ChiaChia Lee
---

1. 有時候要印出ruby array的內容，用for loop如果沒判斷index，最後又會多一個逗號或空格
```
nums = [1, 3, 5, 9, 15]
puts nums * "," #=> "1,3,5,9,15"
```

很easy吧

