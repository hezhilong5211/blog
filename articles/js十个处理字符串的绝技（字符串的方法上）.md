1. JS 字符串允许简单的重复，与纯手工复制字符串不同，我们可以使用字符串的repeat方法。
		 const laughing = '小智'.repeat(3)
		 consol.log(laughing) // "小智小智小智"

		 const eightBits = '1'.repeat(8)
		 console.log(eightBits) // "11111111"
 2.如何填充一个字符串到指定的长度
    // 在开头添加 "0"，直到字符串的长度为 8。
		const eightBits = '001'.padStart(8, '0')
		console.log(eightBits) // "00000001"

	//在末尾添加“ *”，直到字符串的长度为5。
		const anonymizedCode = "34".padEnd(5, "*")
console.log(anonymizedCode) // "34***"
3. 如何将字符串拆分为字符数组
   有多种方法可以将字符串分割成字符数组，我更喜欢使用扩展操作符(...):
		 const word = 'apple'
		 const characters = [...word]
		 console.log(characters) // ["a", "p", "p", "l", "e"]
4.如何计算字符串中的字符长度
		 const word = “apple”
		 world.length // 5
	 但是对于中文字符串来说  点length的方法不行
	 这个时候最好使用es6的新语法  解构出来 然后再length方法
5.如何反转字符串中的字符
   反转字符串中的字符是很容易的。只需组合扩展操作符(...)、Array.reverse方法和Array.join方法
		 const word = "apple"
		 const reversedWord = [...word].reverse().join("")
		 console.log(reversedWord) // "elppa"
