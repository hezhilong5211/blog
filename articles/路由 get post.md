	var http = require('http');
	var url = require('url');
	var ejs = require('ejs');
	var fs = require('fs');

	http.createServer(function(req, res) {
    if(req.url.indexOf('favicon') != -1){
        res.end();
        return false;
    }

    var methodType=req.method.toLowerCase();//获取传值类型，get或者是post

    res.writeHead(200,{"Content-Type":"text/html;charset=utf-8"});
    var pathName=url.parse(req.url,true).pathname;///index.html?1123，使用url模块获取干净的地址路径

    if(pathName == '/'){//默认跳转到login.html页面
        ejs.renderFile('views/login.html',{},function(err,data){
            if(err){
                console.log(err)
            }
            res.end(data);
        })
    }else if(pathName == '/dologin' && methodType=='post'){
        var postStr='';
        req.on('data',function(chunk){
            postStr+=chunk;
        })
        req.on('end',function(chunk){
            console.log(postStr)
            fs.appendFile('login.txt',postStr+'\n',function(err,data){
                if(err){
                    console.log(err);
                    return;
                }
                console.log('写入成功')
            });
            res.end('<script>alert("登陆成功");history.back();</script>')
        })
    }else if(pathName == '/dologin'){
        var info=url.parse(req.url,true);
        info=JSON.parse(JSON.stringify(info));
        ejs.renderFile('views/dologin.html',{query:info.query},function(err,data){
            res.end(data);
        })
    }
    
	}).listen(8001);

	/*
	1、post传值获取参数通过req.on()，类似流的方式，get传值通过url模块获取格式化之后的参数
	2、路由使用urk模块，根据地址栏的pathname进行判断
	*/
	
	//login.html
	<form id="dataForm" method="post" action='/dologin'>
       <input placeholder='请输入账号' id='username' value='' name='username' autocomplete="off" maxlength="25">
       <input type="password" placeholder='请输入密码' id='password' value='' name='password' autocomplete="off" maxlength="25">
       <input type="submit" id ='btn' value="登录">
    </form>