# mobile_software_project01
## 一、实验内容

### （一）安装开发工具

1.下载安装自己电脑对应系统的微信开发者工具

2.新建小程序到对应的文件夹

### （二）创建hello world小程序

#### 1.index.wxml

（1）view：小程序容器标签，等价于网页里的用来包裹文字、组件，划分布局区块。

- class=“title”：给这个 view 设置样式类名 title， 可以给它设置字体颜色、大小等样式。

- {{wording}}：绑定 js 文件里 data中定义的数据。

（2）image：小程序图片标签。

- mode="widefix"：保持图片宽高比，使图片宽度铺满容器。

（3）src="../../img/apple.jpg"

- src：图片资源地址
- ../ 代表向上返回一级文件夹
- ../../= 向上返回两级目录

（4）button：小程序按钮组件。

- tap：小程序里的点击触摸事件等价网页
- bind：事件绑定关键字
- "onClick"：绑定的事件函数名，需要在 index.js 的 Page 中定义 onClick(){} 方法，点击按钮后，就会执行这个 js 函数。



#### 2.index.wxss

（1）page: 小程序内置根选择器，代表整个页面可视区域。

（2）display: flex;开启弹性布局

- flex-direction: column;设置内部元素垂直从上往下排列

- column：上下排（你现在需要的：文字 → 图片 → 按钮，依次垂直摆放）
- row：横向左右并排

（3）justify-content: center;控制主轴方向居中，因为上面设置了 column（主轴是垂直方向），所以这条实现：垂直居中（上下居中）

（4）align-items: center;控制交叉轴居中

（5）width: 100%;page 容器宽度占满手机屏幕全部宽度

（6）margin: 0;清除 page 默认自带外边距，防止四周出现空白留白



#### 3.index.js

（1）data: { wording:'girl' }定义变量 wording，初始值是 girl

（2）onClick:function():onClick：自定义点击事件函数名，对应 wxml 按钮 bind:tap="onClick"

- function()：代表这是一个可执行函数，点击按钮后，大括号内代码运行

（3）if(this.data.wording === 'girl')

- this.data.wording：读取 data 里当前 `wording` 的值

- ===：严格相等判断（值和类型完全一样才成立）

（4）this.setData({ wording: 'boy' })：修改 data 中的变量，并且自动更新 wxml 页面视图



## 二、问题总结与体会

### （一）问题总结

1. 数据更新误区：直接通过 this.data.wording = 'boy' 赋值修改数据，页面不会自动刷新，必须使用 this.setData() 方法修改数据，才能同步更新页面视图。
2. Flex 布局居中失效：使用 flex 实现页面垂直居中时，若遗漏height:100vh，page 容器无法占满屏幕高度，justify‑content: center垂直居中效果会失效，只能实现水平居中。
3. 代码语法漏洞：编写 js 逻辑时容易漏写引号、大括号、分号，例如字符串引号写反、少写闭合大括号，会直接导致小程序编译报错，页面无法运行。

### （二）实验体会

​        通过本次实验，我初步熟悉了微信开发者工具的使用，理解小程序wxml、wxss、js三类文件各自的分工：wxml 负责页面结构搭建，wxss 完成页面样式布局，js 处理业务逻辑与数据交互。掌握了 flex 弹性布局实现页面元素水平、垂直居中的方法，理解插值语法`{{}}`如何实现页面与 JS 的数据绑定，学会使用bind:tap绑定点击事件，利用setData()完成数据双向更新，实现点击按钮切换文本的交互效果。

​       本次实验为后续移动软件开发的学习打下基础，也体会到前端开发结构、样式、逻辑三者相互配合的开发思想。
