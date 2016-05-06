# Rails 勉強会 : RESTful なアプリケーションを作る

View の設定

## index

```
$ editor app/views/tweets/index.html.erb

<ul>
<% @tweets.each do |tweet| %>
  <li><%= tweet.title%></li>
  <li><%= tweet.content%></li>
<% end %>
</ul>
```

## show

```
$ editor app/views/tweets/show.html.erb

<h1><%= @tweet.title %></h1>
<div><%= @tweet.content %></div>
```
