

# Vue

[TOC]

## 一、Vue-CLI2

### 1、安装Vue脚手架

```shell
#安装vue2.x
npm install vue-cli -g

#安装vue3.x，我这里安装的是3.x
npm install @vue/cli -g
```

### 2、查看版本

```shell
vue --version
```

![](IMG/微信截图_20191013101849.png)

### 3、拉取2.x模板(旧模板)

- 拉取2.x模板，就可以即使用vue2.x版本，也可以使用vue3.x。

```shell
npm install @vue/cli-init -g
```

### 4、创建项目

#### 4.1、Vue CLI2

##### 4.1.1、Vue CLI2初始化项目

```shell
vue init webpack 项目夹名称
```

![](IMG/微信截图_20191013105301.png)

##### 4.1.2、查看生成好文件，并重命名为02-vuecli2test

![](IMG/微信截图_20191013105412.png)

##### 4.1.3、build和config文件夹

- build和config文件夹是配置webpack，例如：将config/index.js设置为true，自动打开浏览器。

  ![](IMG/微信截图_20191013150026.png)

#### 4.2、Vue CLI3初始化项目

```shell
vue creat 项目夹名称
```



## 二、Vue-CLI2

### 1、创建项目，测试ESLint规范

- 创建runtimecompiler项目

  ```shell
  vue init webpack runtimecompiler
  ```

  - 这个项目装了ESLint

  - ESLint规范代码
  - 关闭ESLint，在congif/index.js,将参数设置为false即可关闭。

  ![](IMG/微信截图_20191013154738.png)

  

- 创建runtimeonly项目

- 这里不装了ESLint

  ```shell
  vue init webpack runtimeonly
  ```

### 2、Runtime-Compiler和Runtime-Only区别

- runtimecompiler(V1)

  template -> ast -> render -> vdom ->UIR

- runtimeonly(V2)（1.性能更高 2.代码量更少）

  render -> vdom ->UI

#### 2.1、在01-runtimecompiler项目中，修改mai.js，测试render

```js
/*
 * @Description: henggao_learning
 * @version: v1.0.0
 * @Author: henggao
 * @Date: 2019-10-13 15:27:18
 * @LastEditors: henggao
 * @LastEditTime: 2019-10-14 08:40:53
 */
// The Vue build version to load with the `import` command
// (runtime-only or standalone) has been set in webpack.base.conf with an alias.
import Vue from 'vue'
// import App from './App'

Vue.config.productionTip = false

/* eslint-disable no-new */
const cpn = {
  template: '<div>{{message}}</div>',
  data () {
    return {
      message: '我是组件message'
    }
  }
}
new Vue({
  el: '#app',
  // components: { App },
  // template: '<App/>'
  render: function (createElement) {
    // 1. 普通用法：creatElement('标签',{标签的属性}，[''])
    // return createElement('h2', { class: 'box' }, ['Hello World', createElement('button', ['按钮'])])

    // 2. 传入组件
    return createElement(cpn)
  }
})

// - runtimecompiler(V1)
//   template -> ast -> render -> vdom ->UI
// - runtimeonly(V2)（1.性能更高 2.代码量更少）
//   render -> vdom -> UI

```



## 三、Vue-CLI3

- vue-cli 3与 2版本区别
  - 基于webpack 打造，vue-cli2基于webpack 3 
  - 设计原则“0配置”，移除了build和config等目录
  - vue-cli 3 提供了vue ui 命令，提供可视化
  - 移除了static文件夹，新增public，并将index.html移动到public

### 1、创建项目

```shell
vue create testvuecli3
```

![](IMG/微信截图_20191014090732.png)

- 通过空格选择

  ![](IMG/微信截图_20191014091104.png)

​		![](IMG/微信截图_20191014092037.png)

- 如果需要删除自己创建项目的默认配置

  ![](IMG/微信截图_20191014091801.png)

  - 找到C:\Users\ghg\.vuerc，删除以下内容。

  ![](IMG/微信截图_20191014091530.png)

### 2、查看目录

![](IMG/微信截图_20191014092435.png)

### 3、用户图形界面UI

- 本地服务器

```shell
vue ui
```

![](IMG/微信截图_20191014094033.png)



### 4、新建配置

- 如果需要修改自己独有的配置，在项目里新建`vue.config.js`,必须是这个名称。

- 提交到本地git仓库

  - 查看修改

    ```shell
    git status
    ```

    ![](IMG/微信截图_20191014110209.png)

  - 提交到本地git仓库

    ```shell
    git add .
    git commit -m 'henggao'
    ```

- `vue.config.js`

  ```js
  module.exports = {
      
  }
  ```
  - 提交到本地git仓库

  ```
  git add .
  git commit -m 'henggao'
  ```



## 四、箭头函数

### 1、箭头函数的基本使用

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
 <script>
    //  箭头函数：也是一种定义函数的方式
    // 1. 定义函数的方式
    const aaa =function(){

    }

    // 2. 对象字面量中定义函数
    const obj = {
        bbb(){

        }
    }

    // 3. ES6中箭头函数
    // const ccc = (参数列表) =>{      
    // }
    const ccc = () =>{

    }
    
