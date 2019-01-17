# Vue官網範例練習-新手村上路
本篇透過官網實例了解Vue的基礎操作及概念,以此做個練習紀錄。
 
## 01 - Hello Vue
第一課資料綁定插入 string，利用 Mustache 的語法：
```
<div id="app" class="text">
  <p>{{message}}</p>
  <ul>
  <li>{{ message }}</li>
  <li>{{FirstName}}</li>
  <li>{{LastName}}</li>
  <li>{{FirstName+LastName}}</li>
</ul>
</div>
```
```
new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue.js!',
    FirstName: 'Eddie',
    LastName: 'Liu'
}
})
```
結果:<br/>
![](https://i.imgur.com/iMDL0ki.png)<br/>
附上[程式碼範例](https://jsfiddle.net/EddieLiu58/01hzuq5t/31/)

##  02 - Bind Message
 Vue 可透過 v-bind 綁定 HTML 的屬性。
 ```
<div id="app-2">
  <span v-bind:title="message">
   把滑鼠放在這段文字上!
  </span>
</div>
```
```
var app2 = new Vue({
  el: '#app-2',
  data: {
    message: '現在時間' + new Date().toLocaleString()
  }
})
```
結果:<br/>
![](https://i.imgur.com/me1CLX3.png)<br/>
附上[程式碼範例](https://jsfiddle.net/EddieLiu58/kjsvhndy/)

## 03 - Conditional Rendering

透過 v-if 這個指令(directive)決定是否顯示p tag。
單純這樣有點無趣，先加入後面會介紹的v-on來綁定button，透過點擊可以改變seen的狀態。
```
<div id="app-3">
  <p v-if="seen">你有看到我嗎?</p>
  <button type="button" v-on:click="seen=!seen">點我!</button>
</div>

```
```
var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: true
  }
})
```
結果:<br/>
未點button，此時seen預設為true，**v-if成立**，文字顯示。<br/>
![](https://i.imgur.com/eppDdZg.png)<br/>
點擊button後，因為seen變為false，**v-if並未成立**，綁定v-if的文字則消失了。<br/>
![](https://i.imgur.com/1hP7iL4.png)<br/>
附上[程式碼範例](https://jsfiddle.net/EddieLiu58/bt2m5fh4/)

## 04 - List Rendering
透過 v-for 這個指令(directive)顯示 todos list。
```
<div id="app-4">
  <ol>
    <li v-for="todo in todos">
      {{ todo.text }}
    </li>
  </ol>
  <p v-for="(todo, key) in todos">
    {{key +1}}.{{todo.text}}
  </p>
</div>
```
```
var app4 = new Vue({
  el: '#app-4',
  data: {
    todos: [{
        text: '每天練習Vue'
      },
      {
        text: '每天練習Js'
      },
      {
        text: '培養美感'
      }
    ]
  }
})
```
結果:<br/>
![](https://i.imgur.com/6vxIgKC.png)<br/>
附上[程式碼範例](https://jsfiddle.net/EddieLiu58/2mhr87do/)

## 05 - Event Handling
透過 v-on 綁定 click 事件，點擊button時執行reverseMessage，將message反轉。
```
<div id="app-5">
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">Reverse Message</button>
</div>

```
```
var app5 = new Vue({
  el: '#app-5',
  data: {
    message: '文字會反轉哦!'
  },
  methods: {
    reverseMessage: function() {
      this.message = this.message.split('').reverse().join('')
    }
  }
})
```
結果:<br/>
![](https://i.imgur.com/r6ga0nh.png)<br/>
附上[程式碼範例](https://jsfiddle.net/EddieLiu58/ymuc9Lgn/)

## 06 - Form Input Bindings
透過 v-model 可雙向綁定 input 和 vue instance 的 message。
```
<div id="app-6">
  <p>{{ message }}</p>
  <input v-model="message">
</div>
```
```
var app6 = new Vue({
  el: '#app-6',
  data: {
    message: '請修改文字!'
  }
})
```
結果:<br/>
![](https://i.imgur.com/GpJEjNi.png)<br/>
附上[程式碼範例](https://jsfiddle.net/EddieLiu58/uvkLqzp8/)
## 07 - Component
```
<div id="app-7">
  <ol>
    <todo-item v-for="item in groceryList" v-bind:todo="item" v-bind:key="item.id">
    </todo-item>
  </ol>
</div>
```
```
Vue.component('todo-item', {
  props: ['todo'],
  template: '<li>{{ todo.text }}</li>'
})

var app7 = new Vue({
  el: '#app-7',
  data: {
    groceryList: [{
        id: 0,
        text: 'Vegetables'
      },
      {
        id: 1,
        text: 'Cheese'
      },
      {
        id: 2,
        text: 'Whatever else humans are supposed to eat'
      }
    ]
  }
})

```
結果:<br/>
![](https://i.imgur.com/XGCgWQy.png)<br/>
附上[程式碼範例](https://jsfiddle.net/EddieLiu58/wk4r7x5u/#&togetherjs=EMFcTyDTT3)

 
 
 
 
