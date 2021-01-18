	//模拟双击事件(双击事件dblclick不支持)
	var touchtime = 0;
	map.addEventListener("touchend", function(e) { //touchend触摸结束时触发此事件
	if(0 == touchtime) {
	touchtime = new Date().getTime();
	} else {
	if(new Date().getTime() - touchtime < 800) {
	searchNearby(e);
	} else {
	//如果第二次点击在第一次点击0.8秒后，
	//则第二次点击默认为下一次双击判断的第一次点击
	touchtime = new Date().getTime();
	}
	}
	});