</script>   
</body>
</html>

```



### 2、箭头函数和返回值

```html
<!--
 * @Description: henggao_learning
 * @version: v1.0.0
 * @Author: henggao
 * @Date: 2019-10-14 11:11:48
 * @LastEditors: henggao
 * @LastEditTime: 2019-10-14 13:49:30
 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
<script>
    // 1. 参数问题
    // 1.1 放入两个参数
    const sum = (num1,num2) =>{
        return num1 + num2
    }
    // 1.2 放入一个参数
    const power= num => {
        return num * num
    }

    // 2. 函数中
    // 2.1 函数代码有多行代码时
    const test = () => {
        // 1. 打印Hello World
        console.log('Hello World');
        
        // 2. 打印Hello Vue
        console.log('Hello Vue');
    }

    // 2.2 函数代码块中只有一行代码
    // const mui = (num1, num2) =>{
    //     return num1 + num2
    // }
    const mul = (num1,num2) => num1 + num2
    console.log(mul(20,30));

    // const demo = () => {
    //     console.log('Hello Demo')
    // }
    const demo = () => console.log('Hello Demo')
    console.log(demo());
    
</script>
</body>
</html>
```

### 3、箭头函数中this的使用

```html
<!--
 * @Description: henggao_learning
 * @version: v1.0.0
 * @Author: henggao
 * @Date: 2019-10-14 13:50:25
 * @LastEditors: henggao
 * @LastEditTime: 2019-10-14 14:11:37
 -->
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>

<body>
    <script>
        //  是么时候用箭头
        // setTimeout(function (){
        //     console.log(this);
        // },1000)

        // setTimeout(( ) => {
        //     console.log(this);
        // },1000)

        // 问题： 箭头函数中的this是如何查找的？
        // 答案：向外层作用域中，一层层查找this，直到有this的定义 
        //  const obj ={
        //      aaa() {
        //          setTimeout(function(){
        //              console.log(this);  //window
        //          })

        //          setTimeout(() => {
        //              console.log(this);  //obj对象
        //          })
        //      }
        //  }


        const obj = {
            aaa() {
                setTimeout(function () {
                    setTimeout(function () {
                        console.log(this); //window
                    })

                    setTimeout(() => {
                        console.log(this); //window
                    })
                })

                setTimeout(() => {
                    setTimeout(function () {
                        console.log(this); //window
                    })

                    setTimeout(() => {
                        console.log(this); //obj对象
                    })
                })
            }
        }

        obj.aaa()
    </script>
</body>

</html>
```

![](IMG/微信截图_20191014141200.png)

## 五、Vue-Router

### 1、vue-cli2创建项目

```shell
vue init webpack learnvuerouter
```

- 路由
  - 内网IP
  - 公网IP

#### 1.1、后端渲染

- jsp（java server page）
- 后端路由

  - 后端处理URL和页面之间的映射关系。

    ![](IMG/微信截图_20191014182843.png)

#### 1.2、前后端分离

- 前端渲染

  - 浏览器中显示的网页中的大部分内容，都是有前端写的js代码在浏览器中执行，最终渲染出来的网页。

  - 前后端分离

    ![](IMG/微信截图_20191014182913.png)

#### 1.3、SPA页面

- SPA(single page web application)单页面富应用阶段

- 整个网站只有一个页面

  ![](IMG/微信截图_20191014182937.png)

### 2、URL的Hash和HTML5的history

#### 2.1、URL的Hash

- 修改location.hash来改变href，但网页不发生刷新。

  ```js
  location.hash = 'aaa'
  ```

  ![](IMG/微信截图_20191014183830.png)

#### 2.2、HTML5的history

##### 2.2.1、pushState

- 类似栈结构，可以返回back

```js
history.pushState({},'','about')

