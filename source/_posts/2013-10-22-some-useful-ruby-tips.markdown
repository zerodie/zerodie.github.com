---
layout: post
title: "some useful ruby tips"
date: 2013-10-22 09:53
comments: true
categories: [Ruby, tips, useful]
author: ChiaChia Lee
---

有時候要印出ruby array的內容，例如
```
nums = [1, 3, 5, 9, 15]
```
我希望可以印出
```
1 3 5 9 15
```
但是又不想寫for loop，就可以用以下寫法

```
puts nums * " " #=> "1 3 5 9 15"
```

很easy吧

