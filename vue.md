# 入门

## 安装
[官方安装页面](https://cn.vuejs.org/v2/guide/installation.html "官方安装页面")
## 实例、模板、挂载点
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Morton的VUE学习</title>
    <script src="./vue.js"></script>
</head>
<body>
<div id="root">{{msg}}</div>
<script>
    new Vue({
        el:"#root",
        data:{
            msg:"hello world"
        }
    })
</script>
</body>
</html>
```
模板可以写在挂载点中，也可以写在vue实例中（template值）
## 数据、事件、方法
### 插值表达式
`{{}}`
模板中使用两个花括号的形式传递数据 
### v-text和v-html指令
**指令的内容是js表达式，能使用实例data项里的变量**
`<div v-text="content" id="root"><div>`
用这个指令指向一个数据，这个数据定义整个div的内容
### v-on指令
`<div id="root" v-on:click="handleClick">{{msg}}</div>`
指令指向一个函数，函数在vue对象中的methods中定义
```html
 methods:{
            handleClick:function(){
                alert(123);
            }
        }
```
**v-on可以简写成@符号，@click="handleClick"**
## 属性绑定和双向数据绑定
### v-bind
使用指令 v-bind:属性名=“”，可使属性和数据项绑定
v-bind: 可以缩写成 : （一个冒号）
`:title`
### v-model
标签的内容，和数据项是双向绑定的
## 计算属性和侦听器
computed:
定义变量由其它变量生成
![](http://120.79.159.236/wp-content/uploads/2020/01/10f647e799744d229a94c0f871556f32.png)
watch:
侦听变量发生变化,如果变化,就执行函数
![](http://120.79.159.236/wp-content/uploads/2020/01/e1ecf889e3f334e7c0b78eb8d95c2e80.png)
## v-if v-show v-for指令
v-if：如果数据为true，则从dom中移除
v-show：如果数据为true，则显示元素，否则隐藏（display：none）
v-for：![](http://120.79.159.236/wp-content/uploads/2020/01/85e1fe57edc370341d4ef89cbd9f0ba0.png)
添加key值提升效率
![](http://120.79.159.236/wp-content/uploads/2020/01/51e3c8a01b944113399af32bd608c61d.png)
key不可重复，下标可以，用这种方法获取下标来设置key值
![](http://120.79.159.236/wp-content/uploads/2020/01/05d1a023ec35da035dfa4037f6d55d56.png)
# 组件
全局组件
```html
Vue.component("组件名",{
	template:"<li>hh</li>"
})
```
可以使用<<组件名>>来创建元素

局部组件：
components项
![](http://120.79.159.236/wp-content/uploads/2020/01/5a8e0d9c202182b7b9f450cd8cbc05c2.png)

给组件传参
![](http://120.79.159.236/wp-content/uploads/2020/01/568a10fc960936b56bf579657b00b208.png)

父子组件的通信
子组件触发事件
this.$emit("事件名",this.参数)
父组件监听事件
指令 @事件名="父组件定义的函数名",在函数的定义中接受参数

## js数组
[js数组方法集合](https://blog.csdn.net/weixin_44477401/article/details/88687024)