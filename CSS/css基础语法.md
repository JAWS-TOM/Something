# CSS基础语法
## 选择器  

### 基础选择器
1. 标签选择器  
   直接使用 HTML 标签名（如 p、div、h1），匹配页面中所有该标签的元素。
   ```
   /* 所有<p>标签文字设为灰色，字体大小14px */
   p {
   color: #666;
   font-size: 14px;
   }
   ```
2. 类选择器（class 选择器）
   类名前加 .（如 .active、.btn），匹配所有包含指定类名的元素（一个元素可同时有多个类，类名用空格分隔）。
   ```
   /* 所有类名为box的元素设置宽高和边框 */
    .box {
    width: 100px;
    height: 100px;
    border: 1px solid #ccc;
    }
    /* 类名为highlight的元素设置黄色背景 */
    .highlight {
    background: yellow;
    }
   ```
   ```
   <div class="box">普通盒子</div>
   <div class="box highlight">高亮盒子</div>

   ```
3. ID 选择器
   ID 名前加 #（如 #header、#logo）,匹配页面中唯一具有该 ID 的元素（HTML 规范中 ID 需全局唯一）。
   ```
   /* ID为page-title的元素设置字体大小和居中 */
    #page-title {
    font-size: 28px;
    text-align: center;
    }
   ```
   ```
   <h1 id="page-title">首页标题</h1>
   ```
4. 通配符选择器
   *（星号）,匹配页面中所有元素（包括 <html>、<body> 等）
   常用场景：清除所有元素的默认内外边距（CSS 重置）。
   ```
   /* 清除所有元素的默认margin和padding */
   * {
   margin: 0;
   padding: 0;
   }

   ```
### 组合选择器
1. 后代选择器（包含选择器）
   多个选择器用空格分隔（如 父选择器 后代选择器）。
   可以匹配 “父选择器” 包含的所有 “后代选择器” 元素（包括直接子元素和嵌套更深的元素）。
   ```
   <ul class="menu">
    <li>菜单项1</li>
     <li>
       <ul>
        <li>子菜单项1</li>  <!-- 会被匹配 -->
       </ul>
     </li>
   </ul>

   ```
   ```
   /* .menu内所有li元素（无论嵌套层级）文字设为蓝色 */
   .menu li {
   color: blue;
   }
   ```
2. 子选择器（直接后代选择器）
   多个选择器用 > 分隔（如 父选择器 > 子选择器）。
   仅匹配 “父选择器” 的直接子元素（不包含嵌套更深的后代）。
   ```
   /* 仅匹配.menu的直接子元素li（不包含子菜单的li） */
   .menu > li {
   font-weight: bold;  /* 一级菜单项加粗 */
   }
   ```
3. 相邻兄弟选择器
   两个选择器用 + 分隔（如 前元素 + 后元素）。
   匹配 “前元素”紧邻的下一个同级元素（必须同属一个父元素）。
   ```
   /* h2后面紧邻的p元素设置上外边距 */
   h2 + p {
   margin-top: 15px;
   }
   ```
   ```
   <h2>标题</h2>
   <p>第一段文字</p>  <!-- 紧邻h2的p，会被匹配 -->
   <p>第二段文字</p>  <!-- 不紧邻h2，不会被匹配 -->
   ```
4. 通用兄弟选择器
   两个选择器用 ~ 分隔（如 前元素 ~ 后元素）。
   匹配 “前元素”后面所有同级元素（无需紧邻，但必须同属一个父元素）。
   ```
   /* h2后面所有同级p元素设置颜色为灰色 */
   h2 ~ p {
   color: #999;
   }
   ```
5. 群组选择器（并集选择器）
   多个选择器用 , 分隔（如 选择器1, 选择器2, 选择器3）。
   同时对多个选择器匹配的元素应用相同样式，避免重复代码。
   ```
   /* h1、h2、h3标签共用相同样式 */
   h1, h2, h3 {
   margin-bottom: 10px;
   color: #333;
   }

   ```
### 属性选择器（根据元素属性匹配）
1. 基础属性选择器
   [属性名]{} 匹配所有包含该属性的元素。
   ```
   /* 所有带href属性的元素（通常是a标签）设置颜色 */
   [href] {
   color: #0066cc;
   }
   ```
2. 属性值完全匹配
   [属性名="值"]{} 匹配属性值完全等于指定值的元素。
   ```
   /* 仅匹配type="text"的input元素 */
    input[type="text"] {
    border: 1px solid #ccc;
    }
   ```
   ```
   <input type="text">
   <input type="password">
   ```
3. 属性值包含指定字符（空格分隔）
   [属性名~="值"]{} 匹配属性值中包含指定单词的元素，单词以空格分隔。
   ```
   /* 匹配class中包含"box"单词的元素 */
    [class~="box"] {
    width: 100px;
    height: 100px;
    }
   ```
   ```
   <div class="box red">红色盒子</div>
    <div class="box green">绿色盒子</div>
   ```
