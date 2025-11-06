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
## 2.文本标签和通用属性
### 标签
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
- \<div> 块级容器标签，双标签，可嵌套，用于组合、划分网页内容，本身没有默认样式（默认占满一行宽度，高度由内容撑开）
### 通用属性
- id	唯一标识（页面内不能重复）`<div id="logo">...</div>`
- class	类名（可重复，用于批量设置样式）`<p class="text red">...</p>`
- style	行内 CSS 样式（优先级最高）`<span style="color:blue; font-size:16px">...</span>`
- title	鼠标悬停时显示的提示文字 `<a href="#" title="点击查看详情">...</a>`
- hidden	隐藏元素（不显示在页面上）`<p hidden>这段文字会被隐藏</p>`
- ## 3.链接
```
<!-- 1. 外部链接（跳转其他网站） -->
<a href="https://www.baidu.com" target="_blank" rel="noopener noreferrer">
  跳转到百度（新窗口打开）
</a>

<!-- 2. 本地链接（跳转同项目内的页面） -->
<a href="about.html">关于我们</a>  <!-- 同目录下的about.html -->
<a href="news/detail.html">新闻详情</a>  <!-- 子目录下的文件 -->

<!-- 3. 页面内锚点跳转（点击跳转到页面指定位置） -->
<a href="#section1">跳转到第一部分</a>
<!-- 对应位置需要设置id -->
<div id="section1">这是第一部分内容...</div>

<!-- 4. 下载文件（href指向文件路径） -->
<a href="资料.pdf" download>下载PDF资料</a>  <!-- download属性：强制下载（而非打开） -->

<!-- 5. 邮件/电话链接 -->
<a href="mailto:test@example.com">发送邮件</a>  <!-- 点击打开邮件客户端 -->
<a href="tel:10086">拨打10086</a>  <!-- 移动端点击直接拨号 -->

```
- target 属性：
_self：默认值，在当前窗口打开（覆盖当前页面）  
_blank：在新窗口打开（常用），需配合 rel="noopener noreferrer" 提高安全性
- href 属性：
后面等于地址或者路径  

## 4.图片
```
<!-- 基础用法 -->
<img 
  src="images/photo.jpg"  <!-- 图片路径（必填）：可以是本地路径或网络URL -->
  alt="一只猫的照片"       <!-- 替代文本（必填）：图片加载失败时显示，屏幕阅读器会读取 -->
  width="500"             <!-- 宽度（单位px，可省略）：只设width，height会自动等比例缩放 -->
  height="300"            <!-- 高度：不建议同时设width和height，可能导致图片变形 -->
  title="可爱的猫"         <!-- 鼠标悬停时显示的提示文字 -->
>

<!-- 网络图片 -->
<img src="https://picsum.photos/200/300" alt="随机图片">

<!-- 响应式图片（自动适应屏幕宽度） -->
<img src="big.jpg" alt="大图" style="max-width:100%; height:auto;">

```
路径src选择很多，src="photo.jpg"（同目录）、src="images/photo.jpg"（子目录）、src="../photo.jpg"（父目录），网络图片的话直接写完整 URL
## 5.列表
### a.无序列表(默认用圆点标记，可通过 type 属性修改)
```
<ul type="disc">  <!-- disc（默认圆点）、circle（空心圆）、square（方块） -->
  <li>苹果</li>
  <li>香蕉</li>
  <li>橙子</li>
</ul>
```
### b.有序列表（默认用数字标记，type 属性控制编号类型）
```
<ol type="1">  <!-- 1（数字，默认）、A（大写字母）、a（小写字母）、I（大写罗马数字）、i（小写罗马数字） -->
  <li>第一步：打开浏览器</li>
  <li>第二步：输入网址</li>
  <li>第三步：按回车</li>
</ol>

<!-- 从指定数字开始编号 -->
<ol start="3">  <!-- 从3开始计数 -->
  <li>第三步</li>
  <li>第四步</li>
</ol>
```
### c.自定义
```
<dl>
  <dt>HTML</dt>  <!-- 术语（Definition Term） -->
  <dd>超文本标记语言，用于描述网页结构。</dd>  <!-- 解释（Definition Description） -->
  
  <dt>CSS</dt>
  <dd>层叠样式表，用于美化网页样式。</dd>
</dl>
```
## 6.表格
表格用于展示二维数据（如成绩单、价格表），完整结构包括表头、表体、表尾
### 基础格式
```
<table border="1" cellpadding="10" cellspacing="0">
  <!-- 表头（可选，通常放列标题） -->
  <thead>
    <tr>  <!-- 行 -->
      <th>姓名</th>  <!-- 表头单元格（自动加粗居中） -->
      <th>年龄</th>
      <th>性别</th>
    </tr>
  </thead>
  
  <!-- 表体（核心内容区） -->
  <tbody>
    <tr>
      <td>张三</td>  <!-- 普通单元格 -->
      <td>20</td>
      <td>男</td>
    </tr>
    <tr>
      <td>李四</td>
      <td>22</td>
      <td>女</td>
    </tr>
  </tbody>
  
  <!-- 表尾（可选，放总结信息） -->
  <tfoot>
    <tr>
      <td colspan="3">总计：2人</td>  <!-- colspan：跨列合并（合并3列） -->
    </tr>
  </tfoot>
</table>
```
### 关键属性
- border：表格边框宽度（0 为无边框）
- cellpadding：单元格内容与边框的间距（内边距）
- cellspacing：单元格之间的间距（通常设为 0 消除缝隙）
- colspan：跨列合并（如 colspan="2" 表示当前单元格占 2 列）
- rowspan：跨行合并（如 rowspan="2" 表示当前单元格占 2 行）
### 合并栗子
```
<table border="1" cellspacing="0">
  <tr>
    <td rowspan="2">姓名</td>  <!-- 跨行合并2行 -->
    <td>张三</td>
  </tr>
  <tr>
    <!-- 这里少一个<td>，因为上面的单元格跨行了 -->
    <td>李四</td>
  </tr>
  <tr>
    <td colspan="2">合计2人</td>  <!-- 跨列合并2列 -->
  </tr>
</table>

```

