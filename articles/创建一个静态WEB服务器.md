	1、地址栏输入地址能够访问页面
	2、css、js加载正确并起作用（设置其正确的content-type类型）
	3、不存在的页面跳转到404页面
	exports.setMime=function(extname){
    switch (extname) {
        case '.html':
            return 'text/html'
            break;
        case '.css':
            return 'text/css'
            break;
        case '.js':
            return 'text/javascript'
            break;
        case '.jpg':
            return 'image/jpg'
            break;
        case '.png':
            return 'image/png'
            break;
        case '.gif':
            return 'image/gif'
            break;
			}
	}
	var http = require('http');
	var fs = require('fs');
	var path = require('path');
	var url = require('url');
	var mime=require('./module/setMime');//自定义模块，根据文件类型返回mime类型

	http.createServer(function(req, res) {
    if(req.url.indexOf('favicon') != -1){
        res.end();
        return false;
    }

    var pathName=url.parse(req.url).pathname;///index.html?1123，使用url模块获取干净的地址路径
    var extname=path.extname(pathName);//使用path模块获取访问页面的后缀类型
    if(pathName == '/'){//默认跳转到index.html页面
        pathName='/index.html';    
    }

    // 根据地址路径读取文件
    //readFIle是异步获取，readFileSync是同步获取
    fs.readFile('static/'+pathName,function(err,data){
        if(err){
            // 文件不存在则跳转到404页面
            fs.readFile('static/404.html',function(err404,data404){
                if(err1){
                    console.log(err404);
                    return false;
                }
                // 状态码设置为404
                res.writeHead(404,{"Content-Type":"text/html;charset=utf-8"});
                res.write(data404);
                res.end();
            })
            return false;
        }

        var mimeType=mime.setMime(extname);//获取每个请求的文件mime类型
        res.writeHead(200,{"Content-Type":mimeType+";charset=utf-8"});
        res.write(data);
        res.end();
    })
	}).listen(8001);