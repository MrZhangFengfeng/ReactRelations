## title为string类型，且是必需的。

    title: React.PropTypes.string.isRequired

- - -

## React.findDOMNode()

组件并不是真实的 DOM 节点，而是存在于内存之中的一种数据结构，叫做虚拟 DOM （virtual DOM）。只有当它插入文档以后，才会变
成真实的 DOM 。根据 React 的设计，所有的 DOM 变动，都先在虚拟 DOM 上发生，然后再将实际发生变动的部分，反映在真实 DOM上，
这种算法叫做 DOM diff ，它可以极大提高网页的性能表现。

但是，有时需要从组件获取真实 DOM 的节点，这时就要用到 React.findDOMNode 方法：

    class MyComponent extends React.Component({
      handleClick() {
        React.findDOMNode(this.refs.myTextInput).focus();
      },
      render() {
        return (
          <div>
            <input type="text" ref="myTextInput" />
            <input type="button" value="Focus the text input" onClick={this.handleClick} />
          </div>
        );
      }
    });
    React.render(
      <MyComponent />,
      document.getElementById('example')
    );
    
上面代码中，组件 MyComponent 的子节点有一个文本输入框，用于获取用户的输入。这时就必须获取真实的 DOM 节点，
虚拟 DOM 是拿不到用户输入的。为了做到这一点，文本输入框必须有一个 ref 属性，然后 this.refs.[refName] 就
指向这个虚拟 DOM 的子节点，最后通过 React.findDOMNode 方法获取真实 DOM 的节点。

需要注意的是，由于 React.findDOMNode 方法获取的是真实 DOM ，所以必须等到虚拟 DOM 插入文档以后，才能使用这个
方法，否则会返回 null 。上面代码中，通过为组件指定 Click 事件的回调函数，确保了只有等到真实 DOM 发生 Click 
事件之后，才会调用 React.findDOMNode 方法。

- - -

## React 表单

用户在表单填入的内容，属于用户跟组件的互动，所以不能用 this.props 读取。

    class Input extends React.Component({
      constructor(props){
          super(props);
          this.state = {
              value='hello'
          };
      }
      handleChange: function(event) {
        this.setState({value: event.target.value});
      },
      render: function () {
        var value = this.state.value;
        return (
          <div>
            <input type="text" value={value} onChange={this.handleChange} />
            <p>{value}</p>
          </div>
        );
      }
    });

    React.render(<Input/>, document.body);
    
上面代码中，文本输入框的值，不能用 this.props.value 读取，而要定义一个 onChange 事件的回调函数，
通过 **event.target.value** 读取用户输入的值。textarea 元素、select元素、radio元素都属于这种情况。

- - -

## React_Ajax

组件的数据来源，通常是通过 Ajax 请求从服务器获取，可以使用 componentDidMount 方法设置 Ajax 请求，等到
请求成功，再用 this.setState 方法重新渲染 UI。
    
    class UserGist extends React.Component ({
        constructor(props){
          super(props);
          this.state = {
              username: '',
              lastGistUrl: ''
          };
      }
      componentDidMount: function() {
        $.get(this.props.source, function(result) {
          var lastGist = result[0];
          if (this.isMounted()) {
            this.setState({
              username: lastGist.owner.login,
              lastGistUrl: lastGist.html_url
            });
          }
        }.bind(this));
      },

      render: function() {
        return (
          <div>
            {this.state.username}'s last gist is
            <a href={this.state.lastGistUrl}>here</a>.
          </div>
        );
      }
    });
    React.render(
      <UserGist source="https://api.github.com/users/octocat/gists" />,
      document.body
    );
上面代码使用 jQuery 完成 Ajax 请求，这是为了便于说明。React 没有任何依赖，完全可以使用其他库。

- - -

## 单向数据绑定

可以从this.state来修改页面的值，不能从页面来修改state的值。
- - -
## props

properties的简写

- - -
## ...

    let arr1 = [1,2,3];
    let arr2 = [4,...arr1,5];
    console.log(arr2);//[4, 1, 2, 3, 5]
    
    
    let info={name:'winter',age:24}
    ReactDom.render(<MyComponent {...info}>,document.getElementById('app'));
    
- - -
## defaultProps

MyComponent.defaultProps中属性会自动填充到props中。
    
- - -
## class DateTimePicker extends Input

    class DateTimePicker extends Input{
        constructor(props){
            super(props)// Input 的 properties
        }
    }
    
- - -
## ref属性(references)
- 组件内部的标签都可以用ref属性来表示自己，就好像外部标签的id一样。
- 在组件中可以通过this.refs.refName来获取对应的真实DOM。
- 作用：用于操作指定的ref属性对应的DOM对象

    <input ref='winter'>
    this.refs.winter//返回input对象

## react 事件
- 通过onXxx来指定组件的事件处理函数
	react使用的是自定义（合成）事件，而不是使用真实的DOM事件。
		比如 onClick 就是react封装的，而不是本身的原始的onclick事件。
   	react中事件是通过委托方式处理的（委托给组件的最外层元素）。


- 通过event.target得到发生事件的DOM元素对象
	<input onFocus = {this.handleFocus} />
	handleFocus(event){
		event.target   //返回input对象
	}


## 事件委托：
什么是事件委托。比如说ul里有很多li 然后我需要给每个li都有一个事件监听，
那么我直接给ul来添加事件监听就好，免得给多个Li添加,这就叫做事件委托。


## this

- 再组件内自定义的方法中的this为null。
- 强制绑定this。
- es6语法无需绑定this，因为他自身没有this，用的是外部的this。
