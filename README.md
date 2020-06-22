
以learngit测试项目为例，介绍git使用，".../"代表上级目录

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

## 版本回退

每次git提交了修改都有一个commit id，相当于版本号，它是一串十六进制代码，通常前7位就足够指示了
- `git log` 查看版本提交历史，确定id，嫌多用--pretty=oneline简化输出
- `git reset --hard commit_id`来**回退**到某一个id的版本，也可以用HEAD指针
	> HEAD指针是git特有的，永远只想最新更新的版本，`HEAD^`则是倒数第二个版本的id，`HEAD^^`就是倒数第三个，`HEAD~n`就是倒数第n+1个版本（上n个版本）
- `git reflog`能查看历史命令，获取回退前的id，回退之后后悔了，可以用它**回到未来**，同样，回到未来也用`git reset ...`