4. 属性值以指定字符开头
   [属性名^="值"]{} 匹配属性值以指定字符开头的元素。
   ```
   /* 匹配href以"https://"开头的a标签（安全链接） */
    a[href^="https://"] {
    text-decoration: none;
    }
   ```
5. 属性值以指定字符结尾
   [属性名$="值"]{} 匹配属性值以指定字符结尾的元素。
   ```
   /* 匹配src以".png"结尾的img标签（PNG图片） */
   img[src$=".png"] {
   border: 2px solid #fff;
   }
   ```
6. 属性值包含指定字符（任意位置）
   [属性名*="值"]{} 匹配属性值任意位置包含指定字符的元素。
   ```
   /* 匹配href中包含"example"的链接 */
   a[href*="example"] {
   color: orange;
   }
   ```
### 伪类选择器（根据元素状态 / 位置匹配）
1. 状态伪类（元素交互状态）
   :hover：鼠标悬停在元素上时。
   ```
   /* 鼠标悬停在a标签上时变色 */
   a:hover {
   color: red;
   }
   ```
   :active：元素被点击（激活）时。
   ```
   /* 按钮被点击时背景变深 */
   button:active {
   background: #333;
   }
   ```
   :focus：元素获得焦点时（常用于表单输入框）。
   ```
   /* 输入框获焦时显示蓝色边框 */
   input:focus {
   outline: none;
   border-color: #0066cc;
   }
   ```
   :visited：链接被访问后（仅用于 a 标签）。
   ```
   /* 已访问链接变灰色 */
   a:visited {
   color: #999;
   }
   ```
   :link：链接未被访问时（仅用于 a 标签，需放在:visited 前）。
   ```
   a:link {
   color: #0066cc;
   }
   ```
2. 结构伪类（元素在 DOM 中的位置）
   :first-child：匹配父元素的第一个子元素。
   ```
   /* ul的第一个li元素加粗 */
   ul li:first-child {
   font-weight: bold;
   }
   ```
   :last-child：匹配父元素的最后一个子元素。
   ```
   /* 列表最后一个li元素添加下外边距 */
   ul li:last-child {
   margin-bottom: 20px;
   }
   ```
   :nth-child(n)：匹配父元素的第 n 个子元素（n 可为数字、公式或关键词）。
   ```
   /* 匹配第2个li元素 */
   ul li:nth-child(2) {
   color: red;
   }
   /* 匹配偶数位置的li（2、4、6...） */
   ul li:nth-child(even) {
   background: #f5f5f5;
   }
   /* 匹配奇数位置的li（1、3、5...） */
   ul li:nth-child(odd) {
   background: #fff;
   }
   ```
   :only-child：匹配父元素中唯一的子元素。
   ```
   /* 若div中只有一个p元素，则设置字体大小 */
   div p:only-child {
   font-size: 16px;
   }
   ```
5. 其他常用伪类
   :empty：匹配没有任何子元素（包括文本） 的元素。
   ```
   /* 空div显示灰色背景 */
   div:empty {
   background: #eee;
   height: 20px;
   }
   ```
   :checked：匹配被选中的表单元素（如单选框、复选框）。
   ```
   /* 选中的复选框后文字加粗 */
   input:checked + span {
   font-weight: bold;
   }
   ```
   :not(选择器)：否定伪类，匹配不满足指定选择器的元素（反向匹配）。
   ```
   /* 所有不是.active类的li元素设为灰色 */
   li:not(.active) {
   color: #999;
   }
   ```
### 伪元素选择器（创建虚拟元素）
用于在元素的特定位置插入 “虚拟元素”（不属于 DOM，仅用于样式），语法以 :: 开头（CSS3 规范，旧版可用单冒号，最好用双冒号）。
   - ::before 在元素内容的前面插入虚拟元素，需配合 content 属性使用。
   ```
   /* 在p标签内容前添加一个箭头 */
   p::before {
     content: "→";  /* 必须设置content，可空（content: ""） */
     color: red;
     margin-right: 5px;
   }
   ```
   - ::after 在元素内容的后面插入虚拟元素，需配合 content 属性使用。
   ```
   /* 在链接后面添加一个小图标（或文字） */
   a.external::after {
     content: "(外部链接)";
     font-size: 12px;
     color: #999;
   }
   ```
   - ::first-letter 匹配元素第一个字符（仅用于块级元素）。
   ```
   /* 段落首字放大 */
   p::first-letter {
     font-size: 2em;
     color: red;
   }
   ```
   - ::first-line 匹配元素第一行文字（仅用于块级元素，受容器宽度影响）。
   ```
   /* 段落第一行文字加粗 */
   p::first-line {
     font-weight: bold;
   }
   ```


















   
  
