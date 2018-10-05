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