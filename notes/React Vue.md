---
layout: notes
---

<img src= "./zPhoto/Frontend_Diagram.png" />

#React
```
<script src="https://fb.me/react-15.1.0.js"></script>
<script src="https://fb.me/react-dom-15.1.0.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.34/browser.min.js"></script>
```

{ } 表示 JavaScript
< > 表示 HTML
<a ref = "aa" >fsfsdfsd</a>

```
<div className="Comment">    // give Class to div 

var Content = React.createClass({
	componentWillMount: function() {   }
	
ReactDOM.render(
<Content />,
document.getElementById('example')
);
```

### Loop - Map 
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map((number) => number * 2);
console.log(doubled);     //[2, 4, 6, 8, 10]


### 命名规则
在组件的callback中，为每个函数都加上 on 作为前缀，比如 onCreateRplay
在改变 state 的 reducer 中加上 applay 作为前缀，比如 applyCreateReply
在 selector 中 加上 get 作为前缀，比如 getReply
在 action creator 中加上 do 作为前缀，比如 doCreateReply

##ECMAScript 6
### Class
constructor(props) {
super(props);
}
Module
Default Export
class Button extends React.Component {   }
export default Button;
import Button from './Button';



## Component  
```
// React ES6 class
class TodoItem extends React.Component { 
... }
// functional stateless component
function TodoItem() { 
... } 
```
1. 所有component 都有render



```
var HelloMessage = React.createClass({
  render: function() {
    return <h1>Hello {this.props.name}</h1>;
  }
});

ReactDOM.render(
  <HelloMessage name="John" />,
  document.getElementById('example')
);   
```

### Events
```
<button onClick={this.function()}     />
<input  onChange={this.handleChange}  />
<form   onSubmit={this.handleSubmit} >     
</form>
<textarea value={this.state.value} onChange={this.handleChange} />
```

## Props 
######  Props are Read-Only
Props tag  中间的属性，不需要初始化

```
<Button name="+" clickHandler={this.handleClick} orange />
```
props初始值: 	getDefaultProps
设置属性: 		setProps
替换属性: 		replaceProps

### PropTypes      检测属性  

```
Button.propTypes = {
  name: React.PropTypes.string,
  orange: React.PropTypes.bool,
  clickHandler: React.PropTypes.func,
};
```

## State
state初始值: 	getInitialState 
设置状态: 		setState
替换状态: 		replaceState

### 'Buttom_Like':  点击改变状态 
``` 
var LikeButton = React.createClass({
  getInitialState: function() {
    return {liked: false};
  },
  handleClick: function(event) {
    this.setState({liked: !this.state.liked});
  },
  render: function() {
    var text = this.state.liked ? 'Buttom_Like' : 'Buttom_Dislike';
    return (
      <p onClick={this.handleClick}>
       {text}
      </p>
    );
  }
});

ReactDOM.render(
  <LikeButton />,
  document.getElementById('example')
);
```

## Form表单   
用户跟组件的互动，所以不能用 this.props 读取
### onChange
onChange={this.handleChange}
handleChange: function(event){ event.target.value; }

```
<input type="text" value={value} onChange={this.handleChange} />
Ex:
var Input = React.createClass({
  getInitialState: function() {
    return {value: 'Hello!'};
  },
  handleChange: function(event) {
    this.setState({value: event.target.value});
  },
  render: function () {
    var value = this.state.value;
    return (
      <div>
        <input type="text" value={value} onChange={this.handleChange} />
        <p>{value}</p>
      </div>
    );
  }
});
ReactDOM.render(<Input/>, document.body);
```
### onClick
### Submit 
```
handleSubmit(event) {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
}
```
## API  
强制更新: 		forceUpdate
获取DOM节点: 	findDOMNode
判断组件挂载状态: isMounted

## 生命周期 Mount
<img src="zPhoto/React-LifeCycle.png"/>
componentWillMount()	render前调用, once only
componentDidMount()		render后调用, once only
componentWillUnmount()	移除时调用
componentWillReceiveProps(object nextProps)	新加props调用
shouldComponentUpdate(object nextProps, object nextState) 
新props调用前
componentWillUpdate(object nextProps, object nextState)
新的 props 或者 state 之前立刻调用
componentDidUpdate(object prevProps, object prevState)
DOM更新后调用

