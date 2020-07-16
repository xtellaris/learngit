# 学习Git的使用
以learngit测试项目为例，介绍git使用，".../"代表上级目录

# 创建版本库和提交新文件

## 创建repository

以learngit测试项目为例，".../"代表上级目录

1. 新建learngit文件夹作为项目根目录
2. 进入learngit目录
3. `$ git init`命令创建git项目，返回`Initialized empty Git repository in .../learngit/.git`,就说明成功了

> **NOTE!** 不要修改自动生成的.git文件，那是git用来跟踪管理版本库的！

## 提交新文件

**git只能跟踪文本文件的修改历史，可以具体到哪一行加了什么单词，但图片啦、word文档啦（二进制文件）只能记录修改时间和改动前后的文件大小**

1. 在learngit下写个README.md，实际上项目根目录下的任意子目录都可以
2. `git add [file]`添加文件
```
git add README.md
```
3. `git commit`提交到仓库，`-m "Comment"` 参数提交说明
```
git commit -m "wrote a readme file."
```
	git会告诉我们几个文件改了，插入了几行内容
> `add`一次只能加一个文件，而`commit`一次能添加数个文件，因为它只是说明性步骤

## 提交修改、掌握repo状态

`git status` 能输出当前repo的状态，比如有没有修改需要提交？提交的修改有没有注释？
`git diff` 查看上次修改的具体内容

所以提交修改和添加文件步骤是一样的，先add 再commit，中间活用status和diff来掌握repo状态

# 版本控制

## 版本回退

每次git提交了修改都有一个commit id，相当于版本号，它是一串十六进制代码，通常前7位就足够指示了
- `git log` 查看版本提交历史，确定id，嫌多用--pretty=oneline简化输出
- `git reset --hard commit_id`来**回退**到某一个id的版本，也可以用HEAD指针
	> HEAD指针是git特有的，永远只想最新更新的版本，`HEAD^`则是倒数第二个版本的id，`HEAD^^`就是倒数第三个，`HEAD~n`就是倒数第n+1个版本（上n个版本）
- `git reflog`能查看历史命令，获取回退前的id，回退之后后悔了，可以用它**回到未来**，同样，回到未来也用`git reset ...`

## 工作区和暂存区

- 工作区（Working Directory）：git项目的根文件夹，比如learngit这个项目的`learngit/`文件夹
- 版本库（Repository）：工作区下有一个`.git`目录，比如`learngit/.git/`，是Git的版本库。版本库之下有暂存区（stage）、第一个分支`master`、指向`master`的`HEAD`指针
	- 暂存区（Stage）：`git add `之后暂时保存的地方
	- `master`分支：新建Git版本库时自动创建的第一个分支
	- `HEAD`指针：


## 管理和撤销修改

### Git添加修改的一般过程
1. **修改工作区文件**，比如修改`learngit/README.md`
2. `git add README.md` **添加修改**到暂存区（Stage）
3. `git commit ...` 提交暂存区（Stage）的修改到版本库（Repo），这时就有了新的版本号

如果 "第一次修改--> git add --> 第二次修改 --> git commit" 那么对于版本库（Repo）来说，只有第一次修改进入了版本库，因为第二次修改没有`git add`，也就没能进入暂存区，而`git commit`只能添加暂存区的内容

被这样一层一层提交的是对文件的修改，而非文件本身，所以Git管理的是修改，而不是文件。

### 使用`git diff`
可以用如下命令来比较WD、Stage和Repo三者的状态：
```git
# 比较WD和Stage
git diff [filename]

# 比较WD和Repo的HEAD commit
git diff HEAD -- filename 
```

### `git diff`与`git status`的区别

`git status`：只能比较当前WD（分支多的话叫Working tree，也就是当前分支树）和HEAD commit的区别，能找出新增的文件，但没有详细细节

`git diff`：能比较的对象很多，可以是WD和Stagev之间，WD和Repo里的任意一个commit之间，不同commit之间等等，而且能列出修改详情。直接输入`git diff`，默认比较WD和Stage的区别。但不能列出新增文件，而且不能列出新增文件


## 删除文件

# 远程管理

## 添加远程仓库

## 从远程仓库克隆

## 
