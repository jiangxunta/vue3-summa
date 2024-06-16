- 父组件
```
<Demo msg="你好呀！">
    <!-- 如果插槽不带名字的话
    <span>张三</span>
    <span>李四</span> -->
    <template slot="name1">
        <span>张三</span>
    </template>
    <template slot="name2">
        <span>李四</span>
    </template>
</Demo>
```
- 子组件
```
<div class="demo">
    <h2>我是Demo组件</h2>
    <!-- 插槽不带名字直接都放进这里面
    <slot></slot> -->
    <slot name="name1"></slot>
    <slot name="name2"></slot>
</div>
<script>
export default {
    name: 'Demo',
    // props: ['msg'],
    mounted() {
        console.log(this);
    }
}
</script>
```
- $attrs：如果父组件传参，在子组件的props里面没有定义，$attrs就会有，模板里面就可以通过$attrs取出来，否则在子组件的props里面有定义$attrs就没有
- $slots：如果没有插槽slot，$slots在VueComponent里面是有的