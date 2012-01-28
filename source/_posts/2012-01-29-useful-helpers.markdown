---
layout: post
title: "useful helpers and functions in views"
date: 2012-01-28 15:06
comments: true
categories: [Ruby on Rails, helpers]
author: ChiaChia Lee
---

推薦幾個好用的helper&functions：

[**truncate**](http://apidock.com/rails/ActionView/Helpers/TextHelper/truncate): 文字內容超過一定長度的部分，顯示成"..."

```ruby
truncate("Once upon a time in a world far far away")
=> "Once upon a time in a world..."

truncate("Once upon a time in a world far far away", :length => 17)
=> "Once upon a ti..."

truncate("Once upon a time in a world far far away", :length => 17, :separator => ' ')
=> "Once upon a..."
```

<!-- more -->


[**simple_format**](http://apidock.com/rails/ActionView/Helpers/TextHelper/simple_format)：將文字內容中 \n\r 自動轉 p 和 br 等HTML tags。

```ruby
simple_format("Look ma! A class!", :class=>'description')
=> "<p class='description'>Look ma! A class!</p>"
```

[**to_sentence**](http://apidock.com/rails/ActiveSupport/CoreExtensions/Array/Conversions/to_sentence)：把Array內容用逗號或自訂字元分開。

```ruby
%w(lorem ipsum dolor sit).to_sentence
=> "lorem, ipsum, dolor, and sit"

%w(lorem ipsum dolor sit).to_sentence(:words_connector => ' + ')
=> "lorem + ipsum + dolor, and sit"
```


[**number_to_currency**](http://apidock.com/rails/v3.1.0/ActionView/Helpers/NumberHelper/number_to_currency)：把數字轉成currency string。

```ruby
Price is <%= number_to_currency 13.5 %>
=> Price is $13.50
```

[**time_ago_in_words**](http://apidock.com/rails/v3.1.0/ActionView/Helpers/DateHelper/time_ago_in_words)：將時間轉成人性化文字。

```ruby
He was buried alive <%= time_ago_in_words @zombie.created_at %> ago
=> He was buried alive 2 days ago

time_ago_in_words(Time.now - 15.hours)
=> about 15 hours

time_ago_in_words(Time.now)
=> less than a minute
```

[**number_to_human**](http://apidock.com/rails/v3.1.0/ActionView/Helpers/NumberHelper/number_to_human)：將數字轉成human-readable的文字。

```ruby
Ash is <%= number_to_human 13234355423 %> years old
=> Ash is 13.2 billion years old

```

[**div_for**](http://apidock.com/rails/ActionView/Helpers/RecordTagHelper/div_for)：div wrapper，並把class屬性設成model name、id值設成model_id。

```ruby
<%= div_for(@person) do %>
   <%= @person.name %>
<% end %>

=> <div id="person_123" class="person"> Joe Bloggs </div>
```