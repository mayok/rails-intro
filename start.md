# Rails 勉強会 : RESTful なアプリケーションを作る

Model, View, Controller の作成と Route の設定

## アプリケーションの作成, Rubygems の取得

```
# アプリケーションを作成する
# rails new を実行すると Rubygems を取得しようとするので，
# --skip-bundle をつける
$ rails new <app-name> --skip-bundle
$ cd <app-name>

# Gemfile を編集する
$ editor Gemfile

# Rubygems を取ってくる
# このときアプリケーションごとに Rubygems を管理したい場合は --path を指定する
# --path vendor/bundle が一般的
$ bin/bundle install --path vendor/bundle

```

## Model, Controller, View の作成

ここでは `tweet` を扱う MVC モデルを作ることを考える

```
# Model
# rails generate コマンドに続けて model, controller を指定する
# generate は g に省略できる
# rails g model の場合は単数,
# rails g controller の場合は 複数にするのが一般的
$ rails g model Tweet title:string content:text

# migrate ファイルが作成されるので，データベースに反映させる
$ bin/rake db:migrate

# View, Controller を作る
$ rails g controller Tweets show index ...
```

## Route を編集, 確認する

```
# Controller 作成時に指定したもの (上の例では show, index) が
# config/routes.rb にすでに書かれている
$ editor config/routes.rb

# ここでは RESTful なアプリケーションを作るので，
# root と resources を書く
$ cat config/routes.rb

Rails.application.routes.draw do
  root 'tweets#index'
  resources :tweets
end


# config/routes.rb で正しくルートが書かれているかを確認する
$ bin/rake routes

    Prefix Verb   URI Pattern                Controller#Action
      root GET    /                          tweets#index
    tweets GET    /tweets(.:format)          tweets#index
           POST   /tweets(.:format)          tweets#create
 new_tweet GET    /tweets/new(.:format)      tweets#new
edit_tweet GET    /tweets/:id/edit(.:format) tweets#edit
     tweet GET    /tweets/:id(.:format)      tweets#show
           PATCH  /tweets/:id(.:format)      tweets#update
           PUT    /tweets/:id(.:format)      tweets#update
           DELETE /tweets/:id(.:format)      tweets#destroy
```
