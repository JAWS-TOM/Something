# html基础
---
## 1.最小实例  
vscode 里面输入！回车，就能自动生成
```html
<!DOCTYPE html>  <!-- 必须放在第一行，声明为 HTML5 文档（不写会触发浏览器怪异模式） -->
<html lang="zh-CN">  <!-- lang 属性：声明页面主要语言（zh-CN 表示中文，利于SEO和无障碍） -->
  <head>
    <meta charset="UTF-8">  <!-- 字符编码：必须设置，否则中文可能乱码（UTF-8 兼容全球语言） -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  <!-- 移动端适配核心：让页面宽度等于设备宽度，初始缩放1倍 -->
    <meta name="description" content="这是页面描述">  <!-- 网页描述，会显示在搜索引擎结果中 -->
    <title>我的第一个网页</title>  <!-- 浏览器标签页标题，必填（影响SEO） -->
    <link rel="stylesheet" href="style.css">  <!-- 引入外部CSS文件 -->
    <script src="script.js"></script>  <!-- 引入外部JS文件 -->
  </head>
  <body>
    <!-- 可见内容区 -->
  </body>
</html>

```
## 2.文本标签
- \<h1>-\<h6> 标题,  `<h1>主标题</h1>`  
- \<p>  段落,  	自动换行，段落间有默认间距  `<p>这是一段文字</p>`  
- \<br>  强制换行,  单标签（无闭合标签）  `第一行<br>第二行`  
- \<hr>  水平线,  单标签，可通过 CSS 修改样式  `	<hr>`
- \<strong>  强调文本,（加粗，有语义）  `<strong>注意</strong>`
- \<em>  	强调文本,（斜体，有语义）  仅样式斜体  `<em>重点</em>`
- \<del>  删除线,  表示删除的内容  `<em>重点</em>`
- \<ins>  	下划线,（插入的内容）  `<ins>下划线</ins>`
- \<sup>  	上标,  用于公式   `x<sup>2</sup>（显示 x²）`
- \<sub>  下标,  	用于公式  `H<sub>2</sub>O（显示 H₂O）`
- \<span>  行内容器,（无默认样式）用于给部分文本单独设置样式  `<span style="color:red">红色字</span>`

