history.back()
```

![](IMG/微信截图_20191014184111.png)

##### 2.2.2、replaceState

- 不可以返回

```js
history.replaceState({},'','home')
```

##### 2.2.3、go

- go可以回退，前进。

  - history.go(-1) 等价于history.back()
  - history.go(1)等价于history.forward()

  ```js
  history.go(-1)
  
  history.go(-2)
  
  history.go(2)
  ```

  

### 3、vue-router

#### 3.1、安装路由

```shell
npm install vue-router --save
```

- 使用脚手架已经创建

  ![](IMG/微信截图_20191014185706.png)

- 查看main.js

  ![](IMG/微信截图_20191014185756.png)

- 如果手动安装

  - 在src/router/index.js搭建路由框架

  - index.js

    ```js
    // 配置路由相关的信息
    import Vue from 'vue'
    import VueRouter from 'vue-router'
    
    // 1.通过Vue.use(插件),安装插件
    Vue.use(VueRouter)
    
    // 2.创建VueRouter对象
    const routes = [
      
    ]
    const router = new VueRouter({
      // 配置路由和组件之间的应用关系
      routes
    })
    
    // 3.将router传入到到Vue实例
    export default router
    ```

  - 在main.js进行挂载

  - main.js

    ```js
    import Vue from 'vue'
    import App from './App'
    import router from './router'  //默认到index
    // import router from './router/index'
    
    Vue.config.productionTip = false
    
    /* eslint-disable no-new */
    new Vue({
      el: '#app',
      router,
      render: h => h(App)
    })
    ```

    

#### 3.2、路由映射配置

1、删除src/components里的默认文件HelloWorld.vue,创建自己的文件Home.vue、About.vue

- Home.vue

  ```vue
  <template>
    <div>
        <h2>我是Home</h2>
        <p>我是Home内容，哈哈哈</p>
    </div>
  </template>
  
  <script>
  export default {
      name:"Home"
  }
  </script>
  
  <style>
  
  </style>
  ```

- About.vue

  ```vue
  <!--
   * @Description: henggao_learning
   * @version: v1.0.0
   * @Author: henggao
   * @Date: 2019-10-14 19:13:59
   * @LastEditors: henggao
   * @LastEditTime: 2019-10-14 19:13:59
   -->
  <template>
    <div>
        <h2>我是About</h2>
        <p>我是About内容，呵呵呵</p>
    </div>
  </template>
  
  <script>
  export default {
      name:'About'
  }
  </script>
  
  <style>
  
  </style>
  ```

2、删除src/App.vue里的默认配置

- App.vue

  ```vue
  <template>
    <div id="app">
  
    </div>
  </template>
  
  <script>
  export default {
    name: 'App'
  }
  </script>
  
  <style>
  
  </style>
  
  ```

3、配置映射关系

一个映关系就是一个对象

- src/router/index.js

  ```js
  import Vue from 'vue'
  import VueRouter from 'vue-router'
  import Home from '../components/Home.vue'
  import About from '../components/About.vue'
  
  // 1.通过Vue.use(插件),安装插件
  Vue.use(VueRouter)
  
  // 2.创建VueRouter对象
  const routes = [
    {
      path:'/home',
      component:Home
    },
    {
      path:'/about',
      component:About
    }
    
  ]
  const router = new VueRouter({
    // 配置路由和组件之间的应用关系
    routes
  })
  
  // 3.将router传入到到Vue实例
  export default router
  
  ```

  ![](IMG/微信截图_20191014194013.png)

#### 3.3、使用路由

##### 3.3.1、router-link

router-link会被渲染为a标签

- App.vue

  ![](IMG/微信截图_20191015171004.png)

- 运行

  ```shell
  npm run dev
  ```

  ![](IMG/微信截图_20191015171110.png)

##### 3.3.2、使用router-view占位

- App.vue

![](IMG/微信截图_20191015171426.png)

- 查看

  ![](IMG/微信截图_20191015171458.png)

##### 3.3.3、默认打开路径

- src/router/index.js

  ![](IMG/微信截图_20191015172417.png)

- 查看，默认打开 http://localhost:8080/#/home 

![](IMG/微信截图_20191015172507.png)

##### 3.3.4、路由的默认值改为history模式

- 去掉网址中的`#`

![](IMG/微信截图_20191015172849.png)

- src/router/index.js

  ![](IMG/微信截图_20191015173009.png)

- 查看

  ![](IMG/微信截图_20191015173052.png)

##### 3.3.5、router-link补充

1、渲染为button

![](IMG/微信截图_20191015184204.png)

查看

​	![](IMG/微信截图_20191015184224.png)

2、使用replace属性

![](IMG/微信截图_20191015184517.png)

重新打开网页，点击`首页`、`关于`，无法返回

![](IMG/微信截图_20191015184623.png)

3、渲染点击按钮

3.1、当点击按钮时，会出现 `class=“router-link-exact-active router-link-active ”`

![](IMG/微信截图_20191015185246.png)

3.2、根据上面这个class设置样式，使得点击的时候按钮变红。

- App.vue

![](IMG/微信截图_20191015185434.png)

3.3、查看

![](IMG/微信截图_20191015185531.png)

3.4、如果相将 router-link-active修改成ative

- App.vue

![](IMG/微信截图_20191015185937.png)

查看

![](IMG/微信截图_20191015190010.png)

一般开发的时候不用修改。

3.5、如果需要统一修改的样式比较多

![](IMG/微信截图_20191015190408.png)

只需要在router/index.js,修改如下信息

![](IMG/微信截图_20191015190528.png)

查看

![](IMG/微信截图_20191015190622.png)

##### 3.3.5、通过代码跳转路由

vue-router源码中所有组件都有一个router属性。

![](IMG/微信截图_20191015191238.png)

查看

![](IMG/微信截图_20191015191342.png)

- push =>pushState，这个可以返回、前进。

可以通过replace设置属性

![](IMG/微信截图_20191015191843.png)

重新打开网页，点击按钮后，查看，不可以返回、前进。

![](IMG/微信截图_20191015192003.png)

