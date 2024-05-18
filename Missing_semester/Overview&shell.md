# shell是什么

核心功能：允许你执行程序，输入并获取某种半结构化的输出

```Bash
missing:~$
# hostname: missing
# current working directory: ~(home)
# user: $(not root)
```
shell 基于空格分割命令进行解析，如果希望传递空格，要么使用单引号、双引号，要么使用转义符号`\`

shell是一个编程环境，具有变量、条件、循环和函数；如果要求shell执行某个它并不了解的关键字，就会去咨询环境变量`$PATH`（由`:`分割）

```bash
missing:~$ which echo #列出该程序名代表的是哪个程序
/bin/echo
```

`/`根目录，以`/`开头代表其为绝对路径，其他都是相对路径
`.`当前目录
`..`上级目录
