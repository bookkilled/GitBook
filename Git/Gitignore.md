# .Gitignore 配置
## Git忽略特殊文件
在Git工作区的根目录下创建一个特殊的.gitignore文件，然后把要忽略的文件名填进去，Git就会自动忽略这些文件。  
参照网址：https://github.com/github/gitignore  
忽略文件的原则是：
	- 1.忽略操作系统自动生成的文件，比如缩略图等；
	- 2.	忽略编译生成的中间文件、可执行文件等，也就是如果一个文件是通过另一个文件自动生成的，那自动生成的文件就没必要放进版本库，比如Java编译产生的.class文件；
	- 3.	忽略你自己的带有敏感信息的配置文件，比如存放口令的配置文件。  
配置注意：  
```bash
1、配置语法：

　　以斜杠“/”开头表示目录；

　　以星号“*”通配多个字符；

　　以问号“?”通配单个字符

　　以方括号“[]”包含单个字符的匹配列表；

　　以叹号“!”表示不忽略(跟踪)匹配到的文件或目录；

   此外，git 对于 .ignore         配置文件是按行从上到下进行规则匹配的，意味着如果前面的规则匹配的范围更大，则后面的规则将不会生效；

2、示例：

　　（1）规则：fd1/*  
        说明：忽略目录 fd1 下的全部内容；        注意，不管是根目录下的 /fd1/ 目录，还是某个子目录 /child/fd1/ 目录，都会被忽略；

　　（2）规则：/fd1/*
        说明：忽略根目录下的 /fd1/             目录的全部内容；

　　（3）规则：
        /*
        !.gitignore
        !/fw/bin/
        !/fw/sf/
        说明：忽略全部内容，但是不忽略 .gitignore 文件、根目录下的 /fw/bin/ 和 /fw/sf/ 目录；
```
案例分析：
```bash
# Demo configurations:
/.git
.gitignore
*.iml
.idea/
.ipr
.iws
*~
~*
*.diff
*.patch
*.bak
.DS_Store
Thumbs.db
.project
.*proj
.svn/
*.swp
*.swo
*.pyc
*.pyo
node_modules
dist
```

 
