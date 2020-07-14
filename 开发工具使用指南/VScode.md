##### 主题设置

- 文件>首选项>颜色主题（Ctrl+K Ctrl+T）
- Ctrl+Shift+P>输入theme

F3：查找下一个

Ctrl+H：替换

Ctrl+Shift+A：块注释

Ctrl+Shift+Enter：上方插入一行

Ctrl+Enter：下方插入一行

Ctrl+Shift+F：文件夹查找

Alt+Shift+F：格式化代码

##### 快捷键映射

- 文件>首选项>快捷键映射

### Git

##### git流程

三个仓库：本地，远程，工作区

![](C:\Users\Administrator\Documents\game\git流程.png)

- 代码管理工具

鼠标右键：Git Bash Here：在当前位置打开git命令行

 配置用户信息：`git config --global user.name 'Fascinating-W'`

配置邮箱：`git config --global user.email '805391114@qq.com'`

克隆远程仓库：`git clone 'https://github.com/Fascinating-W/vscode.git'`

添加文件：`git add 文件名`

提交文件：`git commit -m 'add index.js'[文件名]`(' '内为提示信息)

推送到远程仓库：`git push`

拉取代码：`git pull`

找回删除文件：`git checkout 文件名`

#### vscode提交更新的代码至远程仓库

工具栏>源代码管理器>对号提交>小三点选择推送

#### 推荐插件

1. css peek：可以在html界面跟踪css的样式，并跳转至css的样式位置
2. Prettier：代码格式化
3. icon fonts：图标集
4. Auto Rename Tag：自动重命名标签（改了开始标签，自动修改结束标签）
5. HTML Boilerplate：html模板
6. Color info：颜色提示
7. Auto close tag：自动闭合标签
8. HTML CSS Support：html中css class的智能提示（提示css中已有的类样式）