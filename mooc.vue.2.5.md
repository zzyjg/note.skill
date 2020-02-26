# vue
--------------------------------

## 专用概念
1.挂载点 模板 实例
2.插值表达式 {{content}}
3.模板指令 v-html/v-text/... 
 <div v-html="content"></div>
 data: {content: "<h1>abc</h1>"}
4.模板指令-事件绑定 v-on: == @ 
 v-on:click="handleclick",可简写为@click="handelClick"
 methods: {
	 handleClick: function(){
		 this.content = "content modified!"
	 }
 }
5.模板指令-属性绑定 v-bind: == :
 v-bind:title="title",可简写为:title="title"
 data: {title: "this is a hw."}
 ****特别：绑定指的是vue的成员变量绑定到属性/事件等上，如属性‘X’绑定的是属性值，即变量（来自vue实例的data)。
6.双向数据绑定（页面内容与数据）v-model
7.计算属性（针对数据，不重复渲染效率高） computed
 computed: {
	 fullName: function(){
		 return this.firstName + " " + this.lastName
	 }
 }
8.侦听器(针对数据和计算属性) watch
 watch: {
	 fullName: function(){
		 this.count ++
	 }
 }
9.指令 v-if v-show v-for
 <div v-if="false">元素删除</div>
 <div v-show="false">元素隐藏</div>
 <li v-for="(item,index) of list" :key="index">{{item}}</li>

## 组件
0.组件的官方定义
 组件就是一个可复用的Vue实例
1.局部组件 需要注册才能使用/调用到
var TodoItem = {
	props: ['item'],
	template: "<li>{{item}}</li>"
}
new Vue(
	components: {
		"todoitem": TodoItem,
	}
)
2.全局组件 可以直接调用
Vue.component("todoitem",{
	props: ['item'],
	template: "<li>{{item}}</li>"
})
3.Vue的每个实例都是一个组件
 无论是根实例new Vue()还是嵌套的子组件实例todoitem，都是组件；
 根实例这个组件有点特别，它的template会通过挂载点el找到，并作为自己的模板。
4.组件注册两种相当的写法
 条件：组件名与注册使用名一致
 写法：new Vue({components: { App }}) ==  new Vue({components: { 'App': App }})
5.单文件组件（.vue文件)
 导出语法 export default { } , 不同于 new Vue({ }) 
 单文件组件的实例属性name无需定义（仅在递归调用和调试时有用，参API说明），组件名以文件名为准
 模板中的根挂载点亦无需定义
6.<style scoped></style>
scoped作用域修饰，让样式仅在本组件内生效，否则将全局有效

## 高级
1.data为什么return
 组件是一个可复用的实例，当你引用一个组件的时候，组件里的data是一个普通的对象，所有用到这个组件的都引用的同一个data，就会造成数据污染。
 将data封装成函数后（JS中只有函数才有作用域），在实例化组件的时候，我们只是调用了data函数生成的数据副本，避免了数据污染。
2.$emit
 this.$emit("delete",this.index)
3.Vue中调用时的$代表Vue自有的实例属性或方法
 vm.$data.a = ''
 vm.$watch('a',function(newValue,oldValue){})
4.$mount()
 Vue实例化时没有收到选项，可以使用$mount('#root')手动挂载到DOM元素（如root）
5.{render: h => h(App)} 等同于下面相应段内容  
 new Vue({
    render: function(createElement) {
        return createElement(App);
    }
 }).$mount('#app')
 作者解释为什么简写成'h'：
 单词hyperscript，通常用在virtual-dom的实现中。Hyperscript 本身是指生成HTML结构的script脚本
 
## CLI
npm install -g cnpm --registry=https://registry.npm.taobao.org
cnpm install -g @vue/cli
cnpm install -g webpack
vue ui //启动GUI

## Router
1.简洁router元素定义法，代码更清爽
 {
    path: '/b',
    component: () => import('../components/B.vue')
 }
2.router服务单页面应用，下例的<div id="nav"/>为公共区,路由子页面在<router-view/>里
 <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link style="color:red" to="/a">A页面</router-link> |
      <router-link style="color:red" to="/b">B页面</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
 </div>
3.地址栏hash和history模式
 hash：#后的变化不重复请求后台（对单页面应用有利），不存在404的问题，但地址栏传参、微信支付等不支持；
 history：具有对URL历史记录进行修改的能力，但需后台配合处理404错误。
4.注册一个全局前置守卫
 router.beforeEach((to, from, next) => {
   // ...
   // next: Function，一定要调用该方法来resolve 这个钩子。next() next(false) next('/') next({path:'/'})
 })
5.this.$router.push()两种参数方式：
 ({name: "course",params: {id: e.id}}); //name方式，在router定义中对应有路径，{path: "/course/:id",name: "course",...}
 ("./userCenter"); //path方式


## 零碎
@/  项目的src文件夹
./  当前目录，区别于上




