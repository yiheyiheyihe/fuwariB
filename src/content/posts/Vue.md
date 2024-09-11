---
title: Vue
published: 2024-09-11
description: 'Vue study'
image: ''
tags: [Demo, Example, Markdown, Fuwari]
category: 'Examples'
draft: false 
---



## Vue

### 创建一个Vue应用

>前提条件
>
>- 已安装18.3或更高版本的 Node.js

```
npm create vue@latest
cd your-project-name
npm install
npm run dev
```



### API风格





### 项目结构 

```
.vscode 		--- VSCode工具配置文件
node_modules 	--- Vue项目的运行依赖文件夹（npm install生成）
public 			--- 资源文件夹（浏览器图标等等）
src				--- 源码文件夹（在此写代码）
.gitignore 		--- git忽略文件（团队协同文件）
index.html		--- 入口HTML文件
package.json	--- 信息描述文件
README.md		--- 注释文件（对该项目的解释）
vite.config.js	--- Vue配置文件
```

### 模板语法

##### 文本插值

>最基本的数据绑定形式是文本插值，它使用的是“Mustache”语法（ 即双大括号{{}} )

双大括号中的标签会被相应组件实例中的变量替换

```vue
<templete>
	<h3>模板语法</h3>
	<p>{{ msg }}<p>
	<p>{{ number+1 }}
    <p>{{  ok? "yes" : "no"}}</p>
    <p>message.split("").reverse().join("") </p>
<templete>

<script>
	export default{
		data(){
			return{
				msg:"神奇的语法",
				number:10,
				ok:true,
				message:"大家好"
			}
		}
	}
<script>
```

```vue
<--没有返回值-->
{{ var a = 1 }}
<--有返回值，但不是单一表达式-->
{{ if(ok) {return message} }}
```

##### 原始HTML

__双大括号会将数据解释为纯文本__，而不是HTML语言。若想实现HTML需使用 `v-html`指令

- 这里我们遇到了一个新概念：`v-html` 被称为一个<mark>指令</mark>。指令由`v-`为前缀

```vue
<template>
	<p>
    	纯文本: {{ rawHtml }}
    </p>
	<P >
      属性: <span v-html="rawHtml"></span>  <--相当于p嵌套span标签-->
    </P>
</template>

<script>
	export default{
    	data(){
    		return{
                rawHtml:"<a href="https://rainn.asia“>测试</a>"
            }
    	}
	}
</script>
```



#####   Attribute 绑定

双大括号<mark>不能</mark>在Html attribute 中使用，例：`id={{ dynamicid }}`

```vue
<template>
	<div id={{ dynamicid }}>
        测试
    </div>
</template>

<script>
	export default{
        data(){
            return{
                dynamicid:"appid"
            }
        }
    }
</script>
```

需要使用`v-bind`指令

`<div v-bind:id="dynamicid"> 测试 </div`

注：如果键值为`null`或`undefined` 将不会显示（该attribute 将会从渲染的元素上移除）

```vue
<template>
	<div v-bind:id="dynamicid" v-bind:class="dunamicClass" v-bind:title="dynamictitle">
        测试
    </div>
</template>

<script>
	export default{
        data(){
            return{
                dynamicid:"appId",
                dynamicClass:"appclass",
                dynamictitle:"appTitle"
            }
        }
    }
</script>

<style>
    .dynamicid{
        color:red
    }
</style>
```

__由于`v-bind`非常常用，所以提供了简写 __

>`<div :id="dynamicid"></div>`

##### 布尔型 Attribute

布尔型 attribute 依据 true / false 值来决定 attribute 是否应该出现在该元素上，`disabled`就是常见的例子之一

`<button :disabled="isButtonDisabled">测试</button>`

```vue
<template>
	<button :disabled="isButtonDisabled">测试</button>
</template>

<script>
	export default{
        data(){
            return{
                isButtonDisabled:true
            }
        }
    }
</script>
```

#####  动态绑定多个值

如果有多个对象具有共同的 <mark>多个attribute</mark>，为了方便，可以把它们 '打包' ，使用无参的`v-bind` 

`<div v-bind="objectOfattrs">`

```vue
<template>
	<div v-bind="objectOfattrs">
        测试1
    </div>
	<div v-bind="objectOffattrs">
        测试2
    </div>
</template>

<script>
	export default{
        data(){
            objectOfattrs:{ 
            	id : "appid",
                class: "appclass"
            }
        }
    }
</script>
```



###  条件渲染

#####  `v-if`

`v-if`  指令用于条件性的渲染（显示）一块内容，这块内容只会在指令的表达式返回__真__时才被渲染

```vue
<template>
	<h3>条件渲染</h3>
	<div v-if="flag">Can you see me or not!</div>
</template>

<script>
	export default{
        data(){
            retrun{
                flag:true
            }
        }
    }
</script>
```

##### `v-else`

可以使用`v-else` 指令添加一个 "else区块"

```vue
<template>
	<div v-if="flag">Can you see me or not?</div>
	<div v-else>Just look at me! </div>
</template>

<script>
	export default{
        data(){
            retrun{
                flag:false
            }
        }
    }
</script>
```

##### `v-else-if`

该指令提供的是一个相应于 `v-if` 的 "else if 区块"。它可以连续多次重复使用，而上者，只能使用一次

```vue
<template>
	<div v-if="type === 'A'">A</div>
	<div v-else-if="type === 'B'"> B</div>
	<div v-else-if="type === 'C'">C</div>
	<div v-else>not A/B/C </div>
</template>

<script>
	export default{
        data(){
            retrun{
                type:D
            }
        }
    }
</script>
```

__说明__：`v-if` 、`v-else-if`、`v-else` 必须挨着使用

##### `v-show`

另一个可以用来条件性地渲染元素的指令是 `v-show`

#####  区别

`v-if`：是 “真实的” 按<mark>条件渲染</mark>，因为它确保了在切换时，条件区块内的事件监听器和子组件 都会被销毁与重建

`v-show`：元素无论初始条件如何，始终会被渲染，只有CSS `display` 属性会被切换

​										`v-if` 直接被销毁，`v-show` 仍然显示

![](Vue.assets/20240905222644.png)

__总结__：

`v-if `有更高的切换开销 ;  `v-show` 有更高的渲染开销。因此，如果需要<mark>频繁切换</mark>，则使用 `v-show` 较好；如果在运行时<mark>绑定条件很少改变</mark>，则 `v-if` 会更合适。
