<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
  <script src="https://cdn.staticfile.org/vue/2.2.2/vue.min.js"></script>
</head>
<body>
<div id="app">
  <ol>
    <todo-item v-for="item in sites" v-bind:todo="item"></todo-item>
  </ol>
</div>

<script>
  Vue.component('todo-item', {
    props: ['todo'],
    template: '<li>{{ todo.text }}</li>'
  })
  new Vue({
    el: '#app',
    data: {
      sites: [
        { text: 'Runoob' },
        { text: 'Google' },
        { text: 'Taobao' }
      ]
    }
  })
</script>
</body>
</html>