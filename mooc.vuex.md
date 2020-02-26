# vuex
------------------------------
## 基础
1.组成
 State：数据仓库；
 getter:派生出一个新的State；
 Mutation：本质是function，专注修改数据，一定是同步的；由commit()完成调用；
 Action：提交Mutation，业务代码+可以异步请求+不能直接操作State；由dispatch()完成调用；
 Module：模块化。
2.import默认识别
 import store from './store' 等同于 import store from './store/index'，即默认自动识别为'store.js'和'store/index.js'；
 import后紧跟的store为变量定义，可任意，下引用同步即可，与导出模块文件定义中的"export default new Vuex.Store({"无关。

 
## 高级
1.store解构 map...  mapGetters mapState
 import {mapGetters} from 'vuex'
 进行解构：
 computed: {
	 ...mapGetters(['memberInfo'])
 }
 简洁使用：
 {{memberInfo}} 代替之前的 {{this.$store.getters.memberInfo}}
 深入说明：
 以...mapState(['vipCategory'])举例，vipCategory在模板中通过{{}}取值使用；在script中通过this.vipCategory使用，或仍通过this.$store.state.vipCategory调用。

## state进阶
1.访问未定义的state成员，控制台不会报错，要注意
 如 const vipCategory = this.$store.state.vipCategory; ，vipCategory不存在也不会报错。
2.computed与mapState
 当一个组件需要获取多个状态时候，将这些状态都声明为计算属性会有些重复和冗余。为了解决这个问题，我们可以使用 mapState 辅助函数帮助我们生成计算属性，让你少按几次键。
 computed: {
    ...mapState(["vipCategory", "vipLevel"]),
    ...mapGetters(["vipInfo"])
 }
3.vuex仍然不应该组件保有局部状态
 虽然将所有的状态放到Vuex会使状态变化更显式和易调试，但也会使代码变得冗长和不直观。如果有些状态严格属于单个组件，最好还是作为组件的局部状态。

## 运行环境
1.ESLint - 关闭对console和未使用变量的校验
 "rules": {
       "no-console": "off",
       "no-unused-vars": [2,{
         "vars": "local", 
         "args": "none"
       }]
     }

2.安装less-loader
 npm install less less-loader --save-dev
3.
 
