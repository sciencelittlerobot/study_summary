# 使用vue cli 3.0.4版本开发和发布npm组件

## 一、开发步骤
* 1、搭建项目
  <pre>vue create <你的项目名称></pre>
  在此省略使用vue cli 3.X的搭建项目的步骤，可以根据自身的需求进行设置，<br>
  当前选择的是：<b>default (babel, eslint)</b>

  安装后的文件目录如下：

  ![](1.jpg "1.jpg")

  将src文件夹名称修改为examples

  在根目录下新建 packages 文件夹，在 packages 下创建要发布的组件包 testButton

  testButton文件夹中包含index.js(用于导出组件)和src/main.vue(组件的内容都写在此文件中)

  packages中的index.js主要是用于批量导出packages中的所有组件

  整理后的文件夹目录结构如下：

  ![](2.jpg "2.jpg")
  
  现在下面列下每个文件中的代码：

  testButton/src/main.vue(在此只是用于测试)
  <pre>
    &lt;template&gt;
      &lt;a class="btn btn-blue" href="javascript:void(0);" @click="fnClick"&gt;
        {{text}}
      &lt;/a&gt;
    &lt;/template&gt;

    &lt;script&gt;
      export default {
        name: 'TestButton',
        props: {
          text: {
            type: String,
            default: function () {
              return '';
            }
          }
        },
        methods: {
          // 按钮点击事件
          fnClick: function () {
            this.$emit('click');
          }
        }
      }
    &lt;/script&gt;

    &lt;style scoped&gt;
      .btn{
        display: inline-block;
        padding: 3px 12px;
        color: #8c8c8c;
        background: #ffffff;
        font-size: 14px;
        border: 1px solid #8c8c8c;
      }
      .btn.btn-blue{
        border: 1px solid #0079ff;
        color: #0079ff;
      }
      .btn.btn-red{
        border: 1px solid #ff5e5e;
        color: #ff5e5e;
      }
      .btn.btn-green{
        border: 1px solid #35a26c;
        color: #35a26c;
      }
      .btn:active{
        opacity: 0.75;
      }
    &lt;/style&gt;
  </pre>

  testButton/index.js文件

  <pre>
  // 导入组件，组件必须声明 name
  import TestButton from './src/main.vue'

  // 为组件添加 install 方法，用于按需引入
  TestButton.install = function (Vue) {
  Vue.component(TestButton.name, TestButton)
  }
  export default TestButton
  </pre>

  packages/index.js文件

  <pre>
  // 导入单个组件
  import TestButton from './testButton/index'

  // 以数组的结构保存组件，便于遍历
  const components = [
      TestButton
  ]
  // 定义 install 方法
  const install = function (Vue) {
      if (install.installed) return
      install.installed = true
      // 遍历并注册全局组件
      components.map(component => {
          Vue.component(component.name, component)
      })
  }
  if (typeof window !== 'undefined' && window.Vue) {
      install(window.Vue)
  }
  export {
      // 导出的对象必须具备一个 install 方法
      install,
      // 组件列表
      TestButton
  }
  </pre>

  有2种引入方式，一个是全局引入，一个按需引入
  



  