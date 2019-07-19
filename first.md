# 导航

## 当前工作目录

  `pwd` - **p**rint name of current/**w**orking **d**irectory


    [gexiang@iZ28fpe62ijZ ~]$ pwd
    /home/gexiang

## 更改当前路径

  ### 绝对路径

  绝对路径从根目录开始,后面接一个又一个文件目录,直到到达指定的目录或者文件.

  ### 相对路径
  绝对路径是从根目录开始,通向目标目录,而相对路径是从工作目录开始,通向目标目录.

  特殊符号 `.` 代表当前目录
  `..` 代表上层目录

  `cd` - **c**hange current **d**irectory to dir 

  ```
[gexiang@iZ28fpe62ijZ ~]$ cd /usr/bin/
[gexiang@iZ28fpe62ijZ bin]$ pwd
/usr/bin
[gexiang@iZ28fpe62ijZ bin]$ cd ..
[gexiang@iZ28fpe62ijZ usr]$ pwd
/usr
```


### 常用快捷切换目录

  * cd/cd~ 将工作目录改变成主目录
  * cd- 将工作目录改编成先前工作目录


## 列出目录

ls - **l**i**s**t directory contents

### 常用参数
* -a 列出所有文件,包括以点开头的文件(隐藏文件)
* -h --human-readable 以详细格式列出时,以人们可读方式现实文件大小
* -l 使用详细格式现实结果
* -t 按照修改时间排序
* -S 按照文件大小排序

```
[me@ linuxbox ~]$ ls 
Desktop 　 Documents 　 Music 　 Pictures 　 Public 　 Templates 　 Videos
```

### 详细输出
```
[me@ linuxbox ~]$ ls -l 
total 56 
drwxrwxr-x 2 me me 4096 2012-10-26 17:20 Desktop 
drwxrwxr-x 2 me me 4096 2012-10-26 17:20 Documents 
drwxrwxr-x 2 me me 4096 2012-10-26 17:20 Music 
drwxrwxr-x 2 me me 4096 2012-10-26 17:20 Pictures 
drwxrwxr-x 2 me me 4096 2012-10-26 17:20 Public
```

输出解释:

  * drwxrwxr-x 对文件的访问权限。第一个字符表示文件的类型。在不同类型之间，开头的“-”表示该文件是一个普通文件，d表示目录。紧接着的三个字符表示文件所有者的访问权限，再接着的三个字符表示文件所属组中成员的访问权限，最后三个字符表示其他所有人的访问权限 

  * 数字2 文件硬链接数.
  * me 文件所有者的用户名.
  * me 文件所属用户组的名称.
  * 4094 文件以字节标识的大小.
  * 2012-10-26 17:20 上次修改文件的日期和时间
  * Desktop 文件名

##  系统层标准
在Linux系统中,文件系统布局与其他类UNIX系统很相似.实际上,一个已经发布的名为Linux文件系统层次标准(LinuxFilesystemHierarchyStandard)的标准,已经详细阐述了这个设计.并不是所有Linux发行版都严格符合该标准,但大部分与之很接近.

* / 根目录,一切从这里开始
* /bin 包含
## file命令确定文件类型

  linux 系统中的文件名不反应文件的内容和类型. 使用file命令来确定文件的类型.

  file *filename*




  # 阅读文本内容

  * more/less 
  * head/tail
  * cat 打印文件内容,适合少量文件


## more/less

more为早期UNIX中的程序,less比more多了向前翻页的功能. 两个程序都是支持vi的命令操作.

## head/tail
查看文件的前多少行,查看文件的后多少行.

head/tail -n 10 *filename* 

参数
  * -n 查看到n行的内容