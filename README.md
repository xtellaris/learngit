
以learngit测试项目为例，介绍git使用，".../"代表上级目录

## 创建repository

以learngit测试项目为例，".../"代表上级目录

1. 新建learngit文件夹作为项目根目录
2. 进入learngit目录
3. `$ git init`命令创建git项目，返回`Initialized empty Git repository in .../learngit/.git`,就说明成功了

> **NOTE!** 不要修改自动生成的.git文件，那是git用来跟踪管理版本库的！

## 提交文件

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

