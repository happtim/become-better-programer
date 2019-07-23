
[文件目录导航](#文件目录导航)
  - [pwd - 当前工作目录](#当前工作目录)
  - [cd - 更改当前路径](#更改当前路径)
  - [ls - 列出目录](#列出目录)
  - [FHS - 文件层次标准](#文件层次标准)
  - [file - 文件类型](#文件类型)

[阅读文本内容](#阅读文本内容)
  - [more/less](#more/less)
  - [head/tail](#head/tail)

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
    * -a 列出所有文件,包括以点开头的文件(隐藏文件)
    * -h --human-readable 以详细格式列出时,以人们可读方式现实文件大小
    * -l 使用详细格式现实结果
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

# 阅读文本内容

* ## more/less

  more为早期UNIX中的程序,less比more多了向前翻页的功能. 两个程序都是支持vi的命令操作.

* ## head/tail
  查看文件的前多少行,查看文件的后多少行.

  head/tail -10 *filename* 

  参数
    * -n 查看到n行的内容


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


* ## 通配符
  由于shell需要经常使用文件名,因此他提供了一些特殊字符来帮助你快速指定一组文件名.这些特殊字符称为通配符.

    * \* 匹配任意多个字符 (匹配0+个)
    * ? 匹配任意单个字符 (只匹配1个)
    * [characters] 匹配任意一个属于字符集中的字符

  * ### 通配符示例
    * \* 所有文件
    * g* 以g开头的任意文件
    * Data??? 以Data开头,后面跟3个字符的任意文件
    * [abc]* 以abc中任意开头的任意文件
    * backup.[0-9][0-9][0-9] 1以backup.开头,后面紧跟3个数字的任意文件.


* ## 命令的使用

  * ### 命令是什么

  * **可执行程序** 可执行程序就像在/usr/bin目录里看到的所有文件一样.在该程序类别中,程序可以编译为二进制文件,比如C,C++语言编写的程序,也可以是shell,Perl,Python,Ruby等脚本语言编写的程序.
  * **shell内置命令** bash支持许多在内部称之为shell builtin的内置命令.如:cd.kill.set.pwd
  * **shell函数** shell函数是合并到环境变量中的小型shell脚本.
  * **alias** 自定义命令

  * ### 获取命令的简要描述

    whatis 程序实现匹配具体关键字的手册页的名字和一行描述

    ```
    $ whatis ls
    ls (1)               - list directory contents
    ls (1p)              - list directory contents
    ```


  * ### 识别命令

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

  * ### 获取执行程序的位置
    
    `which`命令可以确定一个可执行文件的准确位置,`which`命令只适用于可执行程序,而不适用于内置命令和命令别名.在大型服务器中往往安装软件多个版本,此时可以方便定位出执行命令的位置.

    ```
    $ which git
    /usr/bing/git

    $which reboot
    /usr/sbin/reboot
    ```
  * ### 获取命令文档
  
    help 获取shell内置命令的帮助文档
    ```
    $ help cd
    ```
    
    --help 很多命令都有的语法选择支持参数.
    ```
    $ mkdir --help
    ```

  * ### man手册

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

  * ### 使用别名创建自己的命令

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

* ## 重定向

