## Shell Script

赋值语法`foo=bar`
访问变量中存储的值`$foo`
shell空格会起到分割参数的作用

原义字符串`'`
转义字符串`"`

```bash
foo=bar
echo "$foo"
# 打印 bar
echo '$foo'
# 打印 $foo
```

支持`if,case,while,for`
- `$0` 脚本名
- `$1~$9` 脚本的参数
- `$@` 所有参数
- `$#` 参数个数
- `$?` 前一个命令的返回值
- `$$` 当前脚本的进程识别码
- `!!` 完整的上一条命令，包括参数
- `$_` 上一条命令的最后一个参数，如果使用交互式shell，可以在按下Esc后键入`.`来获取这个值。

`STDOUT`返回输出值
`STDERR`返回错误及错误码
返回值为0表示正常执行，其他所有非0都表示有错误发生

退出码可以搭配`&&`和`||`来使用，进行条件判断，同一行的多个命令可以用`;`分隔
程序`true`的返回值永远是0，`false`的返回值永远是1

以变量的形式获取一个命令的输出
- 命令替换（command substitution）
    `$(CMD)`:首先调用cmd，然后用得到的返回值替换
- 进程替换（porcess substitution）
    `<(CMD)`:首先执行cmd并将结果输出到一个临时文件中，并将其替换为临时文件名
```bash
test #提供了多种命令用于表文件类型和值
[] #传统的test命令的一种昂方式，用于条件测试，使用空格分隔参数，使用特定的转义字符来进行字符串匹配等操作
[[]] #扩展表达式语法，不需要转义符号进行字符串匹配等操作，支持更多的比较运算符和模式匹配功能
```

通配（globbing）
- 通配符
    - `?`匹配一个
    - `*`匹配任意个字符
- `{}`包含公共子串时，可以用花括号来自动展开这些命令

[shellcheck](https://www.shellcheck.net/)这样的工具可以帮助你定位脚本中的错误

`shebang`是一个特殊注释，放在脚本第一行，用于指定解释器执行这个脚本文件
```bash
#!/path -[argument] 
# 可以搭配`env`命令增强脚本的可移植性
```
## Shell工具
### 查看命令如何使用

`-h,--help,man(manual)`
可以安装一下[TLDR pages](https://tldr.sh/)，以防出现手册太繁杂的情况
### 查找文件
`find`
`fd`更简单、快速
`locate`更更快，只能通过文件名

> shell的哲学之一就是寻找（更好用的）替代方案

### 查找代码
`grep`
代替方案`ack,ag,rg(ripgrep)`
`rg`速度快，语法符合直觉

### 查找shell命令
`history`可以跟`grep`命令结合起来进行查找

`Ctrl+R`之后可以输入子串来进行匹配
`fzf`模糊查找工具
`fishshell`基于历史的自动补全
可以通过修改`.bashrc或.zshrc`来修改shell histroy的行为

### 文件夹导航
```bash
alias
ln - make links between files
fasd #基于frecency对文件进行排序
autojump
# 概览目录结构
tree
broot
# 更加完整的文件管理器
nnn
ranger
```

