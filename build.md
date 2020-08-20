cd $GOPATH/src
go get -v -u github.com/ochinchina/supervisord
cd ochinchina/supervisord/
go generate
go get -u
GOOS=linux go build -tags release -a -ldflags "-linkmode external -extldflags -static" -o supervisord github.com/ochinchina/supervisord


可用API：
http://192.168.6.94:9001/program/list GET
http://192.168.6.94:9001/program/stop/kibana POST
http://192.168.6.94:9001/program/start/kibana POST
http://192.168.6.94:9001/supervisor/reload POST
http://192.168.6.94:9001/program/startPrograms POST 批量启动  ["kibana"]
http://192.168.6.94:9001/program/stopPrograms POST 批量关闭 ["kibana"]
http://192.168.6.94:9001/supervisor/shutdown put 关闭supervisor
