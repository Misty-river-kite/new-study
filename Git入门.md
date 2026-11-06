# Git入门



# 安装和配置

# 使用方式

## 命令行

\-\-local\(省略\)  \-\>   本地配置，只对本地仓库有效

\-\-global         \-\>   全局配置，所有仓库生效

\-\-system       \-\>   系统配置，对所有用户生效

git config \-\-global credential\.helper store    \-\>  保存用户名和密码

git config \-\-global \-\-list  \-\>   查看配置

![image\.png](图片和附件/image.png)

## 常用命令

Git ls\-files  \-\>  查看所有追踪文件

Git status   \-\>  查看工作区和暂存区的工作状态

Git status \-s \-\> 查看状态

Git branch    \-\> 查看分支（\*所处的分支就是目前所处的分支）

Git log \-\-graph \-\-oneline \-\-decorate \-\-all  \-\> 查看分支图

## 新建版本库

1. 找到合适的位置创建目录

2. 创建一个git仓库

\-\>  git int

\-\>  git clone\+仓库地址

## 工作区域和文件位置

工作区    \-\>git add   暂存区    \-\>git commit   本地仓库

#### 状态

未跟踪    \-\>git add    未修改    \-\>\(修改文件\)    已修改     \-\>git add    已暂存

\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\>git add

git rm\< \-\-\-\-\-\-\-\-\-\-  git commit\<\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-                     

git checkout\<\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-   git reset\<\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-

## 添加和提交文件

Git status   \-\>  查看仓库状态

Git add\.      \-\>  把当前目录下所有文件添加到暂存区

Git commit  \-\>  提交\(vim\)

Git log         \-\>  查看提交历史记录

## Git reset

Git reset \-\-soft   \-\>回退到某个版本，并保存工作区和暂存区的所有修改内容

Git reset \-\-hard  \-\>回退到某个版本，并丢弃工作区和暂存区的所有修改内容

Git reset \-\-mixed  \-\>回退到某个版本，并保存工作区、丢弃暂存区的所有修改内容

Git reflog   \-\>  查看操作历史记录

Git reset \-\-方式doft/hsrd/mixed\+版本号

## Git diff

Git diff  比较工作区和暂存区的差异

git diff HARD  比较工作区和版本库的差异

Git diff \-\-cached  比较暂存区和版本库的差异

Git diff 版本号1 版本号3  比较两个版本的差异

Git diff  版本号  HEAD    比较某一版本和HARD

Git diff HEAD\~ HEAD  /  git diff HEAD^ HEAD  比较这个版本和上一个版本的差异

Git diff HEAD～2  比较提交前的两个版本和这个版本的差异

命令\+文件名  只显示该文件的差异

## 删除文件

Rm\+文件名   删除工作区文件

\-\>git add \+文件名  删除暂存区的文件

Git rm \+ 文件名  删除暂存区和工作区的文件

Git commit \-m "\(提交生声明，删除了什么什么文件\)"   在版本库中删除

## \.gitignore文件

### 应该忽略的文件

1. 系统或软件自动生成的文件

2. 编译产生的中间文件和结果文件

3. 运行时生成日志文件、缓存文件、临时文件

4. 涉及身份、密码、口令、密钥等敏感信息的文件

### 文件匹配规则（？）

- 空行或以\#开头的行会被git忽略，一般空行用于可读性的分割，\#一般用作注释

- 使用标准的blob模式匹配，eg：

\*通配任意个字符

```Plain Text
*.a
//忽略所有的.a文件
```

？匹配单个字符

\[ \]表示匹配列表中的单个字符，比如:\[abc\]表示a/b/c

- 两个\*表示匹配任意的中间目录

- \[ \]可以使用短中线连接，比如

\[0\-9\]表示任意一位数字，\[a\-z\]表示任意一位小写字母

- ！表示取反

```Plain Text
!lib.a
//忽略所有.a文件，但lib.a不忽略
```

```Plain Text
/TODO
//只忽略当前目录下的TODO文件，而不忽略其他目录下的
```

```Plain Text
build/
//忽略任何目录下的build文件夹
```

```Plain Text
doc/*.txt
//忽略doc目录下所有的txt文件，但是不忽略子目录
```

```Plain Text
doc/**/*.pdf
//忽略doc目录及其子目录下所有的pdf文件
```

# 远程仓库

## ssh配置和克隆仓库

Git clone 仓库地址  \-\>  克隆远程仓库

Git push  \-\>  推送更新内容

Git pull  \-\>  拉取更新内容

## 关联本地仓库和远程仓库

Git remote add \+别名（一般是 origin） \+仓库地址  \-\>  关联本地仓库和远程仓库

Git remote \-v  \-\>  查看当前仓库对于远程仓库的别名和地址

Git pull 仓库别名 分支名称  \-\>  拉取远程仓库的指定分支并合并（仓库别名和分支可以省略，省略则默认拉取origin别名和main分支）

//远程仓库和本地仓库的修改发生冲突则无法使用pull,需要手动修改

# Vscode

Vscode \-\> 源代码界面，文件后最后一个图标表示文件的状态

- ??\(Untracked\) ：未跟踪

- M\(Modified\)     ：已修改

- A\(Added\)         ：已添加暂存

- D\(Deleted\)       ：已删除

- R\(Renamed\)    ：重命名

- U\(Updated\)      ：已更新未合并

![image\.png](图片和附件/image%201.png)

//这个相当于git commit \-m，输入框的内容即为指令后面跟的内容

# Git分支

## 基础指令

Git branch    \-\> 查看分支列表

Git branch 分支名   \-\> 新建分支

//新建但是不切换

Git checkout 分支名   \-\>  切换分支

//该命令还可以恢复文件修改状态，可能引起歧义

Git switch 分支名   \-\>  切换分支

Git merge 分支名   \-\>  把"分支名"对于的分支合并到当下所在的分支中

*合并后的分支依然会存在* 

Git branch \-d 分支名  \-\>  删除已经被合并的分支

Git branch \-D 分支名  \-\>  强制删除分支

## 解决合并冲突问题

Git diff查看冲突内容

手动修改文件冲突内容

添加暂存

提交

Git merge \-\-abort  \-\> 在提交前可以用该指令来终止合并

## 回退和rebase

Git rebase main  \-\> 将当前分支变基到main分支上

Git rebase 分支名 \-\>（在main分支上执行）把main分支的提交记录变基到指定分支的末尾

