# Redux-React
<img src="zPhoto/Flux Flow.png">
<img src="zPhoto/Redux Flow.png"> 
Action: Topic
Reducer: 修改 State
Presenter Component:  静态组件
Container Component: connect(), dispach


## Actions

```
export const addTodo = (text) => ({
  type: 'ADD_TODO',
  id: nextTodoId++,
  text
})
```
## Reducer
- (previousState, action) => newState
- 根据Topic, 改变 Store数据
- 触发: dispatch, state改变

### combineReducers
```
const todoApp = combineReducers({
  visibilityFilter,
  todos
})
```
## Store
### 1. getState() 
获取 state；
### 2. dispatch 
发布 action, 更新 state；
### 3. subscribe() 
listener 监听器
#### 监听每次 state 变化
```
let unsubscribe = store.subscribe(() =>
    console.log(store.getState())
)
```
### 4. replaceReducer

## Provider 
###### 接受Redux的store作为props
```
Provider
<Provider store={store}>
   <App/>
</Provider>
```
## connect()
1. 连接React组件与 Redux store
2. connect(mapStateToProps, mapDispatchToProps, mergeProps, options)(App);
    - [mapStateToProps]: store中state 返回Object
    - [mapDispatchToProps]: 输入dispach 返回Object
    - [mergeProps]: 接收前2个函数生成的 stateProps, dispatchProps, 在加上原始的props, 合并成新的props, 并传给原始根节点的props

```
//  mapStateToProps
const mapStateToProps = state => {
  return {
    todo : state.todos[0]
  }
}
// mapDispatchToProps
const mapDispatchToProps = dispatch => {
  return {
    destroyTodo : () => dispatch({
      type : 'DESTROY_TODO'
    })
  }
}
/******** or  **********
const mapDispatchToProps = ({
  destroyTodo: () => ({
    type : 'DESTROY_TODO'
  })
})
***********************/ 
export default connect(
  mapStateToProps,
  mapDispatchToProps
)(TodoItem)
```




# Vue 
    <script src="https://unpkg.com/vue"></script>

## Basic 
```
new Vue({
   el: '#app',
   data: {  },
   methods: { }
   computed: { }
})
```

### computed
有缓存，只有改变才重新取值

```
<div id="app">
  {{message}} 
  <p>computed_Message转换：{{ computedMessage }}</p>
  <p>methods_Message转换：{{ methodsMessage() }} </p>
</div>
<script>
var vm = new Vue({
  el: '#app',
  data: {
    message: 'abcdef'
  },
  computed: {
    computedMessage: function () {
      return this.message.split('').reverse().join('')
    }
  },
  methods: {
    methodsMessage: function () {
      return this.message.split('').reverse().join('')
    }
  }
})
console.log(typeof(vm.computedMessage));   // string 
console.log(typeof(vm.methodsMessage));    // function
```

get: function () {  }
set: function () {  }

### IF条件语句
v-if = "seen"
v-else
v-else-if
### Loop
v-for="value in object"
v-for="(value, key) in object"
###### v-for="(value, key, index) in object"
```
<li v-for="(value, key, index) in object">
    {{ index }}. {{ key }} : {{ value }}
</li>
// 1.key1 : value1
// 2.key2 : value2
```
##### v-for="n in 20"
```
<li v-for="n in 20">
     {{ n }}
</li>    // 1, 2, 3. . . 20
```

### v-show

## v-on:click 
### @click   
```
<div id="app">
  <button v-on:click="counter += 1">增加 1</button>
  <p>这个按钮被点击了 {{ counter }} 次。</p>
</div>
<script>
new Vue({
  el: '#app',
  data: {
    counter: 0
  }
})
</script>
```
### keyup
    <input v-on:keyup.13="submit">
    <input v-on:keyup.enter="submit">
    <input @keyup.enter="submit">

>key键名:
>.enter
>.tab
>.delete ("删除"和"退格")
>.esc
>.space
>.up
>.down
>.left
>.right
>.ctrl
>.alt
>.shift
>.meta

```
<input @keyup.alt.67="clear">    		// Alt + C
<div @click.ctrl="doSomething"></div>  // Click + Ctrl
```

