<template>

  <!--1.数据绑定最常见的形式就是使用 {{...}}（双大括号）的文本插值：-->
  <h1>{{ msg }}</h1>
  <hr>

  <!--    2.使用 v-html 指令用于输出 html 代码：-->
  <div v-html="msg"></div>
  <hr>

  <!--    3.HTML 属性中的值应使用 v-bind 指令。以下实例判断 use 的值，如果为 true 使用 class1 类的样式，否则不使用该类：-->
  <label for="r1">修改颜色</label><input type="checkbox" v-model="use" id="r1">
  <div v-bind:class="{'class1': use}">
    v-bind:class 指令
  </div>
  <hr>

  <!--  4.指令是带有 v- 前缀的特殊属性。指令用于在表达式的值改变时，将某些行为应用到 DOM 上。如下例子：-->
  <label>显示</label><input type="checkbox" v-model="seen">
  <p v-if="seen">现在你看到我了</p>
  <hr>

  <!--  5.参数在指令后以冒号指明。例如， v-bind 指令被用来响应地更新 HTML 属性：-->
  <a v-bind:href="url">菜鸟教程</a>
  <hr>

  <!--  6.在 input 输入框中我们可以使用 v-model 指令来实现双向数据绑定：-->
  <p>{{ msg }}</p>
  <input v-model="msg">
  <hr>

  <!--  7.v-model 指令用来在 input、select、textarea、checkbox、radio 等表单控件元素上创建双向数据绑定，根据表单上的值，自动更新绑定的元素的值。
    按钮的事件我们可以使用 v-on 监听事件，并对用户的输入进行响应。
    以下实例在用户点击按钮后对字符串进行反转操作：-->
  <p>{{ message }}</p>
  <button v-on:click="reverseMessage">反转字符串</button>
  <hr>

  <!--  8.过滤器函数接受表达式的值作为第一个参数。
    以下实例对输入的字符串第一个字母转为大写：-->
  <!--  <p>{{ message | capitalize }}</p>
    <hr>-->

  <!--  循环-->
<!--  <ul>
    <template v-for="site in sites">
      <li>{{ site.name }}</li>
    </template>
  </ul>-->

<!--  计算属性computed-->
  <label>计算属性computed，反转字符</label>{{reversedMessage}}
  <hr>



</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      msg: 'vue从入门到放弃！',
      message: 'pompom',
      use: false,
      seen: true,
      url: 'http://www.runoob.com',
      sites: [
        { name: 'Runoob' },
        { name: 'Google' },
        { name: 'Taobao' }
      ]
    }
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  },
  filters: {
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  }
}
</script>

<style>
.class1 {
  background: #444;
  color: #eee;
}
</style>