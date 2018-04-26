# 修饰符
    -> 指出一个指令以特殊方式绑定
        例如：.prevent修饰符告诉 v-on 指令对于触发的事件调用阻止默认事件
            event.preventDefault();

            <form v-on:submit.prevent="onSubmit">...</form>