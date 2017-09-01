###　setState是异步的
> `setState`可以接受第二个参数作为异步操作结束后的回调函数

`setState` 异步批量执行，所以存在点延迟，如果想得到正确的结果可以这样写

    let self = this;
    setTimeout(function() {
    self.state.text === 'new' ? self.setState({text: 'changed'}) : self.setState({text: 'delay'})
    },0);

- - -
### 注意
- 绝对不要直接改变 `this.state`  ,因为在之后调用`setState()`可能会冲掉你所做的更改。把`this.state`当做不可变的。

- `setState()` 不会立即改变`this.state`，而是创建一个即将处理的`state`转变。在调用该方法之后获取`this.state`的值可能
会得到现有的值，而不是最新的值。

- `setState()`不保证调用的同步性，为了提升性能，可能会批量性执行更改。

- `setState()`将总是触发一次重绘，除非在`shouldComponentUpdate()`里面实现了条件渲染逻辑。如果使用可变的对象，但是
又不能在`shouldComponentUpdate()`里面实现这种逻辑，仅在新`state`和旧`state`之间存在差异的时候调用`setState()`将会避免
不必要的重新渲染。

- - -

