# 组件注册

## 组件名
    -> 命名方式有两种，推荐使用短横线分隔命名

## 全局注册
    -> Vue.component('component-name',{
        // ...
    })

    -> 这些组件是全局注册的，因此在注册之后可以在任何新创建的Vue 根实例的模板中

## 局部注册
    -> var ComponentA = { /* ... */ }
        然后在components 选项中定义想要使用的组件：
        new Vue({
            el : "#app",
            components : {
                'component-a' : ComponentA,
            }
        })

    -> 如果希望在 ComponentA 在 ComponentB 中可用，则需要这样写：
        var ComponentA = { /* ... */ }

        var ComponentB = {
            components : {
                'component-a' : ComponentA,
            },
            //...
        }

        如果用Babel 和webpack 使用ES2015模块，则应如下写法
        import ComponentA from './ComponentA.vue'

        export default {
            components : {
                'component-a' : ComponentA,
            }
        }