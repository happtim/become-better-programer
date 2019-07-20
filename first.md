* # 导航

  * ## 当前工作目录

    `pwd` - **p**rint name of current/**w**orking **d**irectory

    ```
    $ pwd 
    $ /home/gexiang
    ```

  * ## 更改当前路径

    `cd` - **c**hange current **d**irectory to dir 

      * ### 绝对路径

        绝对路径从根目录开始,后面接一个又一个文件目录,直到到达指定的目录或者文件.

      * ### 相对路径
        绝对路径是从根目录开始,通向目标目录,而相对路径是从工作目录开始,通向目标目录.

    特殊符号 `.` 代表当前目录
  `..` 代表上层目录


      ```
      $ cd /usr/bin/
      $ pwd
      /usr/bin
      $ cd ..
      $ pwd
      /usr
      ```


    * ### 常用快捷切换目录

      * cd/cd~ 将工作目录改变成主目录
      * cd- 将工作目录改编成先前工作目录


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

## 符号链接

  ### 软链接

这种特殊的文件叫做符号链接,一个文件很可能采用多个名字来引用.

```
lrwxrwxrwx   1 root root       19 Jun 24  2018 libstdc++.so.6 -> libstdc++.so.6.0.19
-rwxr-xr-x   1 root root   991616 May 16  2018 libstdc++.so.6.0.19
```

上面闲了一个指向libstdc++.so.6.0.19 共享文件的符号链接libstdc++.so.6.其他文件使用libstdc++.so.6的程序的时候访问的是libstdc++.so.6.0.19.如果安装了新的版本如libstdc++.so.6.0.20只需要将原来链接删除重新链接so.6.0.20版本的库文件.所有程序依赖这个库so.6就重新指向了so.6.0.20版本了.假如新版本出现bug,可以重新链接回原有版本.



  * ##  系统层次标准

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
## file命令确定文件类型

  linux 系统中的文件名不反应文件的内容和类型. 使用file命令来确定文件的类型.

  file *filename*

* # 阅读文本内容

  * ## more/less

    more为早期UNIX中的程序,less比more多了向前翻页的功能. 两个程序都是支持vi的命令操作.

  * ## head/tail
    查看文件的前多少行,查看文件的后多少行.

    head/tail -10 *filename* 

    参数
      * -n 查看到n行的内容


* # 操作文件与目录

  * ## 创建目录

    `mkdir` - **m**a**k**e **dir**ectories

    ```
    mkdir dir1 dir2 dir3
    ```

  * ## 复制文件和目录

    `cp` - **c**o**p**y files and directories

    ```
    cp item1 item2
    ```

  * ## 移动和重命名文件

    `mv` - **m**o**v**e (rename) files

    ```
    mv item1 item2
    ```

  * ## 删除文件和目录

    `rm` - **r**e**m**ove files or directories

    ```
    rm item1 item2
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
      ls -l
      -rw-r--r-- 1 root root      64 Mar 15 10:36 add.py

      ln add.py add_link_file.py
      ls -l
      -rw-r--r-- 2 root root      64 Mar 15 10:36 add_link_file.py
      -rw-r--r-- 2 root root      64 Mar 15 10:36 add.py
      ```

    * ### 符号链接(软链接)

      ```
      ln -s item link
      ```

      符号链接是为了克服硬链接的局限性而创建的.符号链接通过创建一个特殊类型文件,该文件包含了指向指向引用文件或目录的文本指针.非常类似与Windows系统中的快捷方式.

      符号链接指向的文件与符号链接自身文件几乎没有区别.将一些东西写入符号链接里,那么这些东西也会同样写入引用的文件内.删除一个符号链接时,只是删除符号链接,并没有删除文件本身.