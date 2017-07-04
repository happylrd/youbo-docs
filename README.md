# youbo-docs

<img src="https://github.com/happylrd/youbo-cms/blob/master/kiri/src/common/image/logo.png" width="128" style="max-width:100%;" alt="Youbo">

> Yet another pure and fresh micro blog.

A docs for youbo.

## Architecture

```viz
graph youbo {
     desktop_web -- API
     mobile_web -- API
     android_app -- API
     cms -- API
     API -- api_server
     api_server -- image_server
     api_server -- database
     api_server -- cache
     cache -- database
}
```

## Category

symbol | type | core tech
------ | ---- | ---
[Iris](https://github.com/happylrd/youbo-api)   | api server | spring
[Seria](https://github.com/happylrd/youbo-desktop)  | desktop&mobile web | vue
[kiri](https://github.com/happylrd/youbo-cms)   | cms | react
[Daphne](https://github.com/happylrd/youbo-android) | android app | android

> Note: some repos are private now.

## Business

### Domain model

#### Relationship

```puml
User "1" -- "1" UserInfo : contain

Group "1" -- "*" User : has

Manager "1" -- "1" User : is

Manager "1" -- "1" Group : is

Manager "1" -- "*" TweetStream : manage

TweetStream "1" -- "*" Tweet : has

Tweet "1" -- "*" Fragment : has

TweetStream "1" -- "1" CommentBoard : has

Tweet "1" -- "1" CommentBoard : has

CommentBoard "1" -- "*" Comment : has

Tweet "*" -- "1" TweetStage : commit

TweetStage "*" -- "1" TweetStream : merge
```
