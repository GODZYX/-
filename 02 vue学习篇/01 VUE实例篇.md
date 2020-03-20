### VUE 实例创建
>
    var vm = new VUE({
        el: '#root', // 添加到根节点上
        template: '<div>{{text}}</div>',
        data: {
            text: '123'
        }
    })

### VUE实例上都提供了哪些属性
* vm.$data -> 绑定的双向数据
* vm.$props -> 绑定单项数据流
* vm.$options -> 包括实例传入的所有相关配置项值
* vm.$el -> 绑定到对应节点上
* vm.$root -> 对应的根节点
* vm.$children -> 对应孩子节点
* vm.$slots -> 组件化，配置项
* vm.$scropedSlots -> 组件化，配置项
* vm.$refs -> 用来帮助快速定位 实例组件 或者 节点
* vm.$isServer -> 判别是否是服务端渲染

### VUE实例上都提供了哪些方法
* vm.$watch -> 监听数据值变化，有俩参数，一个是变化前值；一个是变化后值。还可以写成 配置项 “watch: { 属性 (newVal, oldVal) {  } }”
* vm.$emit -> 事件机制，观察者模式， 可以传参数
* vm.$on -> 监听 $emit发送过来的事件
* vm.$once -> 同上，但只监听一次
* vm.$mount -> 渲染添加执行到对应某个节点上，传入节点参数
* vm.forceUpdate -> 强制渲染组件，如：定义 obj: {} 但没声明obj.a然后直接用，在组件中，是不会刷新并产生变化的，这时可以用。但不推荐这么用，常用$set方法重新设置属性
* vm.$set -> 设置属性，如：vm.$set(vm.obj, 'a', 1)
* vm.$delete -> 删除属性，如果直接删除，reactive上没删，导致内存溢出

### VUE实例特殊方法
* vm.$options.render 这个是组件生成时渲染方法，如果定义，则会覆盖自动生成方法，如：vm.$options.render = (h) => { return h('div', {}, 'new render function') }