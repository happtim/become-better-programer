
[文件目录导航](#文件目录导航)
  - [pwd - 当前工作目录](#当前工作目录)
  - [cd - 更改当前路径](#更改当前路径)
  - [ls - 列出目录](#列出目录)
  - [FHS - 文件层次标准](#文件层次标准)
  - [file - 文件类型](#文件类型)

[操作文件与目录](#操作文件与目录)
  - [mkdir - 创建目录](#创建目录) 
  - [cp - 复制文件和目录](#复制文件和目录)
  - [mv - 移动和重命名文件](#移动和重命名文件)
  - [rm - 删除文件和目录](#删除文件和目录)
  - [ln - 创建链接](#创建链接)

# 文件目录导航

- ## 当前工作目录

  `pwd` - **p**rint name of current/**w**orking **d**irectory

  ```
  $ pwd 
  $ /home/gexiang
  ```

- ## 更改当前路径

  `cd` - **c**hange current **d**irectory to dir 

  * ### 常用快捷切换目录

    * cd/cd~ 将工作目录改变成主目录
    * cd- 将工作目录改编成先前工作目录

  * ### 绝对路径与相对路径
      * 绝对路径

        从根目录开始,后面接一个又一个文件目录,直到到达指定的目录或者文件.

      * 相对路径

        绝对路径是从根目录开始,通向目标目录,而相对路径是从工作目录开始,通向目标目录.

      特殊符号 `.` 代表当前目录,`..` 代表上层目录.

      ```
      $ cd /usr/bin/
      $ pwd
      /usr/bin
      $ cd ..
      $ pwd
      /usr
      ```

* ## 列出目录

  `ls` - **l**i**s**t directory contents

  * ### 常用参数
    * -l 使用详细格式现实结果
    * -a 列出所有文件,包括以点开头的文件(隐藏文件)
    * -h --human-readable 以详细格式列出时,以人们可读方式现实文件大小
    * -d 将参数按照目录本身列出,而不列出目录内容
    * -t 按照修改时间排序
    * -S 按照文件大小排序

    ```
    $ ls 
    Desktop 　 Documents 　 Music 　 Pictures 　 Public 　 Templates 　 Videos
    ```

  * ### 详细输出
    ```
    $ ls -l 
    total 56 
    drwxrwxr-x 2 me me 4096 2012-10-26 17:20 Desktop 
    drwxrwxr-x 2 me me 4096 2012-10-26 17:20 Documents 
    drwxrwxr-x 2 me me 4096 2012-10-26 17:20 Music 
    drwxrwxr-x 2 me me 4096 2012-10-26 17:20 Pictures 
    drwxrwxr-x 2 me me 4096 2012-10-26 17:20 Public
    ```

    输出解释:

    * drwxrwxr-x 对文件的访问权限.第一个字符表示文件的类型。在不同类型之间,开头的“-”表示该文件是一个普通文件,d表示目录,l表示是一个链接文件.紧接着的三个字符表示文件所有者的访问权限,再接着的三个字符表示文件所属组中成员的访问权限,最后三个字符表示其他所有人的访问权限.

    * 数字2 文件硬链接数.
    * me 文件所有者的用户名.
    * me 文件所属用户组的名称.
    * 4094 文件以字节标识的大小.
    * 2012-10-26 17:20 上次修改文件的日期和时间.
    * Desktop 文件名.

* ## 文件层次标准

  在Linux系统中,文件系统布局与其他类UNIX系统很相似.实际上,一个已经发布的名为Linux文件系统层次标准(LinuxFilesystemHierarchyStandard)的标准,已经详细阐述了这个设计.并不是所有Linux发行版都严格符合该标准,但大部分与之很接近.

  * / 根目录,一切从这里开始
  * /bin 包含系统启动和运行所必须的二进制文件
    * /boot 包含Linux内核,最初的RAM磁盘映像以及启动加载程序
    * /dev 包含设备节点的目录
    * /etc 包含了所有系统层面的配置文件
    * /home 每个用户都会在/home目录中有自己的一个主目录
    * /lib 包含核心系统程序使用的共享库文件
    * /lost+found 每个使用Linux文件系统格式化分区或设备都会有这个目录,当文件系统崩溃时,该目录用于恢复分区
    * /media 包含可移除媒体设备的挂载点.如:USB,CD-ROM等.
    * /mnt 包含手动挂载的可移除设备的挂载点.
    * /opt 存放可能安装在系统中的商业软件.
    * /proc 从文件的角度来说,它不是存储在硬盘中的真正的文件系统,反而是一个Linux内核维护的虚拟文件系统.
    * /root root账户的主目录
    * /sbin 存放系统级别的可执行重要程序,如重启.为root用户使用.
    * /tmp 供用户存放各种程序的零时文件目录.
    * /usr 他包含普通用户使用的所有程序和相关文件.
    * /usr/bin Linux发行版安装的可执行程序.
    * /usr/lib  /usr/bin目录中程序使用的共享库
    * /usr/local 是非系统发行版自带,但打算让系统使用的程序安装目录.通常为自己编译的程序.
    * /usr/sbin 包含系统管理程序
    * /usr/share 包含了/usr/bin中的程序所使用的全部共享数据,如:默认配置文件,图标等.
    * /usr/share/doc 安装在系统中大部分程序包含一些文档文件.
    * /var 除了 /tmp和/home目录之外,其余的目录相对来说都是静态的,也就是安装完之后文件内容是不变的.其他可以改变的文件存放在/var目录中.如:数据库,用户邮件.
    * /var/log 记录了各种系统活动,这些文件非常重要,应该时不时监控他们.

* ## 文件名说明
  
  * ### 隐藏文件
    以"."字符开头的文件名是隐藏的.ls不会列出不会列出这些文件,需要使用`ls -a`.在创建用户账户时,主目录会放置一些隐藏文件来配置账户信息.

  * ### 文件区域大小写
    文件名和命令是区分大小写的. File1和file1是两个不同的文件.
    而在Windows中,文件名是不区分大小写的.File1和file1是一个文件.

  * ### 文件没有文件扩展名概念
    Linux系统中的文件名不反应文件的内容和类型.我们可以按照自己的喜好随意给文件名.文件的内容或用途由其他方式来决定.

    使用file命令来确定文件的类型.
    file *filename*

    ```
    $ file picture.jpg
    picture.jpg: JPEG image data, JFIF standard 1.01
    ```

  * ### 文件名可以包含空格和标点符合
    但是在创建文件的时候,仅句号,连字符,下划线是可以使用的.文件名中不要使用空格,会在使用很多命令行的时候使命令解析错参数.

# 操作文件与目录

* ## 创建目录

  `mkdir` - **m**a**k**e **dir**ectories

  * ### 常用参数
    * -p 若所要建立目录的上层目录目前尚未建立,则会一并建立上层目录.

  ```
  $ mkdir dir1 dir2 dir3
  $ mkdir -p dir1/dir2/dir3
  ```

* ## 复制文件和目录

  `cp` - **c**o**p**y files and directories

  * ### 常用参数
  * -a 复制文件和目录及其属性. 相当于 -dR --preserve=all
  * -R/r 递归复制目录及其内容. 
  * -s 创建符号链接代替复制文件
  * -l 创建硬链接代替复制文件
  * -i 覆盖提示. 不提示使用-n不提示.
  * -u --update 当原文文件比目标文件新或者目标文件丢失才复制.
  * -d 相当于 --no-dereference --preserve=links. 复制符号链接和硬链接.
  * -L --dereference 复制时复制符号链接所指向的本体.
  * -P --no-dereference  复制时不复制符号链接所指向的文件,只是复制符号链接本身.
  * --preserve[=Attr_List] 保留指定属性默认为(mode,ownship,timestamp).附加属性为context,links,xattr,all


  符号链接复制

  ```
  $ touch file
  $ cp -s file file_slink
  $ cp file_slink file_slink2
  $ cp -P file_slink file_slink3
  $ ll
  -rw-r--r-- 1 root root    0 Jul 23 09:56 file
  lrwxrwxrwx 1 root root    4 Jul 23 09:56 file_slink -> file
  -rw-r--r-- 1 root root    0 Jul 23 09:56 file_slink2
  lrwxrwxrwx 1 root root    4 Jul 23 09:57 file_slink3 -> file
  ```

  硬链接复制
  ```
  $ touch file
  $ cp -l file file_link
  $ ll -i
  1314978 -rw-r--r-- 2 root root    0 Jul 23 10:01 file
  1314978 -rw-r--r-- 2 root root    0 Jul 23 10:01 file_link

  $ cp file file_link cur/
  $ ll -i cur/
  1588232 -rw-r--r-- 1 root root 0 Jul 23 10:11 file
  1588246 -rw-r--r-- 1 root root 0 Jul 23 10:11 file_link

  $ rm -f cur/*
  $ cp --preserve=links file file_link cur/
  $ ll -i cur/
  1588232 -rw-r--r-- 2 root root 0 Jul 23 10:12 file
  1588232 -rw-r--r-- 2 root root 0 Jul 23 10:12 file_link
  ```

* ## 移动和重命名文件

  `mv` - **m**o**v**e (rename) files

  * ### 常用参数
  * -i 出现相同文件名覆盖交互式提示
  * -f 出现相同文件名覆盖不提示
  * -n 出现相同文件名不覆盖
  * -u 移动当源文件比目标文件新或者目标文件不存在.

  ```
  mv item1 item2
  ```

* ## 删除文件和目录

  `rm` - **r**e**m**ove files or directories

  * ### 常用参数
  * -f --force 忽略交互提示
  * -i 删除每个文件交互提示
  * -r/R 递归删除目录
  * -d 删除空的目录

  ```
  $ rm item1 item2
  $ rm -rf *
  ```

  类UNIX操作系统并不包含还原删除操作的命令.一旦使用rm命令,就彻底从系统中将该文件删除.

* ## 创建链接

  `ln` - make **l**i**n**ks between files

  * ### 创建硬链接
    ```
    ln file link
    ```
    硬链接是最初UNIX用来创建链接的方式,符号链接较之更为先进.

    * 硬链接不能引用自身文件系统之外的文件,不能链接不在同一磁盘分区的文件.
    * 硬链接无法引用目录.

    硬链接和文件本身并没有什么区别,使用ls -l显示的时候也没有特别的链接说明.当硬链接被删除时,只是这个链接被删除了,文件本身并没有删除,除非该文件所有的链接都被删除.

    ```
    $ ls -l
    -rw-r--r-- 1 root root      64 Mar 15 10:36 add.py

      $ ln add.py add_link_file.py
      $ ls -l
      -rw-r--r-- 2 root root      64 Mar 15 10:36 add_link_file.py
      -rw-r--r-- 2 root root      64 Mar 15 10:36 add.py
      ```

    * ### 符号链接(软链接)

      ```
      ln -s item link
      ```

      符号链接是为了克服硬链接的局限性而创建的.符号链接通过创建一个特殊类型文件,该文件包含了指向指向引用文件或目录的文本指针.非常类似与Windows系统中的快捷方式.

      符号链接指向的文件与符号链接自身文件几乎没有区别.将一些东西写入符号链接里,那么这些东西也会同样写入引用的文件内.删除一个符号链接时,只是删除符号链接,并没有删除文件本身.

      ```
      $ ls
      lrwxrwxrwx   1 root root       19 Jun 24  2018 libstdc++.so.6 -> libstdc++.so.6.0.19
      -rwxr-xr-x   1 root root   991616 May 16  2018 libstdc++.so.6.0.19
      ```

      上面闲了一个指向libstdc++.so.6.0.19 共享文件的符号链接libstdc++.so.6.其他文件使用libstdc++.so.6的程序的时候访问的是libstdc++.so.6.0.19.如果安装了新的版本如libstdc++.so.6.0.20只需要将原来链接删除重新链接so.6.0.20版本的库文件.所有程序依赖这个库so.6就重新指向了so.6.0.20版本了.假如新版本出现bug,可以重新链接回原有版本.


# 通配符
  由于shell需要经常使用文件名,因此他提供了一些特殊字符来帮助你快速指定一组文件名.这些特殊字符称为通配符.

    * \* 匹配任意多个字符 (匹配0+个)
    * ? 匹配任意单个字符 (只匹配1个)
    * [characters] 匹配任意一个属于字符集中的字符

  * ## 通配符示例
    * \* 所有文件
    * g* 以g开头的任意文件
    * Data??? 以Data开头,后面跟3个字符的任意文件
    * [abc]* 以abc中任意开头的任意文件
    * backup.[0-9][0-9][0-9] 1以backup.开头,后面紧跟3个数字的任意文件.


# 命令的使用

  * ## 命令是什么

  * **可执行程序** 可执行程序就像在/usr/bin目录里看到的所有文件一样.在该程序类别中,程序可以编译为二进制文件,比如C,C++语言编写的程序,也可以是shell,Perl,Python,Ruby等脚本语言编写的程序.
  * **shell内置命令** bash支持许多在内部称之为shell builtin的内置命令.如:cd.kill.set.pwd
  * **shell函数** shell函数是合并到环境变量中的小型shell脚本.
  * **alias** 自定义命令

  * ## 获取命令的简要描述

    whatis 程序实现匹配具体关键字的手册页的名字和一行描述

    ```
    $ whatis ls
    ls (1)               - list directory contents
    ls (1p)              - list directory contents
    ```


  * ## 识别命令

    type命令是一个shell内置命令,可以显示出要参数命令的类型.

    ```
    $ type ll
    ll is aliased to `ls -l --color=auto'

    $ type mkdir
    dir is /usr/bin/mkdir

    $ type pwd
    pwd is a shell builtin

    $ type -a cd
    cd is a function
    cd ()
    {
        __zsh_like_cd cd "$@"
    }
    cd is a shell builtin
    cd is /usr/bin/cd
    ```

  * ## 获取执行程序的位置
    
    `which`命令可以确定一个可执行文件的准确位置,`which`命令只适用于可执行程序,而不适用于内置命令和命令别名.在大型服务器中往往安装软件多个版本,此时可以方便定位出执行命令的位置.

    ```
    $ which git
    /usr/bing/git

    $which reboot
    /usr/sbin/reboot
    ```

  * ## 获取命令文档
  
    help 获取shell内置命令的帮助文档
    ```
    $ help cd
    ```
    
    --help 很多命令都有的语法选择支持参数.
    ```
    $ mkdir --help
    ```

  * ## man手册

    大多数供命令行使用的可执行文件,提供了一个称为manual或者man page的文档.该文档可以用一个`man`的特殊分页程序来查看. 大多数linux系统中,`man`命令待用`less`命令来显示手册文档
    ```
    $man man
    ```
    man命令显示文档被分成多个部分,它包括用户命令,程序接口等.如果没有指明部分编号,通常会获取第一次匹配的示例.

    * 1 用户命令
    * 2 内核系统调用的程序接口
    * 3 C库函数程序接口
    * 4 特殊文件,如设备节点和驱动程序
    * 5 文件格式
    * 6 游戏和娱乐,例如屏幕保护程序
    * 7 其他杂项
    * 8 系统管理命令


    `man 1` 会给出passwd的命令使用文档, `man 5` 会显示`/etc/passwd`的文件格式描述手册

    ```
    $ man 1 passwd
    $ man 5 passwd
    ```

  * ## 使用别名创建自己的命令

    alias name='string'

    ```
    $ alias foo='cd /usr; ls; cd -'
    $ type foo
    $ foo is aliased to 'cd /usr; ls; cd -'
    $ foo
    bin  games    java  lib64    local  share  tmp
    etc  include  lib   libexec  sbin   src
    /root
    ```

    查看在环境中定义的所有别名,可是使用不带参数的alias命令.
    ```
    $ alias
    alias cp='cp -i'
    alias egrep='egrep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias foo='cd /usr; ls; cd -'
    alias grep='grep --color=auto'
    alias l.='ls -d .* --color=auto'
    alias ll='ls -l --color=auto'
    alias ls='ls --color=auto'
    alias mv='mv -i'
    alias rm='rm -i'
    ```

# 重定向

  重定向可以把命令行的输入重定向为文件中获取内容,也可以把命令行的输出结果重定向到文件中.如果将多个命令关联起来,形成管道命令.

  * ## 标准输入,标准输出和标准错误

    ```
    $ ls -l /dev/std*
    lrwxrwxrwx 1 root root 15 Nov 10  2017 /dev/stderr -> /proc/self/fd/2
    lrwxrwxrwx 1 root root 15 Nov 10  2017 /dev/stdin -> /proc/self/fd/0
    lrwxrwxrwx 1 root root 15 Nov 10  2017 /dev/stdout -> /proc/self/fd/1

    $ echo hello world > /dev/stdout
    hello world
    ```

    与UNIX"一切都是文件"的思想一致,类似ls的程序实际上把它们的运行结果发送到了一个称为标准输出(standardoutput,通常表示为stdout)的特殊文件中,它们的状态信息则发送到了另一个称为标准错误(standarderror,表示为stderr)的文件中.默认情况下,标准输出和标准错误都将被链接到屏幕上,并且不会被保存在磁盘文件中.

    许多程序从一个称为标准输入(standard input,表示为stdin)的设备得到输入,默认情况下,标准输入连接到键盘.

    I/O重定向功能可以改变输出内容发送的目的地.也可以改变输入内容的来源地.

  * ## 标准输出重定向

    使用">"重定向操作符.IO重定向功能可以重新定义标准输出内哦让那个发送到哪里.后面接文件就可以把便准输出重定向到另一个文件中,而不是显示在屏幕上.主要用于把命令的输出内容保存到一个文件中.

    ```
    $ ls -l /usr/bin > ls-output.txt
    $ ls -l ls-output.txt
    -rw-r--r-- 1 root root 71699 Jul 23 16:09 ls-output.txt
    ```

    使用">>"重定向操作符,尾部继续添加输出文件.
    ```
    $ ls -l /usr/bin > ls-output.txt
    $ ls -l ls-output.txt
    -rw-r--r-- 1 root root 71699 Jul 23 16:31 ls-output.txt
    $ ls -l /usr/bin >> ls-output.txt
    -rw-r--r-- 1 root root 143398 Jul 23 16:31 ls-output.txt
    ```

  * ## 标准错误重定向

    ```
    $ ls -l /bin/usr > ls-output.txt
    ls: cannot access /bin/usr: No such file or directory
    ```

    ls命令输出了一条错误信息,但是为什么这个错误信息显示在屏幕上而没有重定向到ls-output.txt.原因是ls程序并不会把它运行的错误信息发送到标准输出文件上.会把错误信息发送到标准错误文件中.因为我们没有重定向标准错误所以这个信息还是打印在屏幕上.

    ```
    $ ls -l /bin/usr 2> ls-error.txt
    ```

    shell使用文件描述符(file descriptor)分别索引标准输入,输出和错误.分别编号为0,1,2. 编号2代表就是标准错误输出.

  * ## 标准输出和标准错误同时重定向
    ```
    $ ls -l /bin/usr &> ls-output.txt
    ```
    使用"&>"符号就可以将标准输出错误输出同时重定向

  * ## 处理不要的输出

    ```
    $ ls -l /bin/usr 2> /dev/null
    ```
    可以把输出重定向到一个称为/dev/null的特殊文件来实现,这个文件称为位桶(bit bucket)的系统设备.


  * ## 标准输入重定向

    cat - con**cat**enate files and print on the standard output

    ```
    $ cat ls-output.txt
    ```
    将显示ls-output.txt的文件内容.cat经常用来显示短的文本文件.

    ```
    $ cat movie.mpeg.* > movie.mpeg
    ```
    cat 也可以接受多个文件参数作为输入参数,所以也可以用来把文件拼接在一起.

    ```
    $ cat
    hello world #输入回车
    hello world
    ```
    如果cat命令没有给定任何参数,他将从标准输入读取内容,由于标准输入在默认情况下是连接到键盘,所以实际上它正在等待键盘的输入内容.

    ```
    $ cat < ls-output.txt
    ```
    使用重定向符"<".我们将标准输入的源从键盘变为ls-output.txt.由于cat输出又是标准输出.所以会打印ls-output.txt内容.

  * ## 管道

    ```
    command1 | command2 
    ```
    使用管道操作符"|"可以把一个命令的输出传送到另一个命令的标准输入中.


    * ### less/more

      more为早期UNIX中的程序,less比more多了向前翻页的功能. 两个程序都是支持vi的命令操作.

      ```
      $ ls -l /usr/bin | less

      $ less ls-output.txt
      ```
      less 命令可以分页显示任意命令输入. 

    导航操作:
      * 下翻页 SPACE or f(forward)
      * 上翻页 b(backword)
      * 下一行 ENTER or j
      * 上一行 k
      * 下半页 d
      * 上半页 u

    * ### head/tail

      查看文件的前多少行,查看文件的后多少行.

      常用参数
        * -n 查看到n行的内容
        * -f 只存在tail 当文件有新增时,自动打印内容.

      ```
      $ head -10 filename

      $ ls -l /usr/bin | head - 10
      ```

      ```
      $ tail -f  /var/log/message
      ```
      tail -f选项在观察正在被写入的日志的状态时很有用


    * ### 排序文件内文本行

      sort - sort lines of text files

      ```
      $ ls /bin /usr/bin | sort | less
      ```

    * ### 报告或忽略文件中重复的行

      uniq - report or omit repeated lines(unique) 

      常用参数:
        * -d 打印重复行,并且进行分组,只打印重复行的组名.
        * -D 打印重复行.
        * -u 打印唯一行

      ```
      $ ls /bin /usr/bin | sort | uniq | less

      $ ls /bin /usr/bin | sort | uniq -d | less
      ```

    * ### 打印行数,字数和字节数
 
      wc - print newline, **w**ord, and byte **c**ounts for each file

      常用参数:
        * -c --types
        * -m --chars
        * -l --lines
        * -w --words

      ```
      $ ls /bin /usr/bin | sort | uniq | wc -l
      1167
      ```
    * ### 打印匹配

       grep, egrep, fgrep - print lines that match patterns
       (**G**lobally search a **R**egular **E**xpression and **P**rint)

       ```
       grep pattern [file...]
       ```

       ```
       $ ls /bin /usr/bin | sort | uniq | grep zip
       ```

    * ### 从stdin读取数据,并同时输出到stdout和文件中

      tee - read from standard input and write to standard output and files

      ```
      ls /usr/bin | tee ls-output.txt | grep zip
      ```

      tee就好像在管道上安装了"T", 当在某个中间处理阶段来捕获一个管道内容时,会很有用.



# 权限

  * ## 所有者,组成员和其他所有用户

    在UNIX安全模型中,一个用户可以拥有(own)文件和目录.当一个用户拥有一个文件或者目录时,它将对该文件或目录的访问权限拥有控制权.反过来,用户又归属于一个群组(group),该群组由一个或者多个用户组成,组中用户对文件和目录的访问权限由其所有者授予.除了可以授予群组访问权限之外,文件所有者也可以授予所有用户一些访问权限,在UNIX术语中,所有用户是指整个世界(world).

    id - print real and effective user and group IDs

    ```
    $ id
    uid=1001(gexiang) gid=1001(happytimes) groups=1001(happytimes),1004(agvs)
    ```

    在创建用户账户的时候,用户将被分配一个称为用户ID(userID)或者uid的号码。为了符合人们的使用习惯,用户ID与用户名一一映射.同时用户将被分配一个有效组ID(primarygroupID)或者称为gid，而且该用户也可以归属于其他的群组.系统分配普通账户从1000开始编号.

    信息存在哪里?
      * /etc/passwd 用户账户定义文件
      * /etc/group 用组定义文件
      * /etc/shadow 保存用户的密码

  * ## 读写和可执行

    ```
    $ > foo.txt
    $ ls -l foo.txt
    -rw-r--r-- 1 gexiang happytimes 0 Jul 23 20:47 foo.txt
    ```

    文件类型|所有者权限|组权限|其他用户权限
    -|-|-|-
    \-|rw-|r--|r--

    文件类型:
      * \- 普通文件
      * d 目录文件
      * l 符号链接,剩下的属性一定为rwxrwxrwx,他是伪属性.
      * c 字符设备文件.标准输出,标准输出.
      * b 块设备.以数据块方式处理数据的设备.

    权限属性:

    | 属性 | 文件 | 目录 |
    |---|------------------|---------------------------------------------------------------|
    | r | 允许打开和读取文件 | 可以读取目录结构,可以查看查看目录,文件名,不能查看权限所在组等信息. |
    | w | 允许写入文件 | 可以新建,移动,重命名一个文件. |
    | x | 允许文件当作程序执行 | 允许进入目录.可以查看`ls -l`内的信息. |


    目录R权限:
    ```
    root$ ll
    drwxr-x--- 4 root    root       4096 Jul 23 21:26 auth

    gexiang$ ll auth
    ls: cannot open directory auth: Permission denied

    root$ chmod o+r auth/
    gexiang$ ll auth
    -????????? ? ? ? ?            ? a
    d????????? ? ? ? ?            ? sub
    ```

    目录X权限:
    ```
    root$ ll
    drwxr-xr-- 4 root    root       4096 Jul 23 21:26 auth

    gexiang$ cd auth/
    bash: cd: auth/: Permission denied

    root$ chomd o+x auth/
    gexiang$ ll auth
    -rw-r--r-- 1 gexiang happytimes    0 Jul 23 21:25 a
    drwxr-xr-x 2 root    root       4096 Jul 23 21:22 sub
    ```

    目录X权限:
    ```
    gexiang$ cd auth/
    gexiang$ touch file
    touch: cannot touch ‘file’: Permission denied

    root$ chmod o+w auth/
    gexiang$ touch file; ll;
    -rw-r--r-- 1 gexiang happytimes    0 Jul 23 21:25 a
    -rw-r--r-- 1 gexiang happytimes    0 Jul 23 21:37 file
    drwxr-xr-x 2 root    root       4096 Jul 23 21:22 sub

    ```

  * ## 更改文件权限
  
    chmod - **ch**ange file **mod**e bits

    chmod支持两种不同方式改变文件方式,八进制表示法和符号表示法.

    常用参数:
      * -R 递归改变文件和目录

    * ### 八进制表示法
      * x 001 1
      * w 010 2
      * r 100 4
      * rwx 111 7
      * rw- 110 6
      * r-x 101 5
      * r-- 100 4
      * --- 000 0

      ```
      $ > file; ls -l file
      -rw-r--r-- 1 root root 0 Jul 23 22:04 file

      $ chmod 600 file; ls -l file
      -rw------- 1 root root 0 Jul 23 22:04 file
      ```

    * ### 符号表示法

      该符号表示法分为三部分:更改会影响谁,要执行哪个操作以及要设置哪种权限.

      * u 表示"user"表示文件或目录的所有者
      * g 表示"group"文件所属组
      * o 表示"thers"表示其他用户
      * a 表示"all".u,g,o全部.
      * \+ 给ugoa添加权限
      * \- 给ugoa删除权限
      * = 指定权限可用,其余删掉.
      * r 读权限
      * w 写权限
      * x 执行权限
      * s 在文件执行时把进程属主或者属组设为文件的属性.

      ```
      $ > file ; ls -l file;
      -rw-r--r-- 1 root root 0 Jul 24 09:15 file

      $ chmod u+x file; ls -l file;
      -rwxr--r-- 1 root root 0 Jul 24 09:15 file

      $ chmod ugo=rw file; ls -l file;
      -rw-rw-rw- 1 root root 0 Jul 24 09:15 file
      ```

  * ## 设置默认权限

    umask — get or set the file mode creation mask

    umask命令控制着创建文件时给文件的默认权限.它使用八进制表示法从文件模式属性中删除一个位掩码.

    ```
    $ umask; rm -f file; > file; ls -l file;
    0022
    -rw-r--r-- 1 root root 0 Jul 24 09:32 file

    umask 000; rm -f file; > file; ls -l file;
    -rw-rw-rw- 1 root root 0 Jul 24 09:32 file
    ```

    原始文件的权限是`rw-`.再把掩码八进制展开成二进制形式.拿原始文件的权限减去掩码的二进制,就是我们创建文件的实际权限了.

    | 原始模式 | --- | rw- | rw- | rw- |
    |---------|------|-----|----|------|
    | 掩码 | 000 | 000 | 010 | 010 |
    | 结果 | --- | rw- | r-- | r-- |
  
  * ## 一些特殊权限

    虽然通常看到八进制权限掩码都是3位数字,但是实际用四位数字表示.其中有一些权限较少的使用.

      * setuid 字符表示s,数字表示4,叠加位置user的x位.
      * setgid 字符表示s,数字表示2,叠加位置group的x位.
      * sticky bit 字符表示t,数字表示1,叠加位置other的x位

    ```
    $ ls -l /usr/bin/passwd
    -rwsr-xr-x. 1 root root 27832 Jun 10  2014 /usr/bin/passwd

     ls -ld /tmp/
    drwxrwxrwt. 8 root root 4096 Jul 24 09:14 /tmp/
    ```

    * ### setuid 权限

      八进制表示为4000.当把它应用到一个可执行文件时,有效用户ID将从实际用户ID(实际运行该程序的用户)设置成该程序所有者的ID.仅对可执行程序有意义.

      ```
      $ which mkdir
      /usr/bin/mkdir

      $ cp /usr/bin/mkdir /usr/bin/mydir
      $ chmod u+s /usr/bin/mydir

      $ ls -l /usr/bin/mydir
      -rwsr-xr-x 1 root root 79864 Jul 24 10:30 /usr/bin/mydir

      $ su - gexiang
      $ mkdir dir1; mydir dir2;

      $ ls -dl dir*
      drwxr-xr-x 2 gexiang happytimes 4096 Jul 24 10:31 dir1
      drwxr-xr-x 2 root    happytimes 4096 Jul 24 10:31 dir2
      ```

      当普通用户运行一个具有“setuidroot”(已设置setuid位,由root用户所有)属性的程序时,该程序将以超级用户的权限来执行

    * ### setgid 权限

      八进制表示为2000.类似于setuid位,它会把有效组ID从该用户的实际组ID更改为该文件所有者的组ID.可以设置在可以执行程序或者目录中.
      在一个具有sgit权限的目录下,新建的文档会自动继承目录的属组身份.

      ```
      $ mkdir public/; ls -ld public/
      drwxr-xr-x 2 root root 4096 Jul 24 10:47 public

      $ > public/file1

      $ chmod g+s public 
      $ chown :happytimes public/
      $ ls -ld public
      drwxr-sr-x 2 root happytimes 4096 Jul 24 10:48 public

      $ > public/file2
      $ mkdir public/dir1

      $ ll public/
      total 4
      drwxr-sr-x 2 root happytimes 4096 Jul 24 10:50 dir1
      -rw-r--r-- 1 root root          0 Jul 24 10:48 file1
      -rw-r--r-- 1 root happytimes    0 Jul 24 10:49 file2
      ```

      如果对一个目录设置setgid位,那么在该目录下新创建的文件将由该目录所在组所有,而不是由文件创建者所在组所有.当一个公共组下的成员需要访问共享目录下的所有文件时,设置setgid位将很有用,并不需要关注文件所有者所在的有效组.

    * ### sticky

      八进制表示为1000.它是从传统UNIX中继承下来的,可以标记一个可执行文件为"不可交换的".在Linux中,会忽略文件的sticky位,但是如果对一个目录设置sticky位,那么将能阻止用户删除或者重命名文件,除非用户是这个目录的所有者,文件所有者或者是超级用户.它常用来控制对共享目录.比如:/tmp的访问.

      ```
      $ chomd +t dir
      ```


  * ## 改变身份

    可以有三种方式改变用户的身份:
      * 注销重新登陆
      * 使用su命令
      * 使用sudo命令


    * ### su 以其他用户和组ID来运行shell
  
      su - run a command with substitute user and group ID

      常用参数:
        * \- -l --login 将shell按照login方式重新加载

      ```
      $ su - gexiang
      Last login: Wed Jul 24 11:26:01 CST 2019 on pts/2
      [gexiang@iZ28fpe62ijZ ~]$
      ```

    * ### sudo 以另一个用户身份执行命令

      管理者可以通过配置sudo命令/etc/sudoer配置文件,使系统以一种可控的方式,允许普通用户以一个不同的用户身份执行(通常是超级用户)命令. 
      sudo命令并不需要输入超级用户的密码,只需要输入自己的密码进行认证.sudo命令并不需要启动一个新的shell环境.

      在推出Ubuntu的时候,Ubuntu的创造者采取了一个不同的策略.默认情况下,Ubuntu不允许用户以root账户的身份登录(因为不能成功为root账户设置密码),取而代之的是使用sudo命令来授予超级用户的特权.最初的用户账户可以通过sudo命令来获得超级用户的全部权限,后面的用户账户也可以被授予相似的权限.

    * ### chown/chgrp 更改文件所有者和所属群组

      chown - **ch**ange file **own**er and group

      ```
      chown [owner][:[group]] file...
      chown :group file ... same as chgrp
      ```

      常用参数:
        -R --recursive 递归操作文件和目录


      ```
      $ > file; ll file
      -rw-rw-rw- 1 root root 0 Jul 24 14:02 file

      $ chown gexiang:happytimes file;ll file
      -rw-rw-rw- 1 gexiang happytimes 0 Jul 24 14:02 file
      ```

    * 共享目录的使用
  
      假设timge和sun都要很多MP3音乐.并想创建一个共享目录存放他们的音乐文件.

      ```
      $ mkdir /usr/local/share/Music
      $ ls -ld /usr/local/share/Music
      drwxr-xr-x 2 root root 4096 Jul 24 14:18 /usr/local/share/Music

      $ chown :happytimes /usr/local/share/Music; 
      $ ls -ld /usr/local/share/Music
      drwxr-xr-x 2 root happytimes 4096 Jul 24 14:18 /usr/local/share/Music

      $ chmod 775 /usr/local/share/Music; 
      $ ls -ld /usr/local/share/Music
      drwxrwxr-x 2 root happytimes 4096 Jul 24 14:18 /usr/local/share/Music

      $ chmod g+s /usr/local/share/Music;
      $ ls -ld /usr/local/share/Music
      drwxrwsr-x 2 root happytimes 4096 Jul 24 14:18 /usr/local/share/Music

      $ su - gexiang 
      gexinag# umask 0002
      gexiang# mkdir /usr/local/share/Music/Jay
      gexiang# ls -ld /usr/local/share/Music/Jay
      drwxrwsr-x 2 gexiang happytimes 4096 Jul 24 14:26 /usr/local/share/Music/Jay
      ```




