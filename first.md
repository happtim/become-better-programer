
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
# 进程

  内核会保存每个进程的信息以便确保任务有序进行.比如,每个进程将被分配一个称为进程ID(PID，processID)的号码.进程ID是按递增的顺序来分配的,init进程的PID始终为1.内核也记录分配给每个进程的内存信息以及用来恢复运行的进程就绪信息.和文件系统类似,进程系统中也存在所有者,用户ID,有效用户ID等。

  * ## 查看进程信息

    * ### ps 查看进程信息

      ps - report a snapshot of the current processes.

      常用参数:
        * a (前面没有连字符)显示所有终端的进程
        * u (前面没有连字符)显示更多信息 
        * x (前面没有连字符)告知ps命令显示所有的进程,而不关心它属于那个终端 

        * -e 显示系统所有进程
        * -l 使用长格式输出
        * -f 使用完成格式输出信息

        ```
        $ ps aux
        $ ps -elf
        ```
    
      进程状态STAT列:
        * R 运行状态.正在运行或准备运行
        * S 睡眠状态.进程不在运行,而是等待某件事情发送,如键盘输入或者网络报文.
        * D 不可中断睡眠睡眠.进程在等待I/O操作.
        * T 暂停状态.进程被指示暂停.
        * X 无效或者"僵尸"进程.子进程被终止 ,但是还没有被其父进程彻底释放掉.
        * < 高优先级进程.进程可以被赋予等多的重要性,分配更多的CPU时间.
        * N 低有优先级进程.只有在其他更高优先级的进程使用完成处理器才能使用CPU时间.
        * 

    * ### pstree 查看进程树

        pstree - display a tree of processes

        ```
        pstree [options] [pid,user]
        ```

        常用参数:
          * -a 显示命令行参数
          * -u 显示用户名
          * -p 显示PIDs.

        ```
        $ pstree -aup

        $ pstree 1 #查看指定PID的进程树

        $ pstree -p root #查看指定用户进程树
        ```

    * ### top 进程动态排名

      top - display Linux processes

      top程序将按照进程活动的顺序,以列表的形式持续更新显示系统的当前信息.它主要查看系统最高进程的运行情况.显示包含两部分,顶部分显示的是系统总体状态信息,下部是进程显示信息.

      主要交互参数:
        * M 内存排序
        * N PID排序
        * P CPU使用率排序
        * T 运行时间排序

    * ### pgrep 进程检索信息

      pgrep,  pkill  -  look up or signal processes based on name and other attributes

      ```
      pgrep [options] ... pattern
      ```

      常用参数:
        * -u 指定用户的进程
        * -l 输出进程名
        * -t 检索指定终端

      ```
      $ pgrep -l -u root log
      481 systemd-logind
      28646 rsyslogd
      ```

  * ## 进程控制

    * ### 中断进程

      ^C same as Ctrl-C

      /dev/zero 类似 /dev/null 是一个虚拟设备,用来无限提供(0x00,ASCII的NULL).

      ```
      $ dd if=/dev/zero of=/dev/null
      ^C409577+0 records in
      409577+0 records out
      209703424 bytes (210 MB) copied, 1.32879 s, 158 MB/s
      ```

      当执行命令时,shell提示符没有任何返回,这是因为shell正在等待命令结束. 我们按下Ctrl-C会中断程序,然后shell提示符返回.

    * ### & 后台执行

      我们想shell提示符返回,但又不终止程序,可以使用让程序在后台的方式实现.可以把终端想象成一个有前台和后台环境. 在命令后面加上`&`来实现后台运行.

      ```
      $ dd if=/dev/zero of=/dev/null &
      [1] 25343
      ```

      打印的这行内容称为作业控制(job control)的特性表现.显示作业编号为1.PID为25343.

    * ### jobs 查询后台作业

      jobs — display status of jobs in the current session

      ```
      $ jobs
      [1]+  Running                 dd if=/dev/zero of=/dev/null &
      ```

    * ### fg 使进程回到前台
  
      fg — run jobs in the foreground

      ```
      fg [job_id]
      ```

      ```
      $ fg 1
      dd if=/dev/zero of=/dev/null
      ```

    * ### Ctrl-Z 暂停进程

      ```
      ^Z
      [1]+  Stopped                 dd if=/dev/zero of=/dev/null
      ```

    * ### bg 使进程回到后台

      bg — run jobs in the background

      ```
      bg [job_id ...]
      ```

      ```
      $ dd if=/dev/zero of=/dev/null &
      [1] 25658

      $ fg
      dd if=/dev/zero of=/dev/null
      ^Z
      [1]+  Stopped                 dd if=/dev/zero of=/dev/null

      $ bg 1
      [1]+ dd if=/dev/zero of=/dev/null &

       jobs
      [1]+  Running                 dd if=/dev/zero of=/dev/null &
      ```

  * ## 信号

    * ### kill 命令

      kill - terminate a process

      ```
      kill [-signal | -s signal] PID|name ...
      ```

      参数:
        * -l 列出所有信号
        * -s 发送指定信号可以是名字或者编号

      kill命令通常用来杀死进程,用它可以终止运行不正常德程序或者拒绝终止的程序.更准确的说他给进程发送信号.信号是操作系统和程序见通信的一种方式.
      Ctrl-C 中断(INT,Interrupt)和Ctrl-Z 中断暂停(TSTP,Terminal Stop)就是发送的信号.

      ```
      $ dd if=/dev/zero of=/dev/null &
      [1] 25691

      $ kill  25691
      $ kill -9 25691 # 9为kill信号
      ```

    * ### killall 发送信号给多个进程

      killall - kill processes by name

      ```
      $ dd if=/dev/zero of=/dev/null &
      [1] 25691

      $ dd if=/dev/zero of=/dev/null &
      [2] 25711

      $ jobs
      [1]-  Running                 dd if=/dev/zero of=/dev/null &
      [2]+  Running                 dd if=/dev/zero of=/dev/null &

      $ killall dd
      
      $ jobs 
      [2]+  Terminated              dd if=/dev/zero of=/dev/null
      ```
    
    * ### pkill 杀死指定的进程
  
      same as pgrep

