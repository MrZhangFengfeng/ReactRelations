### url中#的作用
- #代表网页中的一个位置，其右边的字符就是该位置的标示符。
- 改变#不会触发网页重载
- 改变#会改变浏览器的访问历史---->会产生历史记录，会产生浏览器的前进与后退
- window.location.hash读取或者设置#值   
    - console.log(window.location.hash)  //'#/demo1'
    - window.location.hash = '#/demo2'   
    
- window.onhashchange = func  监听hash变化
    -  window.onhashchange = function(){...} //hash以改变触发函数

- 前端路由就是通过监听hash值的改变，去发送对应的ajax请求，进而更新页面。

- - - 
### react-route

react-route是一个基于react的一个路由库
- Router ： 路由器组件，它不是路由，是用来包含各个理由组件，是一个容器。
    - 属性 ： history={hashHistory},用来监听浏览器地址栏的变化，并将URL解析成一个地址对象，供React Router匹配
    - 子组件 ： Route

- Route ： 路由组件，注册路由。 path <----> component的对应关系。

      <Route path="/" component={APP}>

- IndexRoute ： 默认路由组件。    
    - 当父路由被请求时，默认就会请求此路由组件
    
- Link ：
    - 路由连接诶组件。动态生成一个a链接，指向一个分路由对应的组件。
    - 属性一：to="/XXX"
    - 属性二：activeClassName = "active"

- hashHistory ： 
    - 路由的切换由URL的hash变化决定，即URL的#部分发生变化
    - 用于Router组件的history属性
    - 作用：为地址url生成?_k=hash，用于内部保存对应的state
