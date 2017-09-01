React是数据驱动的，所以不会轻易的去操纵DOM。如果要操纵DOM，就要用到ref这个属性。

> 所有有ref属性的真实DOM都会被收集在refs里。

    <div ref="progressBar" onClick={this.changeProgress}>
    changeProgress(e){
        let progressBar = this.refs.progressBar;
    }

这样就获得了真实的progressBar的DOM元素。

- - -
### 组件之间通信
组件之间的相互通信通过事件的发布订阅。

- - -
### 父组件调用子组件内的数据
父：

    render(){
        return (
            <div>
                <Header />
                <div id="player"></div>
                <Progress progress = {this.state.progress} onProgressChange = {this.progressChangeHandler}/>
            </div>           
        )
    }

    progressChangeHandler(progress){
        console.log(progress)
    }

子：

    <div className="components-progress row" ref="progressBar" onClick={this.changeProgress.bind(this)}>
    
- - -

