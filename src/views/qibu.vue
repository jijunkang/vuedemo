<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
  <script src="https://cdn.staticfile.org/vue/2.4.2/vue.min.js"></script>
</head>
<body>
<!--
可以看到在 Vue 构造器中有一个el 参数，它是 DOM 元素中的 id。在上面实例中 id 为 vue_det，在 div 元素中：

<div id = "vue_det"></div>
这意味着我们接下来的改动全部在以上指定的 div 内，div 外部不受影响。

接下来我们看看如何定义数据对象。

data 用于定义属性，实例中有三个属性分别为：site、url、alexa。

methods 用于定义的函数，可以通过 return 来返回函数值。

{{ }} 用于输出对象属性和函数返回值。-->
<div id="vue_det">
  <h1>site : {{site}}</h1>
  <h1>url : {{url}}</h1>
  <h1>{{details()}}</h1>
</div>
<script type="text/javascript">
  var vm = new Vue({
    el: '#vue_det',
    data: {
      site: "菜鸟教程",
      url: "www.runoob.com",
      alexa: "10000"
    },
    methods: {
      details: function() {
        return  this.site + " - 学的不仅是技术，更是梦想！";
      }
    }
  })
</script>
</body>
</html>


