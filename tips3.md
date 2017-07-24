### 就近原则
就近原则，就是将一个组件的js 和css放到一个文件夹下，方便对应的修改。

- - -
### 使用脚手架工具创建一个react应用
- react脚手架
  - react专门提供了一个用于创建react项目的脚手架工具：create-react-app
  - 项目的整体技术架构为：webpack + react  + es6 +  eslint

- 创建项目并启动

      npm install -g create-react-app
      create-react-app my-app
      cd my-app/
      npm start
      
 
 
- - -
### import {}
写大括号其实是解构赋值，如果Component不是默认暴露，就需要{},相当于取react.Component
 
     import {Component} from "react";
    
当react是默认暴露的时候，就不需要{}。

     export default react
     import react from "react";
 
- - -
### react的配置你是怎么配置的
- 有脚手架工具帮助配置
- 项目经理
- 我也看过一些相关配置，如。。。
 
- - -
### 自定义时间处理
- npm i pubsub-js --save

消息的发布与订阅：pubsub.js

- PubSub.subscribe("事件名",function(eventName,data){});
- PubSub.publish("事件名",data)
 
- - -
### 项目打包运行
#### 项目编译打包并运行
- npm run build --->打包生成build文件夹及资源
- npm i -g pushstate-server  --->安装一个全局静态服务器
- pushstate-server build --->部署运行build文件
- 访问http://localhost：9000

- npm start这种方式是将项目在内存中运行的，不会生成build文件。

#### 配置sass预编译器环境
- 使用工具包：create-react-app-sass
- npm i create-react-app-sass --save -dev
- 修改package.json(参见其github)




