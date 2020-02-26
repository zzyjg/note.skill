
## ES6
1.data () {}
写法相当于 data: function(){}
2.async作用是避免进入回调地狱
>定义(async要配合await和try...catch使用，注意这些关键字位置是紧靠函数前)：
let HTTP {}
HTTP[key] = async function() {
	let res = null
	try {
		res = await axios.get('/contactList')
	}catch(err){
		res = err
	}
	return res
}
>调用(这时才体现如何避免回调地狱的，调用时必须对应出现async,await，注意这些关键字位置是紧靠函数前）：
 async getList(){
    let res = await this.$Http.getContactList()
    this.list = res.data //只需要另起行这么写，即可接收res进行处理，更自然
 }
3.import export webpack
 export可导出多个模块（import时要加{ }），export default只能导出一个；
 export与export default均可导出常量、函数、文件、模块等；
 Vue是通过webpack实现的模块化，因此可以使用import来引入模块;
 模块可以省略 ".js"，".vue"，“.json” 后缀，webpack 会在之后自动添加上；可以用 "@" 符号代替 "src" 字符串等。

## 高级JS 
1.**JS将字符串作为函数调用的方法**
方法[1]：把方法名当成属性名
因函数在JS里面可以被保存在对象中，因此通过对象的属性访问,调用字符串方法;
又因属性访问可以使用.标记法或者[]标记法。其中使用.访问需要标识符，[]访问使用的是标识符对应的字符串.
 function test(str) {alert(str);}
 Window[test]('OK');
方法[2]：利用函数eval()
 eval(test+'('+'OK'+')')

2.Axios
 基于Promise的HTTP库，相当于Ajax等。
 
## vscode常用快捷键
1.alt+shift+F 格式化代码
2.alt+shfit+A 块注释
3.ctrl/command+/ 行注释
4.ctrl/command+enter 下插入一行，+shift上方插入一行，无论光标在何处

## vscode必装插件
chinese simplified
vetur 					//vue提示
ESlint					//JS-ES6代码规则检查工具，已替代JSHint/JSLint
CSS Peek				//html与css的链接导航
Icon Fonts				//font awesome（即FA-...）等常用字体的输入提示
Cobalt2 theme official	//相中的主题（火）
vscode-icons			//相中的工作区图标（CSS3等文件夹及文件图标组织显示）
## vscode选装插件
1.Auto Rename Tag		//自动重命名标签，即改动头，对应尾自动改
2.HTML Boilerplate		//基本HTML5标签模板
3.color info			//颜色值工具。移动到颜色值自动显示多表达类型、图形选择等，可点击编辑
4.Auto close tag		//自动闭合标签。前面有一半标签，下面/时自动发现并闭合，一般用于检查代码是否有对应遗漏问题
5.HTML CSS support		//HTML中CSS Class的智能提示

## git
//配置
Git config —global user.name ‘zzyjg’

//克隆远程仓库到本地仓库
Git clone/fetch ‘’
//签入更改到本地仓库
Git add index.js	
Git commit -m ‘message is needed’ 
//推送本地仓库更改到远程仓库
Git push 

//拉取远程仓库更新到工作区（协作开发）
Git pull 
//签出本地仓库文件到工作区（误删等操作后的重新签出动作）
Git checkout index.js 
 
## 错误排除
1.代码错误 Mixed spaces and tabs
不允许空格和Tab同时存在!
