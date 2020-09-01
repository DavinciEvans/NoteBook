# commonJS 和 ES6

commonJS 的导入：

`require(moduleA)`

导出：

`module.exports = {A: A, B: B, Func: Func}`

ES6 的导入：

`import * as X from ./example.js`

会将所有导入对象放入 X 当中

`import {A, B} from "./example.js`

导出：

`export {A, B, C}`

或者定义变量、函数、类时

`export let a = "Hello!`

`export function() {alert("Good Morning!")}`

导出默认值：使用 `default`

`export default address`

ES6 需要在 Html 引入 script 时设置属性 `type=module`