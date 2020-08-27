## vue-lazyLoad 常见问题

### 加载图片列表时，会出现数据更新了，而图片没有更新的问题

* 方法：在v-lazy对应的img标签中添加:key标识，自己在调试时尝试用:key="'avatar_'+index"，问题并没有解决，具体示例代码对比如下：
  <pre>
  // 无效的方法
  &lt;img class="avatar" v-lazy="member.avatar == null ? 'images/icon_default_avatar.png' : member.avatar" :key="'avatar_'+index" /&gt;
  

  // 实际解决问题的办法
  &lt;img class="avatar" v-lazy="member.avatar == null ? 'images/icon_default_avatar.png' : member.avatar" :key="member.avatar == null ? 'images/icon_default_avatar.png' : member.avatar" /&gt;
  </pre>