	var fs = require("fs");
	var reradStream = fs.createReadStream('input.txt');
	var writerStream = fs.createWriteStream('output.txt');
	var data = '我是从数据库获取的数据，我要保存起来11\n';

	// 读取文件流
	var str='';
	var count=0;
	reradStream.on('data',function(chunk){
    str+=chunk;
    count++;
	})
	reradStream.on('end',function(chunk){
    console.log(str)
    console.log(count)
    console.log('读取完成')
	})

	reradStream.on('error',function(error){
    console.log(error)
	})

	// 写入文件流
	for(var i=0;i<10;i++){
    writerStream.write(data,'utf8');
	}

	//标记写入完成
	writerStream.end();
	writerStream.on('finish',function(){
    console.log('写入完成111');
	});

	//失败
	writerStream.on('error',function(){
    console.log('写入失败');
	});

	// 管道
	reradStream.pipe(writerStream);

	/*
    fs.createReadStream('fileName')创建文件流读取对象
    用on接受广播：
    data:分片读取；
    end:读取结束
    error:错误信息

    fs.createWriteStream('fileName')创建文件流写入对象
    .end():标记文件末尾
    用on接受广播
    finish:写入结束
    error：写入错误
    
    管道pipe()
    reradStream.pipe(writerStream)，读取后可直接写入

	*/