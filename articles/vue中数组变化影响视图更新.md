1. 数组的更新检测  使用push()、pop()、shift()、unshift()、 splice()、sort()、等数组方法会影响原数组  会直接更新vue的视图
2. filter concat slice map 等方法数组替换旧数组 可以间接更新vue的视图