	类定义的组件创建state状态并修改
	class TodoItem extends React.Component{
    constructor(props){
        super(props);
        this.state = { // define this.state in constructor
            isEditing: false
        } 
    }
    render(){
        return <div></div>
    }
	}
	修改state属性的值
	通过this.setState({isEditing:true})的方式