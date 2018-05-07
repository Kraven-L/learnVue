# 修饰符
    -> 指出一个指令以特殊方式绑定
        例如：.prevent修饰符告诉 v-on 指令对于触发的事件调用阻止默认事件
            event.preventDefault();

            <form v-on:submit.prevent="onSubmit">...</form>

    -> 缩写  v-bind  =>  :
            v-on   =>   @

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

# 列表渲染 
    -> 在遍历时 对应参数为 v-for="(value,key,index) in items"

    -> 可以用数组的增删方法来对要遍历的数组进行修改，从而触发视图的更新
        push() pop() shift() unshift() splice()等

    -> 对于已经创建的实例，Vue不能动态添加根级别的响应式属性。
    
    -> 对已有对象添加多个新属性时，写法为：
        vm.XXXXX = Object.assign( {} , vm.XXXXX , { 需要新增的属性 key : value })

    -> v-for 也可以取整数，可理解为在一个范围内循环 eg: v-for=" n in 10" 
        
    -> 在循环之中可以添加 v-if 来限制遍历的起始位置

    -> 当v-for 和 v-if 处于同一节点，前者比后者优先级更高，也就是v-if 会在每个v-for 循环中进行一次判断，这样可以进行筛选的渲染。

# 事件处理
    -> 可以用v-on 指令监听事件 ，并在触发时运行 js 中一些的代码

    -> v-on 还可以接受一个需要调用的方法名 

## 修饰符
    -> 事件修饰符
        .stop    .prevent    .capture    .self    .once
    -> 修饰符可以串联，顺序很重要
        eg: v-on:click.prevent.self 会阻止所有的点击，而
            v-on:click.self.prevent 会阻止对元素自身的点击

    -> .once修饰符 只会触发一次
        eg: <a v-on:click.once="doThis"></a>

    -> 按键修饰符
        通常监听键盘事件时，需要检查按下按键的键值
        eg: <input v-on:keyup.13="submit"></input> 只有在 'keycode' 是13的时候才调用 vm.submit()

        -> 也会提供别名
            <input v-on:keyup.enter="submit"></input>

            全部的按键别名： .enter  .tab  .delete  .esc  .space  .up  .down  .left  .right

        -> 也可以通过全局的 config.keyCodes 对象自定义按键修饰符别名：
            Vue.config.keyCodes.f1 = 112