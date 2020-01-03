## v-if 常见问题

### 1、当条件发现改变时，v-if并未重新渲染？
* 方法：给要重新渲染的控件添加一个key属性，来唯一标识该控件，被key标识后会重新渲染<br>
  具体可参考官网手册[https://cn.vuejs.org/v2/guide/conditional.html](https://cn.vuejs.org/v2/guide/conditional.html)<br>
  查阅资料[https://blog.csdn.net/wang729506596/article/details/81014739](https://blog.csdn.net/wang729506596/article/details/81014739)
<pre>
  &lt;cmp-button v-if="clientId !== ''" :text="'导入'" :selectFile="true" @callback="exportFrom" key="btn_1"&gt;&lt;/cmp-button&gt;
  &lt;cmp-button v-else :text="'导入'" @click="validateData" key="btn_2"&gt;&lt;/cmp-button&gt;
</pre>