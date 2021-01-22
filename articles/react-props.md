	state 和 props 主要的区别在于 props 是不可变的，而 state 可以根据与用户交互来改变。这就是为什么有些容器组件需要定义 state 来更新和修改数据。 而子组件只能通过 props 来传递数据
	基本用法：
	<Component data="测试props"/>   data就是通过props来传递参数的
	<!DOCTYPE html>
	<html>
	<head>
	<meta charset="UTF-8" />
	<title>React 实例</title>
	<script src="https://cdn.staticfile.org/react/16.4.0/umd/react.development.js"></script>
	<script src="https://cdn.staticfile.org/react-dom/16.4.0/umd/react-dom.development.js"></script>
	<script src="https://cdn.staticfile.org/babel-standalone/6.26.0/babel.min.js"></script>
	</head>
	<body>
	<div id="example"></div>

	<script type="text/babel">


	class Child extends React.Component {

    render() {
        return (
            <div>
            请输入邮箱：<input onChange={this.props.handleEmail}/>
            </div>
        );
    }
	}

 

	class Parent extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            email: ' '
        }
    }

    handleEmail = (event) => {
        this.setState({
            email: event.target.value
        });
    }

    render() {
        return (
            <div>
            <div>用户邮箱：{this.state.email}</div>
            <Child name="email" handleEmail={this.handleEmail}/>
            </div>
        );
    }
	}
	ReactDOM.render(
			<Parent />,
			document.getElementById('example')
	);


	</script>

	</body>
	</html>