# 配置与环境

    环境中存储了两种类型,分别是环境变量(environment variable) 和 shell变量(shell variable). shell变量是由bash存放少量数据,环境变量就是除此之外其他变量.


  * ## 检查环境

    printenv - **print** all or part of **env**ironment

    ```
    printenv [OPTION] ... [VARIABLE] ...
    ```

    ```
    $ printenv | less

    ```

    set命令如果不带选项或者参数,那么只会显示shell变量,环境变量以及已定义的shell函数.
    ```
    $ type set
    set is a shell builtin

    $ set | less
    ```

    打印单条变量内容
    ```
    $ printenv  USER
    root

    $ echo $HOME
    /root
    ```

  常见环境变量:
    * SHELL 当前用户shell名称
    * HOME 当前用户主目录的路径
    * PATH 以冒号分割的一个目录列表,当用户输入一个可执行程序的名称时,会查找该目录列表.
    * PWD 当前工作目录
    * OLDPWD 之前工作目录
    * PS1 提示字符串1.


  * ## 环境是如何建立

    用户登陆系统之后,bash程序就会启动并读取一配置脚本,这些脚本定义了所有用户共享的默认环境.bash会继续读取在用户主目录下用于定义个人环境的配置文件.

    启动配置脚本:
      * /etc/profile 此文件为系统的每个用户设置环境信息,当用户第一次登录时,该文件被执行. 并从/etc/profile.d目录的配置文件中搜集shell的设置.
      * /etc/bashrc 为每一个运行bash shell的用户执行此文件.当bash shell被打开时,该文件被读取
      * ~/.bash_profile 每个用户都可使用该文件输入专用于自己使用的shell信息,当用户登录时,该文件仅仅执行一次.默认情况下,他设置一些环境变量,执行用户的.bashrc文件.
      * ~/.bashrc 该文件包含专用于你的bash shell的bash信息,当登录时以及每次打开新的shell时,该该文件被读取.
      * ~/.bash_logout 当每次退出系统退出bash shell时,执行该文件. 

