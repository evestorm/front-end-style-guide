---
html:
  embed_local_images: false
  embed_svg: true
  offline: false
  toc: true

print_background: false
---

# uni-app规范

## 一. CSS

### 1.1 css用less语法

```less
.header {
  .title {
    color: #white;
  }
}
```

在线文档：

- [中文文档](http://lesscss.cn/)
- [less官网](http://lesscss.org/)

### 1.2 以 rpx 为响应元素

rpx 是相对于基准宽度的单位，可以根据屏幕宽度进行自适应。`uni-app` 规定屏幕基准宽度 750rpx。

开发者可以通过设计稿基准宽度计算页面元素 rpx 值，设计稿 1px 与框架样式 1rpx 转换公式如下：

```
设计稿 1px / 设计稿基准宽度 = 框架样式 1rpx / 750rpx
```

换言之，页面元素宽度在 `uni-app` 中的宽度计算公式：

```
750 * 元素在设计稿中的宽度 / 设计稿基准宽度
```

**举例说明：**

1. 若设计稿宽度为 750px，元素 A 在设计稿上的宽度为 100px，那么元素 A 在 `uni-app` 里面的宽度应该设为：`750 * 100 / 750`，结果为：100rpx。
2. 若设计稿宽度为 640px，元素 A 在设计稿上的宽度为 100px，那么元素 A 在 `uni-app` 里面的宽度应该设为：`750 * 100 / 640`，结果为：117rpx。
3. 若设计稿宽度为 375px，元素 B 在设计稿上的宽度为 200px，那么元素 B 在 `uni-app` 里面的宽度应该设为：`750 * 200 / 375`，结果为：400rpx。

```less
.table {
  height: 200rpx;
}
```

在线文档：

- [uni-app 尺寸单位](https://uniapp.dcloud.io/frame?id=尺寸单位)

### 1.3 单独的 css 文件以 .less 为后缀

```shell
├── selectTable
│   ├── selectTable.js
│   ├── selectTable.less // 以 less 结尾
│   └── selectTable.vue
```

### 1.4 css 每个大块需要写注释

```less
// 外层容器
.container {
	width: 100%;
	top:44px;
	...
}
// 整个表格容器
#select-table {
	position: absolute;
	width: 100%;
	...
	// 滚动容器 scroll-view
	.scroll-Y {
		height: 100%;
	}
}
```

### 1.5 作用域限制

```js
<style lang="less" scoped>
</style>
```



## 二. JS

### 2.1 方法统一使用es6方法简写名称

```js
methods: {
  init() {

  },
}
```

### 2.2 组件的props统一加上注释并且加上校验和类型

```javascript
props: {
  /* 默认值 */
  pickerArr: {
    type: Array,
    default() {
      return [0, 1, 2]
    }
  }
}
```

在线文档：

- [Vue.js Prop](https://cn.vuejs.org/v2/guide/components-props.html)

### 2.3 组件emit 调用需要加注释

```js
// 点击发送按钮时，通知父组件用户输入的内容
this.$emit('send-message', {
  type: 'text',
  content: that.inputValue
});
that.inputValue = '';
```

### 2.4 统一使用import export语法 不用reqiure

```js
export default appConfig;
import * as config from '@/common/service/appConfig.js';
```

### 2.5 export 导出对象 如果不需要重命名 不用加:格式

```js
export default {
  GetAreaInApp, // 不需要重命名的情况
  GetTable: GetTableInApp // 需要重命名的情况
}
```

### 2.6 import 统一使用@做根路径选择

```js
import * as CY22 from '@/service/CY/CY22AppService.js';
```

### 2.7 Vue 的 Model 和方法都写注释

```js
export default {
  data() {
    return {
      // 下拉刷新的常用配置
      downOption: {
        use: false, // 是否启用下拉刷新; 默认true
        auto: false, // 是否在初始化完毕之后自动执行下拉刷新的回调; 默认true
      },
      // 上拉加载的常用配置
      upOption: {
        use: false, // 是否启用上拉加载; 默认true
        auto: false, // 是否在初始化完毕之后自动执行上拉加载的回调; 默认true
      },
    }
  },
  methods: {
    // 获取订单
    requestOrders() {/*...*/}
  }
}
```

### 2.8 跳转统一用绝对路径

```js
uni.navigateTo({
  url: '/pages/saleTarget/saleTarget'
});
```

### 2.9 组件内方法添加注释

```js
methods: {
  // 获取客户列表数据
  getCustomerList() {

  }
}
```

### 3.0 通用方法添加详细注释

```js
/**
* @description 简要描述这本书
* @constructor
* @param {string} title - 书的标题
* @param {string} author - 书的作者
*/

function Book(title, author) {
  ...
}
```

## 三. 通用规范

### 3.1 格式化代码

写完代码，无论 `.vue` `.js` 还是 `.less` 文件，一律 `Ctrl + K` 格式化。若电脑为 Mac ，格式化快捷键为 `Shift + Alt + F` 。

**配置vue格式化**：

打开 HBuilderX 菜单栏中 `工具 > 插件配置 > formator-prettier > prettier.config.js` ，使用下面配置覆盖默认配置：

```js
module.exports = {
  printWidth: 150,
  semi: true,
  tabWidth: 2,
  useTabs: false,
  singleQuote: true,
  trailingComma: "none",
  bracketSpacing: true,
  htmlWhitespaceSensitivity: "ignore",
  parsers: {
    ".jsx": "flow",
    ".scss": "scss",
    ".ts": "typescript",
    ".less": "css",
    ".vue": "vue",
    ".nvue": "vue",
    ".ux": "vue",
    ".yml": "yaml",
  }
}
```

**配置js格式化：**

打开 HBuilderX 菜单栏中 `工具 > 插件配置 > format > jsbeautifyrc.js` ，使用下面配置覆盖默认配置：

```js
module.exports = {
  parsers: {
    ".js": "js",
    ".json": "js",
    ".njs": "js",
    ".sjs": "js",
    ".wxs": "js",
    ".css": "css",
    ".nss": "css",
    ".wxss": "css",
    ".acss": "css",
    ".ttss": "css",
    ".qss": "css",
    ".html": "html",
    ".ux": "html",
    ".wxml": "html",
    ".nml": "html",
    ".vue": "html",
    ".nvue": "html",
    ".axml": "html",
    ".swan": "html",
    ".ttml": "html",
    ".qml": "html"
  },
  options: {
    "indent_size": "1",
    "indent_char": "\t",
    "indent_with_tabs": false, //使用tab缩进
    "eol": "\r\n", //行结束符
    "end_with_newline": false, //使用换行结束输出
    "indent_level": 0, //起始代码缩进数
    "preserve_newlines": true, //保留空行
    "max_preserve_newlines": null, //最大连续保留换行符个数。比如设为2，则会将2行以上的空行删除为只保留1行
    "space_in_paren": false, //括弧添加空格 示例 f( a, b )
    "space_in_empty_paren": false, //函数的括弧内没有参数时插入空格 示例 f( )
    "jslint_happy": false, //启用jslint-strict模式
    "space_after_anon_function": false, //匿名函数的括号前加空格
    "brace_style": "collapse", //代码样式，可选值 [collapse|expand|end-expand|none][,preserve-inline] [collapse,preserve-inline
    "unindent_chained_methods": false, //不缩进链式方法调用
    "break_chained_methods": false, //在随后的行中断开链式方法调用
    "keep_array_indentation": false, //保持数组缩进
    "unescape_strings": false, //使用xNN符号编码解码可显示的字符
    "wrap_line_length": 120,
    "e4x": false, //支持jsx
    "comma_first": false, //把逗号放在新行开头，而不是结尾
    "operator_position": "before-newline",
    "unformatted": ["wbr"],
    "html": {
      "indent_handlebars": true,
      "indent_inner_html": true,
      "indent-scripts": "normal", //[keep|separate|normal]
      "extra_liners": [] //配置标签列表，需要在这些标签前面额外加一空白行
    }
  }
}
```



### 3.2 组件命名

组件统一放在 `components/yyt` 下面 并且以 `yyt` 开始

```shell
App/components
├── uni-tag
│   └── uni-tag.vue
└── yyt
    ├── yyt-Short
    │   └── yyt-Short.vue
    ├── yyt-neil-modal
    │   ├── yyt-neil-modal.vue
```

### 3.3 script/css 与 .vue 文件分离

> homePage.vue

```js
...
<script>
export { default } from './homePage.js';
</script>

<style lang="less" scoped>
@import url('homePage.less');
</style>
```

> homePage.js

```js
export default {
  data() {...},
  ...
}
```

> homePage.less

```less
// 主容器
.home {
  position: relative;
  background: #F2F2F2;
  box-sizing: border-box;
  padding-bottom: 102rpx;
}
```

> 目录结构

```shell
homePage
├── homePage.js
├── homePage.less
├── homePage.vue
```

### 3.4 ⚠️ 注释 ⚠️

**所有文件写完之后，一律记得添加相关注释！！！**

允许使用拼音给类和变量命名，但务必添加上中文注释！例如：

> index.less

```less
.gen-zong-pai-hang { // 跟踪排行

}
```

> index.js

```js
// 跟踪排行
let genZongPaiHang = '';
```

### 3.5 图片上传

项目中需要使用到的图片，如果大于 5kb ，需上传至图片服务器引用：

步骤：

1. 打开 https://pic.cwyyt.cn/
2. 点击上述链接中的 `选择文件` 按钮选择图片
3. 点击 `提交` 按钮上传图片
4. 复制返回的 path 线上图片路径，与 `pic.cwyyt.cn` 拼接：`https://pic.cwyyt.cn/` + `upload/img/20191210/1120452045_鼓掌.gif`
5. 在项目中直接使用刚刚拼接的线上图片路径

## 四. 项目说明

### 4.1 Vue Prototype 扩展

uni-app项目 `main.js` 中，我们在 Vue 的原型下挂载了如下变量以方便开发：

```js
function prototypeEx(Vue){
  // vue prototype 扩展
  Vue.prototype._ = _; // 加入 lodash.js 使用
  Vue.prototype.moment = moment; // 加入 moment 使用
  Vue.prototype.$cw = cw; // 兼容之前app的cw
  Vue.prototype.$storage = storage; // 用于存储
  Vue.prototype.$store = store; // vuex
  Vue.prototype.$backgroundAudioData = {
    playing: false,
    playTime: 0,
    formatedPlayTime: '00:00:00'
  }
}
```

这样我们在组件中就可以使用 `this.*` 的方式调用这些工具，例如：

> homePage.js

```js
export default {
  methods: {
    init() {
      // 从原型 storage 对象中获取当前店铺id
      this.currentStoreId = this.$storage.getAppUserInfo().currentStoreId;
    }
  }
}
```

**注意：**

如果你希望在 `data` 下获取 storage 下方法，是无法通过 `this.$storage` 拿到的，这种情况你只能在当前组件中 import 导入 storage ：

```js
import storage from '@/common/unistorage/index.js';
export default {
  data() {
    return {
      currentStoreId: storage.getAppUserInfo.currentStoreId,
    }
  }
}
```
