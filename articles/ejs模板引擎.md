	var http = require('http');
	var url = require('url');
	var ejs = require('ejs');
	
	http.createServer(function(req, res) {
    if(req.url.indexOf('favicon') != -1){
        res.end();
        return false;
    }

    var userName='来自后台的消息';
    var list=['111','222','333','444'];
    var htmlStr='<h3>我是标题</h3>';

    res.writeHead(200,{"Content-Type":"text/html;charset=utf-8"});
    var pathName=url.parse(req.url,true).pathname;///index.html?1123，使用url模块获取干净的地址路径
    if(pathName == '/'){//默认跳转到index.html页面
        ejs.renderFile('views/index.html',{msg:userName,list:list,htmlStr:htmlStr},function(err,data){
            if(err){
                console.log(err)
            }
            res.end(data);
        })
    }else if(pathName == '/register'){
        var msg='这是一个注册页面!';
        ejs.renderFile('views/register.html',{msg:msg},function(err,data){
            res.end(data);
        })
    }
    
	}).listen(8001);

	/*
	1、引入ejs模块
	2、ejs.renderFile()读取模板并且传入参数
	*/
	
	
		//index.html页面
	<!DOCTYPE html>
	<html lang="zh-CN">
	<head>
	<meta charset="utf-8">
	<title>首页</title>
	</head>
	<body>
	<h2>这是一个ejs模板22</h2>
	<h2><%= msg%></h2>
	<%- htmlStr %>
	<br>

	<ul>
			<% for(var i=0;i<list.length;i++){%>
					<li><%=list[i]%></li>
			<% } %>
	</ul>
	</body>
	</html>