# 网络

  * ## 检查,监控网络
  
    * ### ping 检测与目标主机是否联通

      ping - send ICMP ECHO_REQUEST to network hosts

      ```
      $ ping bing.com
      PING bing.com (13.107.21.200) 56(84) bytes of data.
      64 bytes from 13.107.21.200 (13.107.21.200): icmp_seq=1 ttl=115 time=41.9 ms
      64 bytes from 13.107.21.200 (13.107.21.200): icmp_seq=2 ttl=115 time=41.9 ms
      64 bytes from 13.107.21.200 (13.107.21.200): icmp_seq=3 ttl=115 time=42.9 ms
      64 bytes from 13.107.21.200 (13.107.21.200): icmp_seq=4 ttl=115 time=41.9 ms
      ^C
      ```

    * ### traceroute 跟踪网络数据包的传输路径

      traceroute hostname

      显示从本地系统到目标主机经过的路由列表

    * ### netstat 检查网络设置及相关统计

      netstat - Print network connections, routing tables, interface sta‐tistics, masquerade connections, and multicast memberships

      统计类型:
        * 无参数 显示socket监听信息
        * -r 显示内核路由表
        * -i 显示网络接口表
        * -s 显示统计信息

       ```
       $ netstat -ie
       ```

      常用socket参数:
        * -a 显示列出所有的连接,服务监听.
        * -t 列出tcp协议服务
        * -u 列出udp西医服务
        * -n 显示端口号
        * -l 列出当前监听服务(默认)
        * -p 列出服务的PID
      
      ```
      $ nestat -atunp
      
      Active Internet connections (servers and established)
      Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
      tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      1/systemd
      tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      18092/httpd
      tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      22008/sshd
      tcp        0      0 139.129.117.115:3000    0.0.0.0:*               LISTEN      28636/ruby
      tcp        0    464 139.129.117.115:22      121.236.226.32:51868    ESTABLISHED 26991/sshd: root@pt
      tcp        0      0 10.30.106.90:42552      10.146.184.215:3306     ESTABLISHED 28636/ruby
      ```

  * ## 通过网络传输文件

    * ### ftp 传输文件

      ftp是由File Transfer Protocol协议缩写而来,ftp程序比web浏览器出现的还早,大多数浏览器都支持ftp协议.ftp的传输并不安全,它以明文的方式传送账号和密码.大部分使用ftp传输文件都使用匿名方式,允许没有登陆名和密码.

      常用交互命令
        * ls/dir 列出目
        * cd 切换目录
        * get/mget 下载文件/多个
        * put/send 上传文件
        * open 在进入ftp模式登陆ftp服务
        * close 断开这次连接,还在ftp模式
        * bye/quit 离开
        * help 帮助

      以匿名方式登陆上海交大ftp

      ```
      $ ftp ftp.sjtu.edu.cn
      Trying 202.38.97.230...
      Connected to ftp.sjtu.edu.cn (202.38.97.230).
      220 (vsFTPd 3.0.2)
      Name (ftp.sjtu.edu.cn:root): anonymous  #匿名登陆
      331 Please specify the password.
      Password: #无密码
      230 Login successful.
      Remote system type is UNIX.
      Using binary mode to transfer files.
      ftp>

      ftp> get sjtu.edu.cn.html /home/gexiang/sjtu.edu.cn.html
      local: /home/gexiang/sjtu.edu.cn.html remote: sjtu.edu.cn.html
      227 Entering Passive Mode (202,38,97,230,243,35).
      150 Opening BINARY mode data connection for sjtu.edu.cn.html (333 bytes).

      put dsh.log
      local: dsh.log remote: dsh.log
      227 Entering Passive Mode (202,38,97,230,126,222).
      550 Permission denied.
      ```
  
    * ### wget 非交互式网络下载工具

    The non-interactive network downloader.

    ```
     wget [option]... [URL]...
    ```

    常用参数:
      * -O 下载到本地文件名

    ```
    $ wget baidu.com 
    ```

  * ## 与主机建立安全通信
  
    多年以前,类UNIX操作系统就可以通过网络进行远程操控.早期,在互联网还未普及的时候,登录远程主机有两个很受欢迎的命令rlogin和telnet命令.但是它们与ftp命令有着相同的致命缺点,即所有通信信息(包括用户名和密码)都是以明文的方式传输的,所以它们并不适用于互联网时代.

    * ### ssh 安全登陆远程计算机

      为了解决明文传输问题,ssh(Secure Shell)的新协议应运而生.ssh登陆过程.

      1. 用户向远程主机发登录请求：ssh user@远程主机

      2. 远程主机收到用户的登录请求,把自己的公钥发给用户.

      3. 用户使用这个公钥,将登录密码加密后,发送回远程主机.

      4. 远程主机用自己的私钥,解密登录密码,如果密码正确,就同意用户登录.


      如果你是第一次登录对方主机，系统会出现下面的提示：
      ```
      $ ssh user@host 
      The authenticity of host 'host (12.18.429.21)' can't be established. 
      RSA key fingerprint is 98:2e:d7:e0:de:9f:ac:67:28:c2:42:2d:37:16:58:4d. 
      Are you sure you want to continue connecting (yes/no)?
      ```
      这段话的意思是,无法确认host主机的真实性,只知道它的公钥指纹,问你还想继续连接吗? 
      所谓"公钥指纹",是指公钥长度较长(这里采用RSA算法，长达1024位),很难比对,所以对其进行MD5计算,将它变成一个128位的指纹.上例中是98:2e:d7:e0:de:9f:ac:67:28:c2:42:2d:37:16:58:4d，再进行比较，就容易多了. 很自然的一个问题就是,用户怎么知道远程主机的公钥指纹应该是多少?回答是没有好办法,远程主机必须在自己的网站上贴出公钥指纹,以便用户自行核对.
      
      当远程主机的公钥被接受以后,它就会被保存在文件$HOME/.ssh/known_hosts之中.下次再连接这台主机,系统就会认出它的公钥已经保存在本地了,从而跳过警告部分,直接提示输入密码.


    * ### 公钥登陆

      使用密码登录,每次都必须输入密码,非常麻烦.ssh提供免密码登陆方式. 
      用户将自己的公钥储存在远程主机上.登录的时候,远程主机会向用户发送一段随机字符串,用户用自己的私钥加密后,再发回来.远程主机用事先储存的公钥进行解密,如果成功就证明用户是可信的,直接允许登录shell,不再要求输入密码.

    * ### scp 安全传输文件 
     
      scp — secure copy (remote file copy program)

      ```
      scp source ... target
      source target: [user@]host:[path] or [user@]host[:port][path]
      ```

      ```
      root$ ll /home/gexiang
      -rw------- 1 gexiang happytimes    0 Jul 23 22:07 file

      root$ scp gexiang@localhost:file ./scp-file
      gexiang@localhost's password: #输入密码不会显示
      file                                          100%    0     0.0KB/s   00:00

      root$ scp scp-file gexiang@localhost:scp-scp-file
      gexiang@localhost's password:
      scp-file                                      100%    0     0.0KB/s   00:00

      root$ ll /home/gexiang/scp*
      -rw------- 1 gexiang happytimes 0 Jul 25 11:57 /home/gexiang/scp-scp-file
      ```

    * ### sftp 安全的文件传输协议
  
      sftp — secure file transfer program

      它是ftp程序的安全版本.Sftp与我们先前使用的ftp程序功能极为相似,只是sftp是用SSH加密隧道传输信息而不是以明文方式传输.Sftp相比传统的ftp而言,还有一个重要的优点,就是它并不需要远程主机上运行FTP服务器,仅仅需要SSH服务器.






