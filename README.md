
## deploy
```
gcloud functions deploy hello-function \
  --runtime=go111 \
  --trigger-http \
  --memory 128 \
  --entry-point Receive
```

### TIPS

https://qiita.com/sky0621/items/51477feb86b1ba03c54e


* 下記のエラーは、独自モジュールのpackageが正しく行えてないケースが疑われる。 `go mod init` を適切なmodule名で実行し直す
```
 gcloud functions deploy StructuredHello --runtime=go111 --trigger-http
Deploying function (may take a while - up to 2 minutes)...failed.                                           
ERROR: (gcloud.functions.deploy) OperationError: code=3, message=Build failed: build serverlessapp: cannot find module for path _/tmp/sgb/staging/srv
````



* StructuredHello:リソース名
* Hello: 呼び出されるFunc名(要：HandlerFunc実装)

```
Structured  gcloud functions deploy HelloWorld --runtime=go111 --trigger-http --memory 128 --entry-point Hello
Deploying function (may take a while - up to 2 minutes)...failed.                                                                                                      
ERROR: (gcloud.functions.deploy) OperationError: code=3, message=Build failed: go: finding go.uber.org/zap v1.10.0
go: downloading go.uber.org/zap v1.10.0
go: finding go.uber.org/multierr v1.1.0
go: finding go.uber.org/atomic v1.4.0
go: downloading go.uber.org/multierr v1.1.0
go: downloading go.uber.org/atomic v1.4.0
# serverlessapp
./worker.go:48:28: undefined: HelloWorld.Hello
./worker.go:173:29: undefined: HelloWorld.Hello
```
