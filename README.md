# Goのログ運用を考える

Go1.13でエラーがwrapできるようになった。
使い方については、[ブログ](https://cipepser.hatenablog.com/entry/go1.13-error-wrapping)にまとめた。

[Working with Errors in Go 1\.13 \- The Go Blog](https://blog.golang.org/go1.13-errors)に以下のように書いてある。

> Wrap an error to expose it to callers. Do not wrap an error when doing so would expose implementation details.

実装詳細を晒すなら、エラーをwrapするなとのこと。

## 環境

```sh
❯ go version
go version go1.13.5 darwin/amd64
```

## やりたいこと

1. ログ出力するときにstack traceしたい
1. エラーハンドリング時にエラー型によって分岐させたい
1. エラーメッセージをwrapしたい

## logrus

[logrusのSetReportCaller](https://godoc.org/github.com/sirupsen/logrus#Logger.SetReportCaller)を有効にすると行数を取得することはできる。


## References
- [Go1\.13のError wrappingを触ってみる \- 逆さまにした](https://cipepser.hatenablog.com/entry/go1.13-error-wrapping)
- [Working with Errors in Go 1\.13 \- The Go Blog](https://blog.golang.org/go1.13-errors)
- [logrus \- GoDoc](https://godoc.org/github.com/sirupsen/logrus)
- [階層化 Error パッケージ “xerrors” を試してみる — プログラミング言語 Go \| text\.Baldanders\.info](https://text.baldanders.info/golang/xerrors/)
- [Golangのエラー処理とpkg/errors \| SOTA](https://deeeet.com/writing/2016/04/25/go-pkg-errors/)