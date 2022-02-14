#### Neovim配置

> mkdir ~/.config/nvim
>
> nvim  ~/.config/nvim/init.vim

#### 安装配色主题

> 1.mkdir ~/.config/nvim/colors
>
> 2.下载的配色文件如monokai.vim复制到此文件夹
>
> 3.init.vim中指定主题：colorscheme monokai

#### 安装plug.vim

> mkdir ~/.config/nvim/autoload
>
> init.vim中配置：
>
> ```
> call plug#begin('~/.config/nvim/plugApp') //括号里的路径可以根据实际情况设置
> Plug 'junegunn/vim-easy-align'
> call plug#end()
> ```

#### 安装Coc.nvim

> 出现please install dependencies and compile coc .nvim by: yarn install错误解决方法
>
> 1.npm install -g yarn     安装yarn
>
> 2.到~/.vim/bundle/coc.nvim的文件目录下执行:yarn install

#### neovim无法获取用户输入解决方法

> ​	:te/:terminal 调出终端单独运行该文件
---
### lua配置nvim
#### 什么是 Language Server Protocol ?
> Language Server Protocol (LSP) 是微软为开发工具提出的一个协议， 它将编程工具解耦成了Language Server 与 Language Client 两部分。

![输入图片说明](lsp%E5%9B%BE%E8%A7%A3.jpg)
Client 专注于页面样式实现， Server 负责提供语言支持，包括常见的自动补全，跳转到定义，查找引用，悬停文档提示等功能。
而我们所说的 Neovim 内置 LSP 就是 client 端的实现，这样我们就可以链接到和 VSCode 相同的 language servers ，实现高质量的语法补全。

#### 安装步骤
1. 安装nvim-lspconfig
2. 安装对应 language server
3. 配置对应语言 require('lspconfig').xx.setup{…}
4. :lua print(vim.inspect(vim.lsp.buf_get_clients())) 查看 LSP 连接状态
```
├── init.lua                              入口文件，这里负责加载所有lua文件夹里的文件
└── lua                                   所有 lua 配置文件
    ├── basic.lua                         Neovim 的基础配置
    ├── keybindings.lua                   快捷键配置
    ├── lsp                               内置 LSP  (Language Server Protocol) 配置
    │   ├── diagnostic_signs.lua
    │   ├── language_servers.lua
    │   └── nvim-cmp-config.lua
    ├── plugin-config                     各个插件配置在这个文件夹
    │   ├── bufferline.lua
    │   ├── comment.lua
    │   ├── nvim-autopairs.lua
    │   ├── nvim-colorizer.lua
    │   ├── nvim-tree.lua
    │   ├── nvim-treesitter.lua
    │   ├── rust-tools.lua
    │   ├── surround.lua
    │   ├── telescope.lua
    │   └── which-key.lua
    └── plugins.lua                        插件安装管理
```