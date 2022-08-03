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
  <label>计算属性computed，反转字符</label>{{ reversedMessage }}
  <hr>


  监听属性
  <div id="computed_props">
    千米 : <input type="text" v-model="kilometers">
    米 : <input type="text" v-model="meters">
  </div>
  <hr>

  class 属性绑定
  <div v-bind:class="classObject"></div>
  <hr>

  Vue.js style(内联样式)
  <div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }">菜鸟教程</div>
  <div v-bind:style="styleObject">菜鸟教程</div>
  <div v-bind:style="[baseStyles, overridingStyles]">菜鸟教程</div>
  <hr>

  Vue.js 事件处理器
  <button v-on:click="kilometers += 1">增加 1</button>
  <p>这个按钮被点击了 {{ kilometers }} 次。</p>
  <button v-on:click="greet">Greet</button>

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
      kilometers: 0,
      meters: 0,
      isActive: true,
      error: {
        value: true,
        type: 'fatal'
      },
      sites: [
        {name: 'Runoob'},
        {name: 'Google'},
        {name: 'Taobao'}
      ],
      activeColor: 'green',
      fontSize: 30,
      styleObject: {
        color: 'green',
        fontSize: '30px'
      },
      baseStyles: {
        color: 'green',
        fontSize: '30px'
      },
      overridingStyles: {
        'font-weight': 'bold'
      }

    }
  },
  methods: {
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    },
    greet: function (event) {
      // `this` 在方法里指当前 Vue 实例
      alert('Hello ' + this.msg + '!')
      // `event` 是原生 DOM 事件
      if (event) {
        alert(event.target.tagName)
      }
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
    },
    //返回一个class对象
    classObject: function () {
      return {
        base: true,
        active: this.isActive && !this.error.value,
        'text-danger': this.error.value && this.error.type === 'fatal',
      }
    }
  },
  watch: {
    kilometers: function (val) {
      this.kilometers = val;
      this.meters = this.kilometers * 1000
    },
    meters: function (val) {
      this.kilometers = val / 1000;
      this.meters = val;
    }
  }
}
</script>

<style>
.class1 {
  background: #444;
  color: #eee;
}

.base {
  width: 100px;
  height: 100px;
  margin: auto;
}

.active {
  background: green;
}

.text-danger {
  background: red;
}
</style>