# 修饰符
    -> 指出一个指令以特殊方式绑定
        例如：.prevent修饰符告诉 v-on 指令对于触发的事件调用阻止默认事件
            event.preventDefault();

            <form v-on:submit.prevent="onSubmit">...</form>

# Class 与 Style 绑定

## 绑定HTML Class
    -> 可以传给 v-bind:class 一个对象，来动态地切换class 
        <div v-bind:class="{ active : "isActive" }"></div>

    -> 也可以绑定一个返回对象的计算属性

    -> 也可以绑定一个数组，并且在数组语法中也可以使用对象语法

    -> 绑定在组件上也可以，这些类名会被添加到组件的根元素上，已有的类名不会被覆盖

## 绑定内联样式
    -> 可以传给 v-bind:style 一个样式对象，样式少的话可以传单个样式

    -> 可以将多个样式对象应用到同一个元素上
        <div v-bind:style="[ baseStyle , common Style ]"></div>

    -> vue能自动检测需要添加浏览器引擎前缀的CSS属性，并添加对应前缀。

# 条件渲染
    -> 用 key 管理可复用的元素
        key = "xxxxxx" 添加一个具有唯一属性的 key 属性，就能将一个元素"独立"为两个元素

    -> v-if 和 v-show 都能根据条件渲染元素，不同的是 v-show 的元素始终会被渲染并保留在 DOM 中，只是切换元素的CSS 的 display 属性

    -> v-if 和 v-show 相比， v-if 有更高的切换开销，v-show 有更高的初始渲染开销。