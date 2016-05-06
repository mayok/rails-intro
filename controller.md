# Rails 勉強会 : RESTful なアプリケーションを作る

Controller の設定

## index

```
$ editor app/controllers/tweets_controller.rb

def index
  @tweets = Tweet.all
end
```

## show
```
def show
  @tweet = Tweet.find(params[:id])
end
```

## new
```
def new
  @tweet = Tweet.new
end
```

## create
```
def create
  @tweet = Tweet.new(tweet_params)
  if @tweet.save
    redirect_to @tweet
  else
    render 'new'
  end
end

private
  def tweet_params
    params.require(:tweet).permit(:title, :content)
  end
```
