1. 一个非常常见的操作是将字符串的第一个字母大写。虽然许多编程语言都有一种本地方法来实现这一点，但 JS 需要做一些工作
		let word = 'apply'
		word = word[0].toUpperCase() + word.substr(1)
		console.log(word) // "Apple"
	//另外一种方法
		// This shows an alternative way
		let word = "apple";

  // 使用扩展运算符（`...`）拆分为字符

		const characters = [...word];
		characters[0] = characters[0].toUpperCase();
		word = characters.join("");
		console.log(word); // "Apple"
2.如何在多个分隔符上分割字符串
   假设我们要在分隔符上分割字符串，第一想到的就是使用split方法，这点，智米们肯定知道。 但是，有一点大家可能不知道，就是split可以同时拆分多个分隔符, 使用正则表达式就可以实现：
	 // 用逗号(,)和分号(;)分开。
		const list = "apples,bananas;cherries"
		const fruits = list.split(/[,;]/)
		console.log(fruits); // ["apples", "bananas", "cherries"]
3.如何检查字符串是否包含特定序列
字符串搜索是一项常见的任务。 在 JS 中，你可以使用String.includes方法轻松完成此操作。 不需要正则表达式
		const text = "Hello, world! My name is Kai!"
		console.log(text.includes("Kai")); // true
4.如何检查字符串是否以特定序列开头或结尾
   在字符串的开头或结尾进行搜索，可以使用String.startsWith和String.endsWith方法。
		const text = "Hello, world! My name is Kai!"
		console.log(text.startsWith("Hello")); // true
		console.log(text.endsWith("world")); // false
5.如何替换所有出现的字符串
有多种方法可以替换所有出现的字符串。 可以使用String.replace方法和带有全局标志的正则表达式。 或者，可以使用新的String.replaceAll方法。 请注意，并非在所有浏览器和Node.js 版本中都可用此新方法。
		const text = "I like apples. You like apples."
		console.log(text.replace(/apples/g, "bananas"));
		// "I like bananas. You like bananas."
		console.log(text.replaceAll("apples", "bananas"));
		// "I lik
