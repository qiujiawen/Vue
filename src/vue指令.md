# Vue-指令

指令作用于HTML元素，将数据和DOM做关联，当表达式的值改变时，视图也会变化。

## Vue-常用指令

### v-bind

1、只调用一次，指令第一次绑定到元素时候调用，用这个钩子可以定义一个绑定时执行一次的初始化动作;

2、动态地绑定一个或多个特性，或一个组件 prop 到表达式

3、v-bind:[元素属性名] = "表达式"，可以理解为该属性值是动态变化；

可以简写为 :[元素属性名] = '表达式'

4、使用修饰符

v-bind:prop - 被用于绑定 DOM 属性。

v-bind:camel - 将 kebab-case 特性名转换为 camelCase

v-bind:sync 语法糖，会扩展成一个更新父组件绑定值的 v-on 侦听器。

实例：
```
<!-- 绑定一个属性 -->
<img v-bind:src="imageSrc">

<!-- 动态特性名 -->
<button v-bind:[key]="value"></button>

<!-- 动态特性名缩写 -->
<button :[key]="value"></button>

<!-- 内联字符串拼接 -->
<img :src="'/path/to/images/' + fileName">

<!-- class 绑定 -->
<div :class="{ red: isRed }"></div>
<div :class="[classA, classB]"></div>
<div :class="[classA, { classB: isB, classC: isC }]">

<!-- style 绑定 -->
<div :style="{ fontSize: size + 'px' }"></div>
<div :style="[styleObjectA, styleObjectB]"></div>

<!-- 绑定一个有属性的对象 -->
<div v-bind="{ id: someProp, 'other-attr': otherProp }"></div>

<!-- 通过 prop 修饰符绑定 DOM 属性 -->
<div v-bind:text-content.prop="text"></div>

<!-- prop 绑定。“prop”必须在 my-component 中声明。-->
<my-component :prop="someThing"></my-component>

<!-- 通过 $props 将父组件的 props 一起传给子组件 -->
<child-component v-bind="$props"></child-component>

```

### v-on

1、用于监听DOM事件,类似js元素绑定事件(addEventListener)

2、表达式可以是一个方法的名字或一个内联语句

3、组件和普通元素区别：用在普通元素上时，只能监听原生 DOM 事件。用在自定义元素组件上时，也可以监听子组件触发的自定义事件。

4、监听原生 DOM 事件时，如果使用内联语句，语句可以访问一个 $event 属性：v-on:click="handle('ok', $event)"

5、v-on:[事件名称] = 方法名称

可以简写为 @[事件名称] = = 方法名称

6、修饰符

v-on:stop - 调用 event.stopPropagation()，防止冒泡

v-on:prevent - 调用 event.preventDefault()，阻止元素默认事件

v-on:capture - 添加事件侦听器时使用 capture 模式。

v-on:self - 只当事件是从侦听器绑定的元素本身触发时才触发回调。

v-on:{keyCode | keyAlias} - 只当事件是从特定键触发时才触发回调。

v-on:native - 监听组件根元素的原生事件。

v-on:once - 只触发一次回调。

v-on:left - (2.2.0) 只当点击鼠标左键时触发。

v-on:right - (2.2.0) 只当点击鼠标右键时触发。

v-on:middle - (2.2.0) 只当点击鼠标中键时触发。

v-on:passive - (2.3.0) 以 { passive: true } 模式添加侦听器