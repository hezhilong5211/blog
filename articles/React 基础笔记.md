	1.开发环境的搭建（两种方法）
		1. 1、必须要安装nodejs     注意：安装nodejs稳定版本     nodejs版本:v8.11.2            npm版本:v5.6.0

       2.安装脚手架工具   （单文件组件项目生成工具）   只需要安装一次

              npm install -g create-react-app   /  cnpm install -g create-react-app

       3.创建项目   （可能创建多次）

              找到项目要创建的目录：

              create-react-app reactdemo

       4.cd  到项目里面

              cd  reactdemo

              npm start             yarn start运行项目

              npm run build         yarn build 生成项目
		2.1、必须要安装nodejs     注意：安装nodejs稳定版本      nodejs版本:v8.11.2           npm版本:v5.6.0

       2.安装脚手架工具并创建项目

              找到项目要创建的目录执行：

              npx create-react-app reactdemo

       4.cd  到项目里面

              cd  reactdemo

              npm start  运行项目（调试）

              npm run build 生成项目（发布）
	2.两种创建组件的方式（后期学习hooks）
	第一种是采用函数式的方式（无状态的时候可以使用该方式）：
	function demo（））{
		//这种方式不存在this关键字
		return //标签
		无状态组件的创建形式使代码的可读性更好，并且减少了大量冗余的代码，精简至只有一个render方法，大大的增强了编写一个组件的便利，除此之外无状态组件还有以下几个显著的特点：

	组件不会被实例化，整体渲染性能得到提升
	因为组件被精简成一个render方法的函数来实现的，由于是无状态组件，所以无状态组件就不会在有组件实例化的过程，无化过程也就不需要分配多余的内存，从而性能得到一定的提升。
	组件不能访问this对象
	无状态组件由于没有实例化过程，所以无法访问组件this中的对象，例如：this.ref、this.state等均不能访问。若想访问就不能使用这种形式来创建组件
	组件无法访问生命周期的方法
	因为无状态组件是不需要组件生命周期管理和状态管理，所以底层实现这种形式的组件时是不会实现组件的生命周期方法。所以无状态组件是不能参与组件的各个生命周期管理的。
	无状态组件只能访问输入的props，同样的props会得到同样的渲染结果，不会有副作用
	无状态组件被鼓励在大型项目中尽可能以简单的写法来分割原本庞大的组件，未来React也会这种面向无状态组件在譬如无意义的检查和内存分配领域进行一系列优化，所以只要有可能，尽量使用无状态组件
	}
	第二种方式采用类声明组件（有状态的组件使用）
	class demo expands React.Component {
			//构造函数 定义在组件原型的初始化变量
			  constructor(props) {
        super(props);

        // 设置 initial state
        this.state = {
            text: props.initialValue || 'placeholder'
        };

        // ES6 类中函数必须手动绑定
        this.handleChange = this.handleChange.bind(this);
    }
		handleChange(event) {
        this.setState({
            text: event.target.value
        });
    }

    render() {
        return (
            <div>
                Type something:
                <input onChange={this.handleChange}
               value={this.state.text} />
            </div>
        );
    }
	}
	