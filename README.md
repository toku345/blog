# toku345's blog

## Requirement

- hugo
- firebase tools

## Installation

### hugo

```console
$ brew install hugo
```

### firebase tools

```console
$ npm install
```


## Usage

```console
# ブログ下書き時
$ hugo server -D -w

# 公開ページのみ
$ hugo server

# firebase toolsで確認する場合
$ npx firebase serve --only hosting
```

## Build

```
$ hugo --minify
```

## Deploy

```console
$ npx firebase login
$ npx firebase deploy --only hosting

# authがうんぬんって感じのエラーログがでる場合は、一旦 logout すべし
$ npx firebase logout
```
