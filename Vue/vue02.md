# Vue

[TOC]

## 一、事件监听

### 1、v-on基本使用

- `v-on:click`

- `@click`

```html
<!--
 * @Description: 
 * @version: 
 * @Author: henggao
 * @Date: 2019-10-08 10:13:23
 * @LastEditors: henggao
 * @LastEditTime: 2019-10-08 20:30:42
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
<div id="app">
    <h2>{{counter}}</h2>
    <button v-on:click='counter++'>+</button>
    <button v-on:click='counter--'>-</button>
    <button v-on:click='increment'>+</button>
    <button v-on:click='decrement'>-</button>
    <button @click='increment'>+</button>
    <button @click='decrement'>-</button>
</div>
<script src="../js/vue.js"></script>   
<script>
    const app = new Vue({
        el:'#app',
        data:{
            message:'Hello,Vue!',
            counter : 0
        },
        methods:{
            increment(){
                this.counter++
            },
            decrement(){
                this.counter--
            }
        }
    })
</script>
</body>
</html>
```

### 2、v-on的参数问题

```shell
<!--
 * @Description: 
 * @version: 
 * @Author: henggao
 * @Date: 2019-10-08 10:13:23
 * @LastEditors: henggao
 * @LastEditTime: 2019-10-08 20:55:32
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
<div id="app">
    <!-- 事件调用的方法没有参数 -->
    <button @click='btn1Click()'>按钮1</button>
    <button @click='btn1Click'>按钮2</button>
    
    <!-- 在事件定义时,写函数时省略了小括号，但方法本身是需要一个参数的，这个时候Vue会默认将浏览器的event事件作为参数传入到方法 -->
    <button @click='btn2Click(123)'>按钮3</button>
    <button @click='btn2Click'>按钮4</button>   
    
    <!-- 方法定义时，需要event对象，同时又需要其他参数 -->
    <!-- 在调用方式，如何手动的获取到浏览器参数event对象： $event -->
    <button @click='btn3Click(123, $event)'>按钮5</button>   
    <button @click='btn3Click(abc, $event)'>按钮6</button>   

</div>
<script src="../js/vue.js"></script>   
<script>
    const app = new Vue({
        el:'#app',
        data:{
            message:'Hello,Vue!',
            abc:666
        },
        methods:{
            btn1Click(){
                console.log("btn1Click");
            },
            btn2Click(event){
                console.log('----',event)
            },
            btn3Click(abc,event){
                console.log('++++',abc , event)
            }
        }
    })
</script>
</body>
</html>
```

