# 如何将修改移动到别的分支
有时打开项目会忘记切换到dev分支，而直接在master上修改甚至提交代码，此时需要

## 如果修改未提交缓存(not git commit)
不论有没有添加到暂存区(git add)

1. 贮存当前修改
```sh
git stash
```

2. 切换分支，然后弹出贮存的修改
```sh
git switch [branch]
git stash pop
```

## 如果已经提交(already git commit)
假设当前分支树已经如下：
```
           HEAD
             |
m1-m2-m3-m4-m5  (master)
    \  \
     d1-d2      (dev)
```
`m4`、`m5`是错误提交，它本应该提交给dev分支，并成为`d3`、`d4`提交，也就是如下图
```
      HEAD
       |
m1-m2-m3          (master)
    \  \
     d1-d2-d3-d4  (dev)
```

如何修改：

1. 切换到目标分支，之后cherry-pick
```sh
git switch [target-branch] # 切到dev分支
git chrrey-pick [commit-id] # 选出m4提交
git chrrey-pick [commit-id] # 挑选出m5提交
```
cherry-pick也可以改用fast-forward模式下的merge，区别在于修改后只剩一个commit

2. 切换回误操作分支，重置分支
```sh
git switch [target-branch] # 切回master分支
git reset --hard [commit-id] # 回到m3提交
```

