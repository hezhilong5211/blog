	GET与POST区别
	post数据很大：分段发送。1G
	get数据很小：一次发生。32K
	post处理
	req.on(标识,回调函数)
	标识（字符串）：
	‘data’：多次接受数据。
	‘end’：表示数据传输完成。
	回调函数
	data：function(dat{}
	注意：需要找个临时变量存储data。
	end：function(){}
	注意：传输结束。