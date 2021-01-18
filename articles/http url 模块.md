	var http=require('http');
	var url=require('url');

	http.createServer(function(req,res){
			res.writeHead(200,{"Content-Type":"text/html;charset=utf-8"});
    var str='<ul>';
    for(i=1;i<=10;i++){
        str+='<li>'+i+'</li>';
    }
    str+='</ul>';
    res.write(str);
    if(req.url.indexOf('favicon.ico') == -1){
        var result=url.parse(req.url,true);
        console.log('aid='+result.query.aid)
    }

    res.end();
	}).listen(9999);
	/*
    调试流程：
    写好页面之后cd到该文件目录，node server.js就能运行，但是每次修改都需要再次运行很麻烦，可以全局安装一个插
    件，自动刷新
    npm install -g supervisor
    cd到文件目录 supervisor server.js
    ctrl+c 停止进程

    http模块
    http模块node本身自带，利用createServer方法可以创建http服务器，带两个参数，req是请求参数，res是返回参数，
    res.write写入内容，res.end()结束响应
    每次浏览器访问会有两个请求一次是访问页面一次是获取favicon.ico图标，因此需要通过req中的url进行判断，如果
    是后者则不打印信息，否则控制台会打印两次

    url模块
    url模块也是node自带，有三个方法:
    url.parse(url,true) 可以把请求地址转化为对象，后面的true可以把query参数的内容转化为对象
    url.format(urlObject) 与parse()正好相反，会把含有请求地址的对象转化为网址
    url.resolve('http://www.baidu.com','news') 替换路径,输出 http://www.baidu.com/news
    如果地址本身自带二级目录会被覆盖http://www.baidu.com/nav -> http://www.baidu.com/news
	*/