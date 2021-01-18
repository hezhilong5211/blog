	1.使用http模块创建一个简单的服务器
	//引用模块
	var http=require(“http”);
	//创建服务
	http.createServer(function(req,res){
	//创建服务

                 res.end(“hello world”);

                 //向用户写入

	}).listen(80);
	//监听80端口