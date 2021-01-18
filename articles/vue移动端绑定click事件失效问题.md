	原因可能是你使用了better-scroll，默认它会阻止touch事件。所以在配置中需要加上click: true
	例：
	mounted(){
	this.scroll=new Bscroll(this.$refs.wrapper, { mouseWheel: true, click: true, tap: true })
	}