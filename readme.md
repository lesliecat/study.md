### Vue对象挂载
var vm = new Vue({
	el: '#app',
	data: {
	}
})
Vue要等dom加载完才能挂在，所以不能写在head里，要写在body script标签里面
### 箭头函数作用域 （this)

箭头函数本身没有this，this指向最近的外层作用域

### v-pre(对比v-html)
{{}}不会被编译

### 插值表达式可作简单运算
``` 
{{number/3}}
{{isOk ? '确定' : '取消'}}
```
- 只支持单个表达式，不支持语句 和 流控制

### 管道符 |
```

{{ message | capitalize }}

<!-- 在 `v-bind` 中 -->
<div v-bind:id="rawId | formatId"></div>
你可以在一个组件的选项中定义本地的过滤器：

filters: {
  capitalize: function (value) {
    if (!value) return ''
    value = value.toString()
    return value.charAt(0).toUpperCase() + value.slice(1)
  }
}
```
可以穿连
```
{{data | fun1 | fun2}}
{{data | fun(ar1, ar2)}}
```
ar1,ar2是传入的第二，三个参数，因为数据本身是第一个参数

### app外部调用
```
var app = new ({
		el: '#app',
		data: {},
		methods: {
			init() {
				console.log('diaoyong')
			}
		}
	})
app.init() 叫外部调用
```
### 计算属性
计算属性的调用可以用methods实现，但是计算属性有缓存，数组遍历时重绘不会重新计算，节省内存
另计算属性有复杂场景可以使用get(){ }  setter() {}
### class
对象绑定
数组绑定
data数据写样式绑定
### v-show
v-show 只是css display的切换，适合切换频繁的场景，v-if才是真的的条件渲染，会重载重绘
### v-for
数组遍历 可以用of替代 in,更符合js语法
book in filterBooks
可以不改变原数组，用计算属性来过滤使用副本数组
对象遍历 in
### match
item.name.match(/Javascript/)
match() 1
如何使用 match() 来检索一个字符串。
match() 2
如何使用 match() 来检索一个正则表达式的匹配。
``` 
<script type="text/javascript">

var str="1 plus 2 equal 3"
document.write(str.match(/\d+/g))

</script>
输出：

1,2,3
```
### 修饰符
.lazy  
change事件  data不是实时改变的，要等失焦或按enter键才改变
.number 会把值转变为数值型数据

### v-model
<input type="radio" value = "js">
value绑定的值默认显示值

### 组件
全局注册 Vue.component('name',{template:'<div></div>'})
局部注册 components: {
	name: {
	template: ''
}
}

porps 书第74页（重要）
 
子传父  @接收＝fun(val) 这里有个语法糖， this.$emit('input', '儿子传信息') v-model = 'val' 

### 组件之间通信
bus  创建Vue空实例
this.$parent this.$children可直接修改父子组件的内容（少用，不太符合单向数据流的定义）
### 子组件索引 $rel= 'comp1'
this.$resf.comp1.message
这是应急方案，只在组件渲染完才填充，且非响应式的，仅仅作为一个指节访问子组件的应急方案，应当避免在模板和计算属性当中使用

### nextTick

```
	this.$nextTick(_ => {

		})
```
进入Vue下一个队列，解决有时data数据改变，dom还未重绘

### <script type="text/x-template"></script>
```
<son></son>	
<script type="text/x-template">
	<div>这里可以写html，不用在template里面用字符串拼hmtl</div>
</script>
Vue.component('son',{
	template: "#son"
})



