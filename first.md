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