## v-band
### :class
###### 创建  class= active  
```
<div v-bind:class="{ active: isActive }"></div>
<script>
new Vue({
  el: '#app',
  data: {
    isActive: true
  }
})
</script>
```
###### 创建 class= static active text-danger
```
<div class="static"
   v-bind:class="{ active: isActive, 'text-danger': hasError }">
</div>
<script>
new Vue({
  el: '#app',
  data: {
     isActive: true,
	hasError: true
  }
})
</script>
```
###### or

```
<div id="app">
  <div class="static" v-bind:class="classObject"></div>
</div>
<script>
new Vue({
  el: '#app',
  data: {
    classObject: {
      active: true,
      'text-danger': true
    }
  }
})
</script>
```
######Array Class 创建多个Class,   class= active text-danger
```
<div id="app">
	<div v-bind:class="[activeClass, errorClass]"></div>
</div>
<script>
new Vue({
  el: '#app',
  data: {
    activeClass: 'active',
    errorClass: 'text-danger'
  }
})
```
## Component
### Global Component
```
Vue.component('runoob', {
  template: '<h1>自定义组件!</h1>'
})
// 创建根实例
new Vue({
  el: '#app'
})
```
### Local Component
```
var Child = {
  template: '<h1>自定义组件!</h1>'
}
new Vue({
  el: '#app',
  components: {
    // <runoob> 将只在父模板可用
    'runoob': Child
  }
})
```
#### data Must Be a Function    

### Props
数据传给子组件

```
<div id="app">
    <input v-model="parentMsg">
    <child v-bind:message="parentMsg"></child>
</div>
<script>
Vue.component('child', {
  props: ['message'],
  template: '<span>{{ message }}</span>'
})
new Vue({
  el: '#app',
  data: {
  parentMsg: '父组件内容'
  }
})
```

### 组件通信
> this.$parent：指向父组件的实例；
> this.$root：指向根实例对象；
> this.$children：父组件的一个数组，包含它所有的子元素；

### 自定义 Event
> $on()：监听事件；
> $emit()：在组件实例上触发事件；
> $dispatch()：派发事件，沿着父链冒泡；
> $broadcast()：广播事件，事件向下传导给所有后代；

## v-model 
###### 使用: `<input> <textarea> <select>`

```
<div id="app-6">
  <p>{{ message }}</p>
  <input v-model="message">
</div>
<script>
var app6 = new Vue({
  el: '#app-6',
  data: {
    message: 'Hello Vue!'
  }
})
</script>
```
### checkbox 多选框
```
<div id="app">
  <p>单个复选框：</p>
  <input type="checkbox" id="checkbox" v-model="checked">
  <label for="checkbox">{{ checked }}</label>
  
  <p>多个复选框：</p>
  <input type="checkbox" id="runoob" value="Runoob" v-model="checkedNames">
  <label for="runoob">Runoob</label>
  <input type="checkbox" id="google" value="Google" v-model="checkedNames">
  <label for="runoob">Google</label>
  <input type="checkbox" id="taobao" value="Taobao" v-model="checkedNames">
  <label for="taobao">taobao</label>
  <br>
  <span>选择的值为: {{ checkedNames }}</span>
</div>
<script>
new Vue({
  el: '#app',
  data: {
  checked : false,
    checkedNames: []
  }
})
</script>
```
### radio 单选
```
<div id="app">
  <input type="radio" id="runoob" value="Runoob" v-model="picked">
  <label for="runoob">Runoob</label>
  <br>
  <input type="radio" id="google" value="Google" v-model="picked">
  <label for="google">Google</label>
  <br>
  <span>选中值为: {{ picked }}</span>
</div>
<script>
new Vue({
  el: '#app',
  data: {
	picked : 'Runoob'
  }
})
</script>
```
### Select 选择框    selected和value绑定
```
<div id="app">
  <select v-model="selected" name="fruit">
    <option value="">empty</option>
    <option value="www.youtube.com">Youtube</option>
    <option value="www.google.com">Google</option>
  </select>  
  网站是: {{selected}}
</div>
<script>
new Vue({
  el: '#app',
  data: {
    selected: '' 
  }
})
</script>
```

.lazy:  完成后才更新

```
<div id="app-6">
  <p>{{ message }}</p>
  <input v-model.lazy="message">
</div>
<script>
var app6 = new Vue({
  el: '#app-6',
  data: {
    message: 'Hello Vue!'
  }
})
</script>
```
.number   输入string转换成number

    <input v-model.number="age" type="number">

.trim   省略首尾空格