## 7.表单
表单用于收集用户输入（如登录、注册、搜索），核心是 <form> 容器 + 输入控件
### a.基础结构
```
<form 
  action="/submit"  <!-- 表单提交的地址（后端接口） -->
  method="post"     <!-- 提交方式：get（数据在URL中，适合简单查询）、post（数据隐藏，适合敏感信息） -->
  onsubmit="return checkForm()"  <!-- 提交前执行JS验证（可选） -->
>
  <!-- 表单控件 -->
</form>

```
### b.文本输入框
```
<!-- 普通文本 -->
<input 
  type="text" 
  name="username"  <!-- 提交时的参数名（后端接收用） -->
  value="默认值"   <!-- 初始显示的内容 -->
  placeholder="请输入用户名"  <!-- 提示文字（未输入时显示） -->
  maxlength="10"   <!-- 最大输入长度 -->
  required         <!-- 必填项（提交时会验证） -->
  readonly         <!-- 只读（不能修改） -->
  disabled         <!-- 禁用（灰色，不能交互） -->
>

<!-- 密码框（输入内容隐藏为圆点） -->
<input type="password" name="password" placeholder="请输入密码">
```
### c.单选按钮(只能选一个)
```
<!-- name相同的单选按钮为一组，互斥 -->
<input type="radio" name="gender" id="male" value="男">
<label for="male">男</label>  <!-- label与input绑定（点击文字也能选中） -->

<input type="radio" name="gender" id="female" value="女" checked>  <!-- checked：默认选中 -->
<label for="female">女</label>

```
### d.复选框（可多选）
```
<input type="checkbox" name="hobby" id="book" value="读书" checked>
<label for="book">读书</label>

<input type="checkbox" name="hobby" id="sport" value="运动">
<label for="sport">运动</label>
```
### e.下拉菜单
```
<select name="city">
  <option value="">请选择城市</option>  <!-- 提示项 -->
  <option value="beijing">北京</option>
  <option value="shanghai" selected>上海</option>  <!-- selected：默认选中 -->
  <option value="guangzhou">广州</option>
</select>

<!-- 允许多选（按住Ctrl键） -->
<select name="fruit" multiple size="2">  <!-- size：显示的选项数量 -->
  <option value="apple">苹果</option>
  <option value="banana">香蕉</option>
</select>
```
### d.多行文本框
```
<textarea 
  name="intro" 
  rows="4"  <!-- 显示的行数 -->
  cols="30"  <!-- 显示的列数（宽度） -->
  placeholder="请输入个人简介"
>默认内容</textarea>  <!-- 标签内的内容是默认值 -->
```
### e.按钮
```
<!-- 提交按钮（触发表单提交） -->
<input type="submit" value="提交">

<!-- 重置按钮（清空表单内容） -->
<input type="reset" value="重置">

<!-- 普通按钮（需配合JS使用） -->
<input type="button" value="点击" onclick="alert('Hello')">

<!-- 更灵活的按钮标签（推荐） -->
<button type="submit">提交</button>  <!-- 类型同input，内容可以是文字/图片 -->
```
### f.其他控件
```
<!-- 文件上传 -->
<input type="file" name="avatar" accept="image/*">  <!-- accept：限制上传类型（如只允许图片） -->

<!-- 隐藏域（提交后端但不显示给用户） -->
<input type="hidden" name="id" value="123">

```
## 8.语义化标签
- \<header>	页头	网站 logo、导航栏、页面标题
- \<nav>	导航栏	主导航链接、菜单
- \<main>	主要内容	页面核心内容（一个页面只一个<main>）
- \<article>	独立文章	博客、新闻、评论、帖子
- \<section>	区块 / 章节	页面中的一个独立部分（如 “简介”“联系方式”）
- \<aside>	侧边栏	广告、相关推荐、作者信息
- \<footer>	页脚	版权信息、联系方式、备案号
- \<figure>	媒体容器（图片 + 说明）	配合<figcaption>使用
- \<figcaption>	媒体说明文字	放在<figure>内，解释图片 / 视频
### 语义化标签实例
```
<!DOCTYPE html>
<html>
<head>
  <title>我的博客</title>
</head>
<body>
  <header>  <!-- 页头 -->
    <h1>我的技术博客</h1>
    <nav>  <!-- 导航 -->
      <a href="/home">首页</a>
      <a href="/article">文章</a>
    </nav>
  </header>

  <main>  <!-- 主要内容 -->
    <article>  <!-- 文章主体 -->
      <h2>HTML语义化标签详解</h2>
      <p>语义化标签能让代码更清晰...</p>
      <figure>  <!-- 图片+说明 -->
        <img src="example.jpg" alt="语义化结构示意图">
        <figcaption>图1：语义化页面结构</figcaption>
      </figure>
    </article>

    <aside>  <!-- 侧边栏 -->
      <h3>相关推荐</h3>
      <ul>
        <li><a href="#">CSS入门</a></li>
      </ul>
    </aside>
  </main>

  <footer>  <!-- 页脚 -->
    <p>© 2023 我的博客 版权所有</p>
  </footer>
</body>
</html>

```












