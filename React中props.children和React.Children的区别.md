## React中props.children和React.Children的区别

在React中，当涉及组件嵌套，在父组件中使用props.children把所有子组件显示出来。如下：

    class ParentComponent(props){
        return (
            <div>
                {props.children}
            </div>
        )
    }
    
### 如果想把父组件中的属性传给所有的子组件，该怎么做呢？

> 使用React.Children帮助方法就可以做到。

比如，把几个`Radio`组合起来，合成一个`RadioGroup`,这就要求所有的`Radio`具有同样的`name`属性值。可以这样设计：把`Radio`看做子组件，`RadioGroup`看
做父组件，`name`的属性值在`RadioGroup`这个父组件中设置。

首先是子组件：

    function RadioOption(props) {
      return (
        <label>
          <input type="radio" value={props.value} name={props.name} />
          {props.label}
        </label>
      )
    }   
    

然后是父组件，不仅需要把它所有的子组件显示出来，还需要为每个子组件赋上name属性和值：

    function renderChildren(props) {

      return React.Children.map(props.children, child => {
        if (child.type === RadioOption)
          return React.cloneElement(child, {
            name: props.name
          })
        else
          return child
      })
    }
    
    class RadioGroup(props) {
      return (
        <div>
          {renderChildren(props)}
        </div>
      )
    }

    class App() {
      return (
        <RadioGroup name="hello">
          <RadioOption label="选项一" value="1" />
          <RadioOption label="选项二" value="2" />
          <RadioOption label="选项三" value="3" />
        </RadioGroup>
      )
    }
