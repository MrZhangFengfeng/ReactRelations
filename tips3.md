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
写大括号其实是解构赋值，如果react不是默认暴露，就需要{}
 
     import {react} from "react";
    
当react是默认暴露的时候，就不需要{}。

     export default react
     import react from "react";

