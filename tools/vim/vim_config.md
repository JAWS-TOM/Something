# 通用vim配置  
先创建配置文件.vimrc
一般在在当前用户空间`vim ～/.vimrc`
```
" ===================== 显示方面 =====================
set number                  " 显示绝对行号，方便定位
set relativenumber          " 显示相对行号，移动更直观
set cursorline              " 高亮当前行，明确光标位置
set cursorcolumn            " 高亮当前列，便于代码对齐
set signcolumn=yes          " 固定符号列，避免界面跳动（用于断点/错误提示）
set laststatus=2            " 始终显示状态栏
set statusline=%F%m%r%h%w\ [格式=%{&ff}]\ [编码=%{&enc}]\ [类型=%Y]\ [行=%l,列=%v][%p%%]\ %{strftime(\"%Y-%m-%d\ %H:%M\")}  " 状态栏显示：路径、编码、位置、时间等
set wildmenu                " 命令行补全显示菜单
set wildmode=longest,full   " 命令补全：先匹配最长公共部分，再展开完整列表

" ===================== 编辑方面 =====================
set showcmd                 " 实时显示输入的部分命令，避免误输
set autoindent              " 新行继承上一行缩进
set smartindent             " 智能缩进（适配C/C++等语言）
set expandtab               " Tab键转为空格，避免格式混乱
set tabstop=4               " Tab等效4个空格
set shiftwidth=4            " 自动/手动缩进每次4个空格
set softtabstop=4           " Backspace一次删4个空格
set backspace=indent,eol,start  " 退格键可删缩进、换行符、行首内容
set scrolloff=3             " 光标靠窗口边界时自动滚动，保留上下文
set sidescrolloff=5         " 光标靠左右边界时横向滚动
set wrap                    " 长行自动换行
set linebreak               " 换行不拆分单词

" ===================== 搜索与查找 =====================
set ignorecase              " 搜索忽略大小写
set smartcase               " 搜索含大写时自动区分大小写
set hlsearch                " 高亮搜索结果
set incsearch               " 增量搜索（输入即实时匹配）
set gdefault                " 替换命令默认作用于整行所有匹配项

" ===================== 编码与兼容性 =====================
set enc=utf-8               " 内部处理用UTF-8编码
set fenc=utf-8              " 保存文件默认UTF-8编码
set fencs=utf-8,gbk,gb2312,cp936  " 自动识别多种中文编码，避免乱码
set fileformats=unix,dos,mac  " 兼容Windows/Linux/Mac换行格式

" ===================== 方便 =====================
set nobackup                " 不生成.xxx~备份文件
set noswapfile              " 不生成.xxx.swp交换文件
set autoread                " 外部修改文件后自动重新读取
set confirm                 " 危险操作（如未保存关闭）弹确认
set showmatch               " 输入括号时高亮匹配项
set matchtime=2             " 括号匹配高亮持续0.2秒
set mouse=a                 " 全模式支持鼠标操作（点击、选中等）
set encoding=utf-8          " 统一编码，避免中文注释乱码

```

