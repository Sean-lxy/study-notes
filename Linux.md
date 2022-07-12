#### 1. `ls` 列出文件和目录

1. `ls` 列出文件和目录
2. `ls  -la` 由 `-a` 显示所有文件和目录（包括隐藏） 和  `-l` 显示详细列表组成。

#### 2. `chown` 更改文件属主，也可以同时更改文件属组

```shell
# -R：递归更改文件属组
chown [-R] 属主名 文件名

chown [-R] 属主名：属组名 文件名

```

#### 3. `chmod` 更改文件权限

权限除了用 `r` 、`w`、`x`  这种方式表示，也可以用数字表示，数字和字母的对应关系为：

- r:4
- w:2
- x:1

```shell
# -R：递归更改文件权限
chmod [-R] xyz 文件或目录

# xyz分别表示 Owner、Group、Others的权限
chmod 750 index.html
# Owner权限为7，可读可写可执行；Group权限为5，可读可执行；Other的权限为0，不可读不可执行

```

还可以通过使用符号类型改变权限的方式：

三种身份分别简写为 `u`、 `g`、`o` ，用 `a` 表示所有身份。使用 `+`、`-`、`=` 表示加入、去除、设定权限

```shell
chmod u+x,g-x,o-x index.html

chmod u=rwx,g=rx,o=r index.html 

```

#### 4. `su` 切换身份

#### 5. `whoami` 显示用户名

#### 6. `pwd` 显示当前目录

#### 7. `cd` 切换工作目录

#### 8. `mkdir` 创建目录

- `mkdir` 创建目录
- `mkdir -o ` 递归创建目录

#### 9. `touch` 创建文件

#### 10. `echo` 打印输出

```shell

# 显示转义字符
echo "\" test content \"";

# 创建或覆盖文件内容
echo "test content" > index.html

# 追加文件内容
echo "tet content" >> index.html

```

#### 11.`cat` 连接文件并打印输出

```shell

# 查看文件内容
cat index.html

# 清空内容
cat /dev/null > index.html

# 写入内容
cat index.html > second.html

# 追加写入
cat index.html >> second.html

# 多文件追加
cat inedx.html second.html >> third.html

```

#### 12. `cp` 复制文件或目录

```shell

cp -r website/ static

```

#### 13.`mv` 移动并重命名

```	shell

# 文件改名
mv index.html index2.html

# 隐藏文件
mv index.html .index.html

# 移动文件
mv /homw/www/index.html /home/static/

# 批量移动

mv /homw/www/website/* /homw/www/static

```

#### 14. `rm` 删除一个文件或目录

```shell

# rm file

# -f 表示强制删除
# -r 表示目录下的所有文件

rm -rf /*

```

#### 15. `vi` or `vim` 

Vim 分为三种模式，分别是：命令模式、输入模式、底线命令模式

命令模式下的命令：

- i 切换到输入模式
- x 删除当前光标所在处的字符
- : 切换到命令模式

输入模式下：

- esc 回到命令模式
- : 切换到命令模式

命令模式下：

- w 保存文件
- q 退出程序

####  16. `ssh` 远程连接工具

```shell

ssh [OPTIONS] [-p PORT] [USER@]HOSTNAME [COMMAND]

```

