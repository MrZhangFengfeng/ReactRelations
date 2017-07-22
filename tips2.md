### 受控组件
react是一个单项数据流，但是可以自定义双向数据流组件(受控组件)。

通过event.target.value来获取输入框的值，然后同步setstate到受控标签内。

- - - 
### 导入js库
- react.js : React对象
- react-dom ：ReactDOM对象

- - -
### JSX
- 全称javascript XML
- react定义的一种类似于XML的JS扩展语法：XML+JS
- 作用：用来创建爱你react虚拟DOM(元素)对象
- JS中可以直接套标签,标签内部嵌套JS需要{...}
- 在解析显示数组时，会自动遍历显示
- 把数据的数组转换为标签的数组

- - -

### Component
react 是面向组件化编程的(组件化编码开发)，而非面向对象编程。
创建组件类
  
方式1，无状态函数------最简洁，适合写简单的组件

      function MyComponent(){
        return <div>summer</div>
      }
    
方式2：es6语法-----复杂组件推荐使用

    class MyComponent wxtends React.Component{
      render(){
        return(
          <div>
            <div>summer</div>
          </div>
        )
      }
    }
    
方式3：es5语法-----老语法，不推荐使用
    
      var MyComponent = React.createClass({
        render(){
            return(
              <div>
                <div>summer</div>
              </div>
            )
        }
      })   

- - -
### ReactDOM.render()渲染组件的基本流程
- react内部会创建组件实例对象
- 得到虚拟DOM并解析为真实DOM
- 插入到指定页面的元素内部。


- - -
### props
- 所有组件标签的属性的集合对象
- 给标签指定属性，保存外部数据(可能是一个function)
- 在组件内部读取属性


- - -
### 组件由什么组成？
- html
- css
- js
还是这基本的

- - -
### hook函数
- 所谓的钩子函数也就是回掉函数
- react为每个状态都提供了两种钩子函数，will函数和did函数

- - -
### render
- 每次更新都会render，每次setstate都会render。。。会render好多次
- compomentWillMount和compomentDidMount在一个生命周期内只会执行一次
- compomentWillUpdate和compomentDidUpdate会执行多次

- - -
### 删除组件
- ReactDOM.unmountComponentAtNode(document.getElementById('demo')); ----主动去移除组件，不属
于生命周期内的。可以通过js来控制去移除。
- componentWillUnmount()----组件将要被移除，属于生命周期内的

- - -
### 注意
- 一般会在compomentDidMount中开启监听，发送ajax请求。
- 可以在componentWillUnmount()中进行一些收尾工作，比如移除定时器，移除监听等等

- - -
### componentWillReceiveProps
- 

- - -
### this.attr
如果要在组件内多个方法里用到一个变量或者常量。
- 放在constructor里
- 定义到this上。this.